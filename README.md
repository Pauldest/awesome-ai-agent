# 🌟 Awesome AI Agent

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> 🤖 一份结构化的 AI Agent 领域全景图与学习指南。先看懂全貌，再按需深入。

---

# Part 1: 全景认知

> 在一头扎进论文和框架之前，先花 5 分钟搞清楚这个领域的全貌。

## 🤖 AI Agent 是什么

**AI Agent（智能体）= LLM + 感知 + 推理 + 规划 + 记忆 + 行动**

传统的 ChatBot 只是"你问我答"，而 AI Agent 能够**自主地**感知环境、制定计划、调用工具、执行行动，并根据结果不断调整——就像一个真正的"数字员工"。

```
             ┌──────────────────────────────────────┐
             │            🧠 LLM（大脑）              │
             │    理解意图 · 推理判断 · 生成决策        │
             └──────────┬───────────────┬───────────┘
                        │               │
              ┌─────────▼──┐     ┌──────▼────────┐
              │  📋 规划     │     │  💾 记忆        │
              │ 任务分解     │     │ 短期/长期记忆   │
              │ 步骤编排     │     │ 经验积累       │
              └─────────┬──┘     └──────┬────────┘
                        │               │
              ┌─────────▼───────────────▼────────┐
              │          🔧 工具调用 & 行动         │
              │  API · 代码执行 · 搜索 · 数据库     │
              └──────────────────────────────────┘
```

### Agent vs Copilot vs ChatBot

| | ChatBot | Copilot | **Agent** |
|:---|:---|:---|:---|
| **交互模式** | 你问我答 | 你做我辅助 | **你定目标，我自主完成** |
| **自主性** | ❌ 无 | 🔶 部分 | ✅ 高度自主 |
| **工具调用** | ❌ | 🔶 有限 | ✅ 丰富且动态 |
| **多步推理** | ❌ | 🔶 | ✅ 规划+执行+反思 |
| **典型产品** | 早期 ChatGPT | GitHub Copilot | AutoGPT, Manus, Claude Code |

## 🔥 为什么 AI Agent 是下一个风口

### 市场数据

- **2025 年全球 AI Agent 市场规模约 $80 亿**，预计 2030 年超过 **$500 亿**（CAGR 46%+）
- Gartner 预测：到 2028 年，**33% 的企业软件将内嵌 Agent 能力**
- 2025 被业界称为 **"Agent 元年"**——从实验走向生产

### 落地场景一览

| 场景 | Agent 做什么 | 代表产品/项目 |
|:---|:---|:---|
| 🖥️ 软件开发 | 自动写代码、修 Bug、做 Code Review | Cursor, Claude Code, SWE-agent |
| 🔍 深度研究 | 自动搜索、整合信息、撰写报告 | GPT Researcher, Gemini Deep Research |
| 🛒 客服与销售 | 7×24 智能客服、个性化推荐 | Salesforce Agentforce |
| 💰 金融 | 风控分析、交易策略、合规审查 | Bloomberg Agent |
| 🏥 医疗 | 辅助诊断、患者随访、药物研发 | 各大医疗 AI 公司 |
| 📦 供应链 | 需求预测、智能调度、异常预警 | 各大制造业 AI 项目 |
| 🎨 内容创作 | 自动写作、视频剪辑、多模态生成 | 各类 AIGC 工具 |

## 🏢 大厂在做什么

> 一句话了解各家巨头的 Agent 战略布局。

| 公司 | 核心 Agent 项目 | 关键动作 |
|:---|:---|:---|
| **OpenAI** | Operator（已融入 ChatGPT）、Codex | 多步骤网页任务代理；与 AWS 合作构建 Agent 云平台 |
| **Google** | Agent Development Kit (ADK)、A2A 协议 | 开源 Agent 开发框架；提出 Agent 间通信标准 A2A；搜索进化为 Agentic AI Mode |
| **Microsoft** | Copilot Studio、Agent Factory | 宣布 2026 为"Agent 之年"；推出企业级 Agent 工厂；全面支持 MCP 协议 |
| **Anthropic** | Claude Code、MCP 协议 | 推出行业标准 Model Context Protocol；Claude 深耕 Coding Agent 赛道 |
| **Apple** | 新 Siri、Apple Intelligence | 本地优先策略保护隐私；Xcode 内置 MCP Server 支持 Agentic 开发 |
| **Meta** | Llama 系列开源模型 | 开源大模型降低 Agent 构建门槛 |
| **Salesforce** | Agentforce | 企业级客服/销售 Agent 平台 |

