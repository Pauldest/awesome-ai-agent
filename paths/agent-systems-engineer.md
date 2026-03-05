# 🧑‍💻 AI Agent 系统工程师转型路线（4-6 个月）

> **适合谁**：有后端工程经验的开发者（熟悉 Python、API 开发、分布式系统）
> **时长**：4-6 个月（每周 15 小时）
> **最终产出**：具备设计和实现生产级 AI Agent 系统的能力
> **核心理念**：后端工程师 → AI Agent Systems Engineer 的典型转型路径

---

## 总目标

完成后你应该能设计并实现生产级 AI Agent 系统，能力覆盖：

```
LLM 应用 → RAG 系统 → Agent Workflow → Tool Calling → Agent Orchestration → Cost / Reliability / Observability
```

能做出类似：AI Research Agent、Coding Agent、Enterprise Knowledge Agent，甚至 Agent Infrastructure。

---

## 第一阶段：第 1-3 周

### 🎯 LLM 与 Agent 基础

> 理解 LLM 是怎么工作的，Agent 的核心思想是什么。

### 📖 LLM 基础

必须理解的概念：

| 概念 | 为什么重要 |
|:---|:---|
| Token & Context Window | 决定了 Agent 能"看到"多少信息 |
| Temperature & Top-p | 控制 LLM 输出的随机性 |
| Hallucination | Agent 最大的可靠性挑战 |
| Function Calling | Agent 调用工具的核心机制 |

### 📖 Agent 核心概念

| 概念 | 核心思想 |
|:---|:---|
| ReAct | Think → Act → Observe 循环 |
| Tool Use | LLM 负责决策，工具负责执行 |
| Planning | 把复杂任务拆分为可执行的步骤 |
| Memory | 短期（对话）+ 长期（向量检索） |
| Reflection | 自我评估并改进行为 |

### 🔨 项目：简单 Research Agent

用 Python 从零（不用框架）做一个 Research Agent：

| 能力 | 实现 |
|:---|:---|
| 搜索 | 调用搜索 API |
| 读取 | 抓取网页内容 |
| 总结 | LLM 总结信息 |
| 输出 | 生成研究报告 |

**技术栈**：Python、OpenAI API、requests

---

## 第二阶段：第 4-7 周

### 🎯 RAG 与知识库系统

> 几乎所有企业 AI 产品的核心都是 RAG。这是最实用的技能。

### 📖 核心知识

**Embedding：**
- 理解 text → vector 的过程
- Cosine Similarity、ANN Search

**向量数据库：**

| 数据库 | 定位 |
|:---|:---|
| FAISS | 轻量级，适合学习和原型 |
| Milvus | 生产级分布式向量数据库 |
| Pinecone | 云托管向量数据库 |

**RAG Pipeline：**

```
用户问题 → Embedding → 向量检索 → 上下文组装 → LLM 回答
```

**优化方向：**

| 优化点 | 说明 |
|:---|:---|
| Chunk Size | 文档分块大小直接影响检索质量 |
| Top-K | 检索多少条相关文档 |
| Rerank | 对检索结果二次排序 |
| Hybrid Search | 向量检索 + 关键词检索混合 |

### 🔨 项目：企业文档 AI 助手（必做）

| 功能 | 说明 |
|:---|:---|
| 上传文档 | 支持 PDF / Markdown / TXT |
| 自动向量化 | 文档分块 + Embedding + 存储 |
| 智能问答 | 基于文档内容回答问题 |
| 引用来源 | 回答附带原文出处 |

**技术栈**：FastAPI、FAISS、OpenAI

---

## 第三阶段：第 8-13 周

### 🎯 Agent Workflow

> 理解 Agent Runtime 的核心架构，学会编排复杂工作流。

### 📖 核心知识

**Agent Workflow 典型流程：**

```
User Task → Planner（拆任务） → Task Graph → Executor（执行） → Tools（调用工具）
```

**Tool Calling 实践：**

| 工具类型 | 示例 |
|:---|:---|
| 搜索工具 | Web Search API |
| 代码执行 | Python Interpreter |
| 文件操作 | 读写本地文件 |
| 数据库 | SQL 查询 |
| 浏览器 | 网页抓取与操作 |

**Multi-Agent 协作：**

| 角色 | 职责 |
|:---|:---|
| Planner Agent | 分析需求、拆解任务 |
| Worker Agent | 执行具体任务 |
| Reviewer Agent | 质量审查、结果验收 |

