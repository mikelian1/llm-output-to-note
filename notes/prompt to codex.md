请生成一个单文件 HTML 页面，用于生成“对话内容 → Markdown 知识笔记”的最终 Prompt。

基础版的 prompt 位于 /prompts/

页面核心功能：
1. 选择压缩等级：never / light / medium / high
2. 设置标题映射：
   - 保持不变：heading_offset = 0
   - 上移 x 级：heading_offset = -x
   - 下移 x 级：heading_offset = +x
3. 文本框输入待转换内容 {{CONTENT}}
4. 生成最终 Prompt
5. 一键复制最终 Prompt

页面要求：
- 单文件 HTML，包含 CSS 和 JS，不依赖后端。
- UI 简洁，适合本地打开使用。
- 保留一个大文本框用于粘贴待转换内容。
- 最终 Prompt 区域可预览、可复制。
- 复制成功后给出简短提示。
- 压缩等级与标题映射要分别插入对应的定制化 prompt 片段，其内容分别在 /prompts/compression level/ 和 /prompts/title mapping。
- 基础 Prompt 使用我提供的“知识编译器”初稿内容。
- 生成代码时请直接输出完整 HTML 文件内容，不要解释。