> 📌 *欢迎通过 PR 补充更多厂商的 Agent 布局，尤其是中国厂商（字节、阿里、百度、腾讯等）！*

## 🧑‍💻 成为 Agent 工程师需要什么技能

> Agent 工程师 ≠ 传统 ML 工程师。你不需要从零训练模型，但你需要知道如何**编排和驱动**模型。

### 技术能力栈

```
┌─────────────────────────────────────────────────────────┐
│  🏗️ Agent 架构设计                                       │
│  ReAct · Plan-and-Execute · Multi-Agent · Reflection    │
├─────────────────────────────────────────────────────────┤
│  🔗 LLM 编排 & Prompt Engineering                       │
│  提示工程 · Function Calling · 上下文管理 · 模型选型       │
├─────────────────────────────────────────────────────────┤
│  🗄️ 数据与检索                                           │
│  向量数据库 · RAG Pipeline · Embedding · 知识图谱         │
├─────────────────────────────────────────────────────────┤
│  ⚙️ 工程基础                                             │
│  Python / TypeScript · API 开发 · Docker · CI/CD        │
├─────────────────────────────────────────────────────────┤
│  🛡️ 安全与合规                                           │
│  Guardrails · 幻觉控制 · 权限管理 · 审计日志              │
└─────────────────────────────────────────────────────────┘
```

### 软技能

- **产品思维**：理解用户需求，设计 Agent 的目标和边界
- **系统思维**：设计可靠、可扩展的 Agent 系统
- **持续学习**：这个领域每周都有重大突破，保持学习节奏至关重要

---

# Part 2: 学习指南

> 建立了全局认知后，按你需要的维度深入学习。每个板块独立成章，欢迎通过 PR 持续补充。

**难度标注：** 🟢 入门 | 🟡 进阶 | 🔴 高级

## 📚 必读论文 (Papers)

> 这些论文定义了 Agent 领域的核心范式。建议按顺序阅读。

