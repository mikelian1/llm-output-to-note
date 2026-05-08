##
请生成一个单文件 HTML 页面，用于生成“对话内容 → Markdown 知识笔记”的最终 Prompt。

基础版的 prompt 位于 /prompts/

## 页面核心功能：
1. 选择压缩等级：never / light / medium / high
2. 设置标题映射：
   - 保持不变：heading_offset = 0
   - 上移 x 级：heading_offset = -x
   - 下移 x 级：heading_offset = +x
3. 文本框输入待转换内容 {{CONTENT}}
4. 生成最终 Prompt
5. 一键复制最终 Prompt

## 页面要求：
- 单文件 HTML，包含 CSS 和 JS，不依赖后端。
- 保留一个大文本框用于粘贴待转换内容。
- 最终 Prompt 区域可预览、可复制。
- 复制成功后给出简短提示。
- 压缩等级与标题映射要分别插入对应的定制化 prompt 片段，其内容分别在 /prompts/compression level/ 和 /prompts/title mapping。
- 基础 Prompt 使用我提供的“知识编译器”初稿内容。
- 生成代码时请直接输出完整 HTML 文件内容，不要解释。

## UI 设计要求：
### 整体风格：
- 极简、现代、偏工程工具风格。
- 类似 Obsidian / Linear / Vercel 风格。
- 深色模式优先，同时支持浅色模式。
- 使用柔和圆角、低对比阴影、适度留白。
- 不要花哨动画。

### 页面布局：
- 顶部：标题与简短说明。
- 中部左侧：配置面板。
- 中部右侧：最终 Prompt 实时预览。
- 底部：待转换内容输入框。

### 配置面板包含：

1. 压缩等级（单选按钮或 segmented control）
- never
- light
- medium
- high

每个选项下附带一句简短说明：
- never：完整保留信息
- light：轻度整理
- medium：高密度知识笔记
- high：极限压缩复习版

2. 标题映射
使用：
- 一个“模式选择”
  - 保持不变
  - 上移
  - 下移
- 一个数字选择器（1~3）

例如：
- 上移 1 级
- 下移 2 级

实时显示：
- h2 → h1
- h3 → h2

3. Prompt 操作区
包含：
- 一键复制 Prompt
- 清空内容
- 恢复默认设置

### Prompt 预览区：
- 使用等宽字体。
- 支持自动换行。
- 可滚动。
- 实时更新。

### 待转换内容输入区：
- 大尺寸 textarea。
- 支持粘贴长文本。
- 自动扩展高度。
- 占页面较大空间。

### 交互细节：
- 点击复制后显示：
  “Copied”
  持续约 1 秒。
- 所有配置修改后即时更新 Prompt。
- 不需要提交按钮。

### 技术要求：
- 单文件 HTML。
- 原生 JS。
- 不依赖后端。
- 尽量不要引入大型框架。