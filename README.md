# 🌟 Awesome AI Agent Learning

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> 🤖 一个结构化、持续更新的 AI Agent 学习资料汇总库。从基础理论到前沿框架，从经典论文到实战项目，陪你从零构建属于自己的智能体。

AI Agent（人工智能体）正引领着下一代应用架构的变革。本项目致力于整合碎片化的学习资源，为初学者提供清晰的学习路径，为进阶开发者提供趁手的工具检索。

**难度标注说明：** 🟢 入门 | 🟡 进阶 | 🔴 高级

---

## 📑 目录 (Table of Contents)

- [🗺️ 学习路线图 (Learning Roadmap)](#️-学习路线图-learning-roadmap)
- [🧠 核心概念速查 (Key Concepts)](#-核心概念速查-key-concepts)
- [📚 基础理论 (Foundations)](#-基础理论-foundations)
  - [核心论文 (Must-Read Papers)](#核心论文-must-read-papers)
  - [深度解析文章 (Deep Dive Articles)](#深度解析文章-deep-dive-articles)
- [🛠️ 框架与工具 (Frameworks & Tools)](#️-框架与工具-frameworks--tools)
  - [主流 Agent 框架](#主流-agent-框架)
  - [工具链与记忆库 (Toolchains & Memory)](#工具链与记忆库-toolchains--memory)
- [🚀 实战与教程 (Tutorials & Projects)](#-实战与教程-tutorials--projects)
  - [入门级教程 (Step-by-step)](#入门级教程-step-by-step)
  - [优秀的开源 Agent](#优秀的开源-agent)
- [📺 视频与课程 (Videos & Courses)](#-视频与课程-videos--courses)
- [🏗️ Agent 设计模式 (Design Patterns)](#️-agent-设计模式-design-patterns)
- [🧪 评估与基准 (Evaluation & Benchmarks)](#-评估与基准-evaluation--benchmarks)
- [📖 推荐书籍 (Books)](#-推荐书籍-books)
- [📰 社区与资讯 (Communities & News)](#-社区与资讯-communities--news)
- [🤝 贡献指南 (Contributing)](#-贡献指南-contributing)

---

## 🗺️ 学习路线图 (Learning Roadmap)

> 不知道从哪里开始？跟着这份路线图，一步一步成为 Agent 高手。

```
🟢 第一阶段：打好基础（1-2 周）
│
├── 理解 LLM 基础（Prompt Engineering, In-Context Learning）
├── 阅读 Lilian Weng 的 Agent 综述长文
├── 学习核心概念：ReAct、CoT、Tool Use
└── 动手跑通一个简单的 LangChain Agent Demo
│
🟡 第二阶段：框架实战（2-4 周）
│
├── 深入学习一个主流框架（推荐 LangChain / LangGraph）
├── 阅读 ReAct、Toolformer、Reflexion 论文
├── 构建一个完整的 RAG + Agent 应用
└── 尝试多 Agent 协作框架（AutoGen / CrewAI）
│
🔴 第三阶段：深入探索（持续）
│
├── 研读 Generative Agents、Voyager 等前沿论文
├── 设计并实现自定义 Agent 架构
├── 学习 Agent 评估方法与基准测试
└── 关注社区动态，参与开源项目贡献
```

---

## 🧠 核心概念速查 (Key Concepts)

> 快速理解 Agent 领域的关键术语。

| 概念 | 英文 | 一句话解释 |
| :--- | :--- | :--- |
| **思维链** | Chain-of-Thought (CoT) | 让 LLM 逐步推理，而非直接给出答案，显著提升复杂任务表现。 |
| **推理+行动** | ReAct | 将推理（Reasoning）和行动（Acting）交替进行的 Agent 范式。 |
| **工具调用** | Tool Use / Function Calling | Agent 调用外部工具（API、代码执行器、搜索引擎等）来扩展能力。 |
| **规划** | Planning | Agent 将复杂任务分解为子目标，并制定执行计划的能力。 |
| **记忆** | Memory | Agent 存储和检索历史信息的机制，分为短期记忆和长期记忆。 |
| **反思** | Reflexion | Agent 通过回顾自身行为和结果来自我改进。 |
| **多智能体** | Multi-Agent | 多个 Agent 协作或对话完成复杂任务的架构。 |
| **检索增强生成** | RAG | 结合外部知识检索与 LLM 生成，减少幻觉并增强事实准确性。 |
| **智能体循环** | Agent Loop | Agent 感知 → 思考 → 行动 → 观察的核心执行循环。 |

---

## 📚 基础理论 (Foundations)

### 核心论文 (Must-Read Papers)

> 了解 Agent 的思考方式：规划、记忆与工具调用。

* 🟢 [**Chain-of-Thought Prompting** (2022): Eliciting Reasoning in Large Language Models](https://arxiv.org/abs/2201.11903) - 通过逐步推理提升 LLM 解决复杂问题的能力，Agent 推理的基石。 `[Reasoning]`
* 🟢 [**ReAct** (2022): Synergizing Reasoning and Acting in Language Models](https://arxiv.org/abs/2210.03629) - 提出将大模型的推理与动作执行结合的经典范式。 `[Reasoning] [Acting]`
* 🟢 [**MRKL Systems** (2022): A Modular, Neuro-Symbolic Architecture](https://arxiv.org/abs/2205.00445) - 模块化推理+知识+语言系统，Tool-Use Agent 的理论基础。 `[Architecture] [Tool Use]`
* 🟡 [**Toolformer** (2023): Language Models Can Teach Themselves to Use Tools](https://arxiv.org/abs/2302.04761) - LLM 自主学习使用工具的开创性论文。 `[Tool Use]`
* 🟡 [**HuggingGPT** (2023): Solving AI Tasks with ChatGPT and its Friends in Hugging Face](https://arxiv.org/abs/2303.17580) - 用 LLM 作为控制器调度多种 AI 模型协作。 `[Multi-Model] [Planning]`
* 🟡 [**Reflexion** (2023): Language Agents with Verbal Reinforcement Learning](https://arxiv.org/abs/2303.11366) - Agent 通过语言化的自我反思来改进后续行为。 `[Self-Improvement] [Reflexion]`
* 🟡 [**Generative Agents** (2023): Interactive Simulacra of Human Behavior](https://arxiv.org/abs/2304.03442) - 斯坦福"西部世界"小镇，探讨多智能体社会的里程碑。 `[Multi-Agent] [Simulation]`
* 🔴 [**Voyager** (2023): An Open-Ended Embodied Agent with Large Language Models](https://arxiv.org/abs/2305.16291) - 在 Minecraft 中持续学习的 Agent，展示终身学习能力。 `[Lifelong Learning] [Embodied]`

📌 *欢迎通过 [PR](./CONTRIBUTING.md) 推荐更多优质论文！*

### 深度解析文章 (Deep Dive Articles)

> 比论文更易读，比博客更深入的精选解读。

* 🟢 [LLM Powered Autonomous Agents](https://lilianweng.github.io/posts/2023-06-23-agent/) - OpenAI Lilian Weng 撰写的万字长文，Agent 领域的必读圣经。
* 🟢 [Building LLM applications for production](https://huyenchip.com/2023/04/11/llm-engineering.html) - Chip Huyen 关于 LLM 应用工程化的深度思考。
* 🟡 [The Landscape of Emerging AI Agent Architectures for Reasoning, Planning, and Tool Calling](https://arxiv.org/abs/2404.11584) - 2024 年对 Agent 架构全景的综述。

📌 *欢迎通过 [PR](./CONTRIBUTING.md) 推荐优秀的博客、知乎或 Medium 文章！*

---

## 🛠️ 框架与工具 (Frameworks & Tools)

### 主流 Agent 框架

> 选择适合你项目的 Agent 框架，快速开始构建。

| 框架名称 | 核心特点 | 适用场景 | 语言 | 难度 |
| :--- | :--- | :--- | :--- | :---: |
| **[LangChain](https://github.com/langchain-ai/langchain)** | 生态最庞大，组件极其丰富 | 构建复杂的 LLM 应用，快速实现原型 | Python / JS | 🟢 |
| **[LangGraph](https://github.com/langchain-ai/langgraph)** | 基于图的 Agent 编排，支持循环与状态管理 | 需要复杂状态管理和循环流程的 Agent | Python / JS | 🟡 |
| **[AutoGen](https://github.com/microsoft/autogen)** | 微软出品，主打多智能体对话协作 | 需要多个不同角色 Agent 协同完成任务 | Python | 🟡 |
| **[CrewAI](https://github.com/joaomdmoura/crewai)** | 基于角色的协同框架，API 极其优雅 | 自动化团队工作流（如写作团队、研发团队） | Python | 🟢 |
| **[Semantic Kernel](https://github.com/microsoft/semantic-kernel)** | 微软出品，企业级 AI 编排 SDK | 企业级应用集成、.NET 生态 | C# / Python / Java | 🟡 |
| **[Dify](https://github.com/langgenius/dify)** | 开源 LLMOps 平台，可视化编排 | 快速搭建 Agent 应用，低代码场景 | Python | 🟢 |
| **[Camel](https://github.com/camel-ai/camel)** | 角色扮演式多智能体交互框架 | 研究多智能体协作与对话 | Python | 🟡 |

### 工具链与记忆库 (Toolchains & Memory)

> Agent 的"外挂装备"：记忆、工具、知识库。

* **[Mem0](https://github.com/mem0ai/mem0)** - 专为 AI Agent 设计的增强记忆层，支持跨会话的记忆管理。
* **[ChromaDB](https://github.com/chroma-core/chroma)** - 开源嵌入式向量数据库，轻量易用，适合快速原型。
* **[Milvus](https://github.com/milvus-io/milvus)** - 高性能分布式向量数据库，适合大规模生产环境。
* **[Composio](https://github.com/ComposioHQ/composio)** - 为 Agent 提供 150+ 工具集成的平台。

📌 *欢迎通过 [PR](./CONTRIBUTING.md) 推荐更多实用工具！*

---

## 🚀 实战与教程 (Tutorials & Projects)

### 入门级教程 (Step-by-step)

> 动手做起来！从 Hello World 到完整应用。

* 🟢 [LangChain 官方教程](https://python.langchain.com/docs/tutorials/) - 从基础到进阶的官方系列教程。
* 🟢 [LangGraph 快速入门](https://langchain-ai.github.io/langgraph/tutorials/introduction/) - 通过示例学习基于图的 Agent 编排。
* 🟡 [从零手写一个 ReAct Agent](https://til.simonwillison.net/llms/python-react-pattern) - Simon Willison 用 Python 从零实现 ReAct 模式。

📌 *欢迎通过 [PR](./CONTRIBUTING.md) 推荐更多从零手写 Agent 的教程！*

### 优秀的开源 Agent

> 看看别人怎么做的，站在巨人肩膀上学习。

* 🟢 **[AutoGPT](https://github.com/Significant-Gravitas/AutoGPT)** - 最早引爆全网的自主 Agent 标杆项目。
* 🟢 **[MetaGPT](https://github.com/geekan/MetaGPT)** - 模拟一个完整的软件公司开发团队，多角色协同。
* 🟡 **[Open Interpreter](https://github.com/OpenInterpreter/open-interpreter)** - 让 LLM 在本地执行代码的 Agent，自然语言操控计算机。
* 🟡 **[GPT Researcher](https://github.com/assafelovic/gpt-researcher)** - 自主深度研究 Agent，自动搜索、整合、生成研究报告。
* 🔴 **[SWE-agent](https://github.com/princeton-nlp/SWE-agent)** - 普林斯顿出品，自动修复 GitHub Issue 的软件工程 Agent。
* 🔴 **[Devon](https://github.com/entropy-research/Devon)** - 开源的 AI 结对编程 Agent。

---

## 📺 视频与课程 (Videos & Courses)

> 听大佬讲课，看实操演示。

* 🟢 [吴恩达：LangChain for LLM Application Development](https://www.deeplearning.ai/short-courses/langchain-for-llm-application-development/) - 大模型应用开发的经典入门课程。
* 🟢 [吴恩达：Building Systems with the ChatGPT API](https://www.deeplearning.ai/short-courses/building-systems-with-chatgpt/) - 学习用 ChatGPT API 构建完整系统。
* 🟡 [吴恩达：AI Agentic Design Patterns with AutoGen](https://www.deeplearning.ai/short-courses/ai-agentic-design-patterns-with-autogen/) - 多智能体设计模式实战。
* 🟡 [吴恩达：Multi AI Agent Systems with crewAI](https://www.deeplearning.ai/short-courses/multi-ai-agent-systems-with-crewai/) - 基于 CrewAI 的多 Agent 系统课程。
* 🟡 [吴恩达：AI Agents in LangGraph](https://www.deeplearning.ai/short-courses/ai-agents-in-langgraph/) - LangGraph 实战课程。

📌 *欢迎通过 [PR](./CONTRIBUTING.md) 推荐 YouTube、B 站等平台的优质视频！*

---

## 🏗️ Agent 设计模式 (Design Patterns)

> 构建 Agent 的常见架构模式，从理论到实践的桥梁。

### ReAct Loop（推理-行动循环）
最经典的 Agent 模式。Agent 在每一步中先进行**推理**（Thought），然后执行**行动**（Action），再**观察**结果（Observation），循环往复直到完成任务。
```
Thought → Action → Observation → Thought → Action → Observation → ... → Final Answer
```

### Plan-and-Execute（规划-执行）
Agent 首先制定全局**计划**，然后逐步**执行**每个子任务。适合复杂、多步骤的任务。
```
Task → Planner (生成步骤列表) → Executor (依次执行) → Re-planner (必要时调整) → Done
```

### Multi-Agent Debate（多智能体辩论）
多个 Agent 通过**辩论和讨论**来改进答案质量。不同 Agent 可扮演不同角色（如正方/反方、审稿人/作者）。
```
Agent A (观点) → Agent B (反驳) → Agent A (修正) → ... → 共识
```

### Reflection（反思模式）
Agent 执行任务后进行**自我评估和反思**，利用反馈改进后续行为。
```
Task → Action → Result → Self-Critique → Improved Action → Better Result
```

### Tool-Augmented Agent（工具增强）
Agent 根据需要动态选择并调用**外部工具**（搜索引擎、代码执行器、API 等），扩展自身能力边界。
```
Query → Select Tool → Call Tool → Parse Result → Generate Response
```

---

## 🧪 评估与基准 (Evaluation & Benchmarks)

> 如何衡量你的 Agent 到底行不行？

* **[AgentBench](https://github.com/THUDM/AgentBench)** - 清华大学提出的综合性 Agent 评测框架，覆盖 8 个不同环境。
* **[SWE-bench](https://github.com/princeton-nlp/SWE-bench)** - 评测 Agent 自动修复真实 GitHub Issue 的能力。
* **[WebArena](https://github.com/web-arena-x/webarena)** - 真实网页环境中的 Agent 评测基准。
* **[GAIA](https://huggingface.co/gaia-benchmark)** - 通用 AI 助手的综合评测基准。

📌 *欢迎通过 [PR](./CONTRIBUTING.md) 推荐更多评测工具和基准！*

---

## 📖 推荐书籍 (Books)

> Agent 领域发展迅速，以下书籍提供扎实的基础知识。

* 🟢 《Prompt Engineering for Generative AI》- 扎实掌握 Prompt 工程，Agent 开发的基本功。
* 🟡 《Building LLM Apps》- 从概念到生产部署的 LLM 应用构建指南。
* 🟡 《Designing Large Language Model Applications》- 大语言模型应用的系统设计方法。

📌 *欢迎通过 [PR](./CONTRIBUTING.md) 推荐更多相关书籍！*

---

## 📰 社区与资讯 (Communities & News)

> 保持对前沿动态的持续关注。

### Newsletter & 博客
* [The Batch](https://www.deeplearning.ai/the-batch/) - 吴恩达主理的 AI 周报。
* [AI Agent 周报](https://www.agentailabs.com/) - 专注 Agent 领域的中文周报。
* [Latent Space Podcast](https://www.latent.space/) - 深度 AI 工程话题播客。

### 社区
* [r/LangChain](https://www.reddit.com/r/LangChain/) - LangChain Reddit 社区。
* [LangChain Discord](https://discord.gg/langchain) - LangChain 官方 Discord。
* [AutoGen Discord](https://discord.gg/pAbnFJrkgZ) - AutoGen 官方 Discord。

### 值得关注的 Twitter/X 账号
* [@AndrewYNg](https://twitter.com/AndrewYNg) - 吴恩达，AI 领域意见领袖。
* [@LangChainAI](https://twitter.com/LangChainAI) - LangChain 官方。
* [@kaboramia](https://twitter.com/karpathy) - Andrej Karpathy，原 OpenAI/Tesla AI 负责人。
* [@laboramia](https://twitter.com/lilianweng) - Lilian Weng，OpenAI。

---

## 🤝 贡献指南 (Contributing)

欢迎提交 Pull Request 来完善这个项目！在提交之前，请确保：

1. ✅ 推荐的资源质量高、与 AI Agent 强相关
2. ✅ 附带一句简短准确的**中文描述**
3. ✅ 标注难度等级（🟢 入门 / 🟡 进阶 / 🔴 高级）
4. ✅ 确保提供的链接有效

详情请参考 [CONTRIBUTING.md](./CONTRIBUTING.md)。

---

## ⭐ Star History

如果这个项目对你有帮助，请给一颗 ⭐ Star 支持！

---

## 📄 License

本项目采用 [MIT License](./LICENSE) 开源协议。
