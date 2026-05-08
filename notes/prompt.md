请对这篇关于“使用 RNN/LSTM 做输入法下一词预测（next word prediction / keyboard suggestion）”的论文进行一次深入技术研究。

我的目标不是只看懂论文，而是理解：

1. 论文的完整技术路线
   - 输入是什么
   - 输出是什么
   - 模型结构是什么
   - 为什么选择 RNN/LSTM
   - hidden state 在输入法场景中代表什么
   - 如何进行训练
   - loss 是什么
   - inference 如何部署在手机端
   - latency / memory / battery constraints 如何处理

2. 输入法中的“下一词预测”问题本质是什么
   - 和传统 n-gram 的区别
   - 和规则模板的区别
   - 和语义检索候选的区别
   - 为什么 RNN 在当时是重要突破

3. 论文的创新点
   - 相比当年的输入法方案提升在哪里
   - 相比 n-gram/FST 的优势
   - 是否解决了长上下文问题
   - 是否支持 personalization
   - 是否支持 federated learning
   - 工程上最关键的优化是什么

4. 从现代（2025-2026）的视角重新评价这篇论文
   - 哪些思想已经过时
   - 哪些思想仍然被保留
   - RNN/LSTM 为什么逐渐被 Transformer 替代
   - RNN 在输入法场景中的核心缺陷是什么
   - 手机上的推理瓶颈是什么

5. 现代输入法（Gboard / SwiftKey / Apple Keyboard）现在主要采用什么方案
   - Transformer LM?
   - Tiny Transformer?
   - Distilled LLM?
   - Retrieval + rerank?
   - Personalized on-device adaptation?
   - Federated learning?
   - Mixture of experts?
   - Cache-based language model?
   - Hybrid architecture?

6. 如果今天重新设计一个“下一词推荐系统”，有哪些现代方案？
   请分别分析：
   - Transformer LM
   - Tiny LLM
   - Retrieval-augmented prediction
   - User memory embedding
   - Semantic cache
   - Hybrid n-gram + neural
   - Personalized reranker
   - Local-only inference
   - Cloud-assisted inference
   - Edge AI deployment

7. 请给出：
   - 技术演化时间线
   - 从 T9 → n-gram → RNN → Transformer → LLM 的发展脉络
   - 每一代为什么出现
   - 每一代解决了什么问题
   - 每一代新增了什么问题

8. 请最后回答：
   如果一个大学生想自己实现一个“输入法下一词推荐插件”，
   哪种技术路线最现实？
   
   请分别评价：
   - 工程难度
   - 数据需求
   - 推理成本
   - 手机上的可部署性
   - 用户体验
   - 可扩展性

请不要只停留在论文摘要层面，而是：
- 从 NLP
- 系统设计
- 移动端部署
- 人机交互
- 工业输入法架构

几个角度综合分析。

我希望得到的是：
“为什么输入法会发展成今天这样”的完整理解。