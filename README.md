# llm-output-to-note

一个本地单页 Prompt 生成器，用于把 LLM 对话内容整理成适合长期保存的 Markdown 知识笔记。

它的核心作用不是直接改写文本，而是生成一份结构化 Prompt：你可以先粘贴原始对话，再选择压缩等级和标题层级映射，最后复制生成好的 Prompt 到任意大模型中执行。

## 功能

- 将对话式回答转换为知识笔记改写任务。
- 支持实时预览最终 Prompt。
- 支持四档压缩等级：
  - `never`：完整保留信息，只做格式重构。
  - `light`：轻度整理，删除明显冗余表达。
  - `medium`：中度压缩，生成高密度知识笔记。
  - `high`：高度压缩，生成极限复习版。
- 支持标题层级映射：
  - 保持不变。
  - 整体上移 1-3 级。
  - 整体下移 1-3 级。
- 自动把 `compression_level` 插入到 Prompt 的标题层级规则下方。
- 自动把 `heading_offset` 生成为 `## 5. 标题层级偏移规则`。
- 支持一键复制 Prompt、清空内容、恢复默认配置。
- 纯前端实现，无需后端、数据库或构建流程。

## 使用方法

1. 用浏览器打开 `index.html`。
2. 在左侧输入框中粘贴原始 LLM 对话内容。
3. 在顶部选择压缩等级。
4. 按需要设置标题映射：
   - `保持不变`：原始标题层级不偏移。
   - `上移`：例如 `h3 -> h2`。
   - `下移`：例如 `h2 -> h3`。
5. 在右侧预览最终 Prompt。
6. 点击 `复制 Prompt`，粘贴到大模型中执行。

## 默认配置

当前默认状态：

- 压缩等级：`medium`
- 标题映射：`保持不变`
- 标题偏移：`heading_offset: 0`
- 内容占位符：`{{CONTENT}}`

当输入框为空时，最终 Prompt 会保留 `{{CONTENT}}` 占位符，方便先复制模板再手动替换内容。

## Prompt 结构

生成后的 Prompt 大致由以下部分组成：

```text
基础改写规则

## 4. 标题层级规则（由配置精确指定）

compression_level: ...

## 5. 标题层级偏移规则

heading_offset: ...
标题映射配置...

## 6. 列表保留策略
## 7. 引用块处理
## 8. 必须严格保留
## 9. 数学与代码区域禁止“文学化”

请处理以下内容：
{{CONTENT}}
```

其中 `compression_level` 和 `heading_offset` 都由顶部配置实时生成。

## 文件结构

```text
.
├── index.html   # 单页应用，包含 HTML、CSS 和 JavaScript
└── README.md    # 项目说明
```

## 本地运行

这个项目是纯静态页面，直接打开即可：

```text
index.html
```

如果浏览器限制剪贴板权限，可以用本地静态服务器打开，例如：

```bash
python -m http.server 8000
```

然后访问：

```text
http://localhost:8000
```

## 维护说明

- 修改基础 Prompt：编辑 `index.html` 中的 `basePrompt`。
- 修改压缩等级：编辑 `compression` 对象。
- 修改标题映射规则：编辑 `getHeadingRule()`。
- 修改最终拼接顺序：编辑 `buildPrompt()`。
- 修改界面布局和样式：编辑 `<style>` 中的 CSS。

## 适用场景

- 把 ChatGPT、Claude、Gemini 等模型的长对话整理成知识库笔记。
- 把课程问答、技术解释、论文阅读对话转成 Markdown。
- 为 Obsidian、Notion、语雀、飞书文档等知识库生成高密度笔记草稿。
- 在不同笔记层级规范之间快速调整 Markdown 标题结构。

## 注意事项

- 本工具只生成 Prompt，不会直接调用模型 API。
- 输出质量仍取决于你使用的大模型以及原始对话质量。
- 高压缩等级可能删除辅助例子，重要内容建议先使用 `medium` 或 `light`。
- 标题映射会硬性指定层级，适合需要稳定 Markdown 结构的笔记工作流。