**推荐框架**：[LangGraph](https://github.com/langchain-ai/langgraph)（Workflow 清晰、状态机驱动、支持 Multi-Agent）

### 🔨 项目：AI Research Agent（重要）

| 能力 | 说明 |
|:---|:---|
| 自动搜索 | 根据研究主题搜索多个信息源 |
| 阅读网页 | 解析和提取关键信息 |
| 多轮总结 | 逐步深入的信息整合 |
| 报告生成 | 输出结构化研究报告 |

**技术栈**：LangGraph、OpenAI、Browser Tool

---

## 第四阶段：第 14-19 周

### 🎯 Agent 系统架构

> 这一阶段 90% 的人不会。把 Agent 当成分布式系统来设计。

### 📖 Agent Runtime 核心组件

| 组件 | 职责 | 类比 |
|:---|:---|:---|
| Planner | 任务规划与分解 | 类似 DAG 调度器 |
| Executor | 执行具体步骤 | 类似 Worker |
| Memory | 上下文管理与持久化 | 类似缓存 + 数据库 |
| Tool Manager | 工具注册与调度 | 类似服务发现 |
| Scheduler | 任务优先级与并发控制 | 类似任务队列 |

**可参考架构**：Temporal、Azure Durable Functions

### 📖 Agent 调度挑战

Agent 系统会大量调用外部 API，需要解决：

| 挑战 | 解决方案 |
|:---|:---|
| Rate Limit | 令牌桶、滑动窗口限流 |
| Retry | 指数退避重试策略 |
| Queue | 异步任务队列 |
| Priority | 任务优先级调度 |

### 📖 Agent Memory

| 类型 | 说明 |
|:---|:---|
| Conversation Memory | 对话上下文（短期） |
| Vector Memory | 基于 Embedding 的长期知识检索 |
| Episodic Memory | 历史任务经验（反思与学习） |

### 📖 Observability

Agent 最大的工程痛点：**难以调试**。

需要建设：

| 能力 | 说明 |
|:---|:---|
| Trace | 端到端追踪 Agent 的每一步决策 |
| Prompt Logs | 记录每一次 LLM 调用的输入/输出 |
| Tool Logs | 记录工具调用结果 |
| Cost Tracking | Token 消耗和成本追踪 |

### 🔨 项目：Multi-Agent Task System（高级）

| 能力 | 说明 |
|:---|:---|
| 任务队列 | 异步任务提交与执行 |
| Agent Workflow | 多 Agent 协作流水线 |
| Tool Calls | 丰富的工具调用 |
| Rate Limiting | API 调用限流保护 |
| Retry | 失败自动重试 |

**技术栈**：Redis、Queue、Workers、LLM

---

## 第五阶段：第 20-24 周

### 🎯 生产级 Agent

> 从能用到能上线。关注可靠性、成本和安全。

### 📖 成本优化

Agent 很容易 1 个用户请求 → 20+ 次 LLM 调用。

| 策略 | 说明 |
|:---|:---|
| Cache | 缓存重复查询的结果 |
| 小模型 | 简单任务用便宜模型 |
| Planner 优化 | 减少不必要的步骤 |

### 📖 Guardrails

| 风险 | 防护措施 |
|:---|:---|
| Hallucination | 输出验证、事实检查 |
| Unsafe Output | 内容过滤、规则引擎 |
| Infinite Loops | 最大轮数限制、超时机制 |
| 权限越界 | Human-in-the-loop 审批 |

### 📖 Evaluation

| 指标 | 说明 |
|:---|:---|
| Accuracy | 任务完成的正确率 |
| Latency | 端到端响应时间 |
| Cost | 每次任务的 Token 成本 |
| Tool Success Rate | 工具调用的成功率 |

### 🔨 最终项目：AI Knowledge Worker

完整的生产级系统：

| 能力 | 说明 |
|:---|:---|
| 读文档 | 上传并解析各种格式文档 |
| 搜索互联网 | 自动搜索外部信息 |
| 总结信息 | 多源信息整合与总结 |
| 写报告 | 输出结构化报告 |
| 生成 PPT | 可选：自动生成演示文稿 |

**系统架构：**

```
Frontend
  ↓
API (FastAPI)
  ↓
Agent Runtime
  ↓
Tool Layer (Search, Browser, Code Runner)
  ↓
LLM (OpenAI / Claude / Qwen)
  ↓
Vector DB (FAISS / Milvus)
```

---

## 推荐技术栈

| 类别 | 推荐 |
|:---|:---|
| 语言 | Python |
| LLM | OpenAI、Claude、Qwen |
| Agent 框架 | LangGraph、AutoGen |
| RAG | FAISS、Milvus |
| Infra | Redis、FastAPI、Docker |

---

## 时间线总览

| 月份 | 重点 | 项目 |
|:---|:---|:---|
| 第 1 月 | LLM 基础 + RAG | Research Agent + 文档 AI 助手 |
| 第 2 月 | Agent Workflow | AI Research Agent |
| 第 3 月 | Agent 系统架构 | Multi-Agent Task System |
| 第 4 月 | 生产级 Agent | AI Knowledge Worker |

---

## 一句话总结

未来 AI 行业最稀缺的是 **AI Systems Engineer**——

```
LLM + Distributed Systems + Backend Engineering
```

而不是 Prompt Engineer。

---

📌 *如果你有更好的阶段规划或项目建议，欢迎 [提交 PR](../CONTRIBUTING.md)！*
