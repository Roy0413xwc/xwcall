---
onenote-id: 6d2f2363-5910-4bbd-b73f-3c443f193332:1
---
![[面试--Hello Agent开源项目学习 image.png]]

![[面试--Hello Agent开源项目学习 image 1.png]]

==🟡开源项目====🟡6.23/6.24====🟡/6.25==

https://datawhalechina.github.io/hello-agents/#/./chapter1/%E7%AC%AC%E4%B8%80%E7%AB%A0%20%E5%88%9D%E8%AF%86%E6%99%BA%E8%83%BD%E4%BD%93

[datawhalechina/hello-agents · Discussions · GitHub](https://github.com/datawhalechina/Hello-Agents/discussions)讨论区有代码

[hello-agents/Extra-Chapter/Extra01-面试问题总结.md at main · datawhalechina/hello-agents](https://github.com/datawhalechina/hello-agents/blob/main/Extra-Chapter/Extra01-%25E9%259D%25A2%25E8%25AF%2595%25E9%2597%25AE%25E9%25A2%2598%25E6%2580%25BB%25E7%25BB%2593.md)

[datawhalechina/Agent-Learning-Hub: AI Agent 学习路线与资料库收集](https://github.com/datawhalechina/Agent-Learning-Hub)

![[面试--Hello Agent开源项目学习 image 2.png]]

由 Thought、Action、Observation 构成的严谨循环，LLM 智能体得以将内部的语言推理能力，与外部环境的真实信息和工具操作能力有效地结合起来

![[面试--Hello Agent开源项目学习 image 3.png]]

至此，智能体发展的历史长河中，几大关键的技术拼图已经悉数登场：符号主义提供了逻辑推理的框架，联结主义和强化学习提供了学习与决策的能力，而大型语言模型则提供了前所未有的、通过预训练获得的世界知识和通用推理能力。下一节，我们将看到这些技术是如何在现代智能体的设计中融为一体的。

![[面试--Hello Agent开源项目学习 image 4.png]]

![[面试--Hello Agent开源项目学习 image 5.png]]

为了实现上述过程，自注意力机制为每个输入的词元向量引入了三个可学习的角色：

- 查询 (Query, Q)：代表当前词元，它正在主动地“查询”其他词元以获取信息。
- 键 (Key, K)：代表句子中可被查询的词元“标签”或“索引”。
- 值 (Value, V)：代表词元本身所携带的“内容”或“信息”。

来自 \<https://datawhalechina.github.io/hello-agents/#/./chapter3/%E7%AC%AC%E4%B8%89%E7%AB%A0%20%E5%A4%A7%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B%E5%9F%BA%E7%A1%80>

![[面试--Hello Agent开源项目学习 image 6.png]]

在文本生成中，当同时设置 Top-p、Top-k 和温度系数时，这些参数会按照分层过滤的方式协同工作，其优先级顺序为：温度调整→Top-k→Top-p。温度调整整体分布的陡峭程度，Top-k 会先保留概率最高的 k 个候选，然后 Top-p 会从 Top-k 的结果中选取累积概率≥p 的最小集合作为最终的候选集。不过，通常 Top-k 和 Top-p 二选一即可，若同时设置，实际候选集为两者的交集。 需要注意的是，如果将温度设置为 0，则 Top-k 和 Top-p 将变得无关紧要，因为最有可能的 Token 将成为下一个预测的 Token；如果将 Top-k 设置为 1，温度和 Top-p 也将变得无关紧要，因为只有一个 Token 通过 Top-k 标准，它将是下一个预测的 Token。

来自 \<https://datawhalechina.github.io/hello-agents/#/./chapter3/%E7%AC%AC%E4%B8%89%E7%AB%A0%20%E5%A4%A7%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B%E5%9F%BA%E7%A1%80?id=_321-%e6%8f%90%e7%a4%ba%e5%b7%a5%e7%a8%8b>

模型参数量和训练数据量之间存在一个最优配比

来自 \<https://datawhalechina.github.io/hello-agents/#/./chapter3/%E7%AC%AC%E4%B8%89%E7%AB%A0%20%E5%A4%A7%E8%AF%AD%E8%A8%80%E6%A8%A1%E5%9E%8B%E5%9F%BA%E7%A1%80?id=_331-%e7%bc%a9%e6%94%be%e6%b3%95%e5%88%99>

- ReAct：边思考，边行动，边观察
- Plan-and-Solve：先制定计划，再逐步执行
- Reflection：**先生成答案，再检查答案，再根据反馈修改**
- **下面的问题没仔细看**

![[面试--Hello Agent开源项目学习 image 7.png]]