| 难度 | 论文 | 一句话概括 | 年份 |
|:---:|:---|:---|:---:|
| 🟢 | [Chain-of-Thought Prompting Elicits Reasoning in LLMs](https://arxiv.org/abs/2201.11903) | 让 LLM 学会"逐步思考"，Agent 推理的起点 | 2022 |
| 🟢 | [ReAct: Synergizing Reasoning and Acting](https://arxiv.org/abs/2210.03629) | 推理+行动交替进行，最经典的 Agent 范式 | 2022 |
| 🟢 | [MRKL Systems](https://arxiv.org/abs/2205.00445) | 模块化推理+工具调用的理论基础 | 2022 |
| 🟡 | [Toolformer: LMs Can Teach Themselves to Use Tools](https://arxiv.org/abs/2302.04761) | LLM 自主学习使用工具 | 2023 |
| 🟡 | [HuggingGPT: Solving AI Tasks with ChatGPT and Friends](https://arxiv.org/abs/2303.17580) | 用 LLM 调度多种 AI 模型协作 | 2023 |
| 🟡 | [Reflexion: Language Agents with Verbal Reinforcement Learning](https://arxiv.org/abs/2303.11366) | Agent 通过自我反思改进行为 | 2023 |
| 🟡 | [Generative Agents: Interactive Simulacra of Human Behavior](https://arxiv.org/abs/2304.03442) | 斯坦福"西部世界"小镇，多智能体社会模拟 | 2023 |
| 🔴 | [Voyager: An Open-Ended Embodied Agent with LLMs](https://arxiv.org/abs/2305.16291) | Minecraft 中持续学习的 Agent，终身学习典范 | 2023 |

📌 *[→ 提交更多论文推荐](./CONTRIBUTING.md)*

## 🧠 核心概念速查 (Key Concepts)

> 遇到不熟悉的术语？在这里快速查阅。

| 概念 | 英文 | 一句话解释 |
|:---|:---|:---|
| 思维链 | Chain-of-Thought (CoT) | 让 LLM 逐步推理，而非直接给出答案 |
| 推理-行动 | ReAct | 推理（Thought）→ 行动（Action）→ 观察（Observation）的循环 |
| 工具调用 | Tool Use / Function Calling | Agent 调用外部 API、代码执行器等扩展能力 |
| 规划 | Planning | 将复杂任务拆分为子目标并制定执行计划 |
| 记忆 | Memory | 短期记忆（对话上下文）+ 长期记忆（向量检索） |
| 反思 | Reflexion | Agent 回顾自身表现并自我改进 |
| 多智能体 | Multi-Agent | 多个 Agent 分工协作完成复杂任务 |
| 检索增强生成 | RAG | 结合外部知识检索与生成，减少幻觉 |
| 模型上下文协议 | MCP | Anthropic 提出的标准化工具连接协议 |
| Agent 间通信 | A2A | Google 提出的 Agent 间通信标准协议 |

📌 *[→ 提交更多概念解释](./CONTRIBUTING.md)*

## 🛠️ 必读框架 (Frameworks)

> 选择趁手的工具，事半功倍。

| 框架 | 一句话简介 | 适用场景 | 语言 | 难度 |
|:---|:---|:---|:---|:---:|
| [LangChain](https://github.com/langchain-ai/langchain) | 生态最大的 LLM 应用框架 | 快速原型，复杂应用 | Python/JS | 🟢 |
| [LangGraph](https://github.com/langchain-ai/langgraph) | 基于图的 Agent 状态编排 | 需要循环和复杂状态管理 | Python/JS | 🟡 |
| [CrewAI](https://github.com/joaomdmoura/crewai) | 基于角色的多 Agent 协作 | 团队工作流自动化 | Python | 🟢 |
| [AutoGen](https://github.com/microsoft/autogen) | 微软多智能体对话框架 | 多角色 Agent 协同 | Python | 🟡 |
| [Dify](https://github.com/langgenius/dify) | 可视化 LLMOps 平台 | 低代码快速搭建 Agent | Python | 🟢 |
| [Semantic Kernel](https://github.com/microsoft/semantic-kernel) | 微软企业级 AI 编排 SDK | 企业集成，.NET 生态 | C#/Python/Java | 🟡 |

📌 *[→ 提交更多框架推荐](./CONTRIBUTING.md)*

## 📖 必读书籍 (Books)

> Agent 领域变化极快，但这些书能帮你打下扎实的基础。

| 难度 | 书名 | 关注领域 |
|:---:|:---|:---|
| 🟢 | 《Prompt Engineering for Generative AI》 | Prompt 工程基础，Agent 开发的基本功 |
| 🟡 | 《Building LLM Apps》 | 从概念到生产的 LLM 应用构建 |
| 🟡 | 《Designing Large Language Model Applications》 | LLM 应用的系统设计方法论 |

📌 *[→ 提交更多书籍推荐](./CONTRIBUTING.md)*

## 📺 必看课程 (Courses)

> 跟着大佬动手学。

| 难度 | 课程 | 讲师/平台 |
|:---:|:---|:---|
| 🟢 | [LangChain for LLM Application Development](https://www.deeplearning.ai/short-courses/langchain-for-llm-application-development/) | 吴恩达 × DeepLearning.AI |
| 🟢 | [Building Systems with the ChatGPT API](https://www.deeplearning.ai/short-courses/building-systems-with-chatgpt/) | 吴恩达 × DeepLearning.AI |
| 🟡 | [AI Agentic Design Patterns with AutoGen](https://www.deeplearning.ai/short-courses/ai-agentic-design-patterns-with-autogen/) | 吴恩达 × Microsoft |
| 🟡 | [Multi AI Agent Systems with crewAI](https://www.deeplearning.ai/short-courses/multi-ai-agent-systems-with-crewai/) | 吴恩达 × CrewAI |
| 🟡 | [AI Agents in LangGraph](https://www.deeplearning.ai/short-courses/ai-agents-in-langgraph/) | 吴恩达 × LangChain |

📌 *[→ 提交更多课程推荐（YouTube、B站等均可）](./CONTRIBUTING.md)*

## 🚀 标杆开源项目 (Open Source Projects)

> 读源码是最好的学习方式。

| 难度 | 项目 | 做了什么 |
|:---:|:---|:---|
| 🟢 | [AutoGPT](https://github.com/Significant-Gravitas/AutoGPT) | 最早引爆全网的自主 Agent 标杆 |
| 🟢 | [MetaGPT](https://github.com/geekan/MetaGPT) | 模拟软件公司的多角色协作 Agent |
| 🟡 | [Open Interpreter](https://github.com/OpenInterpreter/open-interpreter) | 自然语言操控本地计算机 |
| 🟡 | [GPT Researcher](https://github.com/assafelovic/gpt-researcher) | 自主深度研究与报告生成 |
| 🔴 | [SWE-agent](https://github.com/princeton-nlp/SWE-agent) | 自动修复 GitHub Issue |
| 🔴 | [Devon](https://github.com/entropy-research/Devon) | 开源 AI 结对编程 Agent |

📌 *[→ 提交更多开源项目推荐](./CONTRIBUTING.md)*

## 🧪 评估基准 (Benchmarks)

> 怎么衡量一个 Agent 到底行不行？

| 基准 | 评测什么 |
|:---|:---|
| [AgentBench](https://github.com/THUDM/AgentBench) | 综合 Agent 能力（8 个不同环境） |
| [SWE-bench](https://github.com/princeton-nlp/SWE-bench) | 自动修复真实 GitHub Issue 的能力 |
| [WebArena](https://github.com/web-arena-x/webarena) | 真实网页环境中的 Agent 表现 |
| [GAIA](https://huggingface.co/gaia-benchmark) | 通用 AI 助手综合能力 |

📌 *[→ 提交更多评测基准](./CONTRIBUTING.md)*

## 🔧 工具链 (Toolchains)

> Agent 的"装备库"。

| 工具 | 用途 |
|:---|:---|
| [Mem0](https://github.com/mem0ai/mem0) | Agent 增强记忆层，跨会话记忆管理 |
| [ChromaDB](https://github.com/chroma-core/chroma) | 轻量级向量数据库 |
| [Milvus](https://github.com/milvus-io/milvus) | 生产级分布式向量数据库 |
| [Composio](https://github.com/ComposioHQ/composio) | 150+ 工具集成平台 |

📌 *[→ 提交更多工具推荐](./CONTRIBUTING.md)*

## 📰 社区与资讯 (Communities)

> 这个领域每周都有新突破，保持连接很重要。

| 类型 | 资源 | 简介 |
|:---|:---|:---|
| 📧 Newsletter | [The Batch](https://www.deeplearning.ai/the-batch/) | 吴恩达的 AI 周报 |
| 🎙️ Podcast | [Latent Space](https://www.latent.space/) | 深度 AI 工程话题 |
| 💬 Discord | [LangChain](https://discord.gg/langchain) | LangChain 官方社区 |
| 💬 Discord | [AutoGen](https://discord.gg/pAbnFJrkgZ) | AutoGen 官方社区 |
| 🐦 Twitter | [@AndrewYNg](https://twitter.com/AndrewYNg) | 吴恩达 |
| 🐦 Twitter | [@LangChainAI](https://twitter.com/LangChainAI) | LangChain 官方 |

📌 *[→ 提交更多社区/资讯源推荐（尤其是中文社区！）](./CONTRIBUTING.md)*

## 📝 深度文章 (Articles)

> 比论文更易读，比博客更深入。

| 难度 | 文章 | 作者 |
|:---:|:---|:---|
| 🟢 | [LLM Powered Autonomous Agents](https://lilianweng.github.io/posts/2023-06-23-agent/) | Lilian Weng (OpenAI) |
| 🟢 | [Building LLM applications for production](https://huyenchip.com/2023/04/11/llm-engineering.html) | Chip Huyen |
| 🟡 | [The Landscape of Emerging AI Agent Architectures](https://arxiv.org/abs/2404.11584) | 综述论文 (2024) |

📌 *[→ 提交更多深度文章推荐（知乎、Medium 等均可）](./CONTRIBUTING.md)*

---

## 🤝 贡献指南

这个项目的价值来自社区的每一份贡献。**Part 1（全景认知）** 相对稳定，**Part 2（学习指南）** 是持续生长的——欢迎你来填充！

### 如何贡献

1. **找到对应板块**：论文 → `必读论文`，框架 → `必读框架`，以此类推
2. **按格式添加一行**：每个板块都是表格，加一行即可
3. **标注难度**：🟢 入门 | 🟡 进阶 | 🔴 高级
4. **附中文简介**：一句话说清楚这个资源是什么
5. **提交 PR**

详情请参考 [CONTRIBUTING.md](./CONTRIBUTING.md)。

---

## 📄 License

[MIT License](./LICENSE) — 自由使用，自由分享。
