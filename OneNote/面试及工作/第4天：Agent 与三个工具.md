---
onenote-id: cb687cb1-21ff-4ad9-a067-20f889401da4:1
---
**第4天：Agent 与三个工具**

**上午：Agent 核心原理**

要理解 Agent 不是单纯聊天，而是循环决策系统：

\[

\text{目标}

\rightarrow

\text{规划}

\rightarrow

\text{调用工具}

\rightarrow

\text{观察结果}

\rightarrow

\text{继续行动}

\]

典型循环：

\[

\text{Thought}

\rightarrow

\text{Action}

\rightarrow

\text{Observation}

\rightarrow

\text{Thought}

\]

需要掌握：

- Tool Calling；
- Function Calling；
- ReAct；
- Planning；
- Memory；
- RAG；
- MCP；
- Workflow 与 Agent 的区别；
- 工具调用失败后的重试；
- 权限控制；
- Prompt Injection；
- 任务执行的可观测性。

工具函数一般由名称、描述和参数 Schema 组成，例如：

{  
  "name": "search_document",  
  "description": "检索内部技术文档",  
  "parameters": {  
    "query": "string",  
    "top_k": "integer"  
  }  
}

模型不直接执行工具，而是生成调用请求，程序负责执行并返回结果。

**下午：Claude Code 实操**

Claude Code 是运行在终端中的 agentic coding 工具，可以理解代码库、执行常规开发任务，并处理 Git 工作流。([GitHub](https://github.com/anthropics/claude-code?utm_source=chatgpt.com))

一天内至少完成这些操作：

1. 进入一个 Python 项目；
1. 让它解释目录结构；
1. 找到一个函数的调用链；
1. 修复一个人为制造的 Bug；
1. 生成单元测试；
1. 运行测试；
1. 查看代码差异；
1. 让它编写 README；
1. 学会限制允许执行的命令；
1. 不盲目接受生成代码，自己验证结果。

建议用你现有的联邦学习或 RAG 项目练习，而不是创建毫无背景的 Demo。

**晚上：OpenClaw 与 Hermes**

**OpenClaw**

OpenClaw 的定位是自托管网关，把聊天软件、插件和 AI Agent 连接起来，使助手能够持续运行和执行任务。官方文档列出了 Telegram、WhatsApp、Slack、Teams 等多种渠道。([OpenClaw](https://docs.openclaw.ai/?utm_source=chatgpt.com))

一天内重点了解：

- Gateway；
- Channel；
- Agent；
- Session；
- Tool；
- Plugin；
- 本地部署与服务器部署；
- 权限和凭证管理；
- 为什么高权限 Agent 有安全风险。

不必五天内精通所有部署，只需要能解释架构并完成基本安装或阅读 Quick Start。

**Hermes Agent**

Hermes Agent 强调内置学习循环，会从执行经验中创建或改进 Skills，并保留跨会话知识。([GitHub](https://github.com/nousresearch/hermes-agent?utm_source=chatgpt.com))

重点理解：

- Skill；
- Memory；
- Learning Loop；
- 任务经验如何复用；
- 与普通一次性聊天机器人的区别；
- 与 OpenClaw 的定位差异。

**三者对比**

| **工具** | **重点** |
| --- | --- |
| Claude Code | 代码仓库理解与开发执行 |
| OpenClaw | 消息渠道、工具和长期在线助手的连接层 |
| Hermes Agent | 经验学习、技能沉淀与持续改进 |

**第4天产出**

准备一个两分钟回答：

我使用 Claude Code 完成了什么任务？它如何读取项目、修改代码、运行测试？我如何确保生成代码安全可靠？