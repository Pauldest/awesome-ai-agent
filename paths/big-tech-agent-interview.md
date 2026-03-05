# 🏢 大厂 Agent 工程师进阶路线（8-12 周）

> **适合谁**：已有 Agent 项目经验，准备冲击大厂核心 Agent 岗位的工程师
> **前置条件**：完成过至少一个完整 Agent 项目（如 Coding Agent 或 Research Agent）
> **时长**：8-12 周（每周 15-20 小时）
> **目标**：补齐大厂面试和实际工作中最看重的"1→10"能力

---

## 为什么需要这条路径

大厂核心 Agent 岗位（OpenAI、Google、Microsoft、Anthropic、字节、阿里等）除了要你能"做出 Agent"，更看重：

```
你能不能解释 LLM 为什么这样表现？
你能不能设计服务百万用户的 Agent 系统？
你能不能系统性地衡量和改进 Agent 效果？
你能不能保证 Agent 在生产环境中安全可靠？
```

这些是区分"会用 API"和"核心工程师"的关键能力。

---

## 第一阶段：第 1-3 周

### 🎯 LLM 原理与模型层

> 大厂面试必问：你理解 LLM 内部是怎么工作的吗？

### 📖 必须掌握的概念

| 概念 | 为什么重要 |
|:---|:---|
| Transformer 架构 | Agent 的"大脑"是怎么构成的 |
| Self-Attention 机制 | 理解 LLM 如何"关注"上下文中的不同部分 |
| Tokenization (BPE/SentencePiece) | 为什么某些 prompt 效果好、某些差 |
| 位置编码 (RoPE/ALiBi) | 为什么有 context window 限制 |
| KV Cache | 为什么推理速度和内存是这样的 |
| Scaling Laws | 模型越大一定越好吗？什么时候该用小模型 |

### 📖 微调技术

> 核心岗位要求你能针对特定任务优化模型表现，而不只是写 prompt。

| 技术 | 一句话解释 |
|:---|:---|
| SFT (Supervised Fine-Tuning) | 用标注数据教模型完成特定任务 |
| LoRA / QLoRA | 低成本微调，只更新少量参数 |
| RLHF / DPO | 用人类偏好对齐模型输出 |
| Instruction Tuning | 教模型理解和遵循指令 |

### 📚 推荐资源

| 类型 | 资源 | 说明 |
|:---|:---|:---|
| 论文 | [Attention Is All You Need](https://arxiv.org/abs/1706.03762) | Transformer 原始论文，必读 |
| 论文 | [LoRA](https://arxiv.org/abs/2106.09685) | 低秩适配微调 |
| 论文 | [DPO](https://arxiv.org/abs/2305.18290) | 直接偏好优化 |
| 课程 | [Karpathy: Let's build GPT](https://www.youtube.com/watch?v=kCc8FmEb1nY) | 从零实现 GPT，强烈推荐 |
| 课程 | [Stanford CS224N](https://web.stanford.edu/class/cs224n/) | NLP 与深度学习经典课程 |
| 书籍 | 《Build a Large Language Model (From Scratch)》 | 动手从零构建 LLM |

### 🔨 练习

1. 用 Karpathy 的教程从零实现一个 mini-GPT
2. 用 LoRA 对一个开源模型（如 Qwen/Llama）做 SFT，让它更好地完成 tool calling
3. 能白板画出 Transformer 的完整架构并解释每一层

---

## 第二阶段：第 4-5 周

### 🎯 Agent 系统设计

> 大厂面试的灵魂问题：请你设计一个 XXX Agent 系统。

### 📖 系统设计方法论

**Agent 系统设计面试的典型框架：**

```
1. 需求分析
   ├── 功能需求（Agent 能做什么）
   ├── 非功能需求（延迟、吞吐、成本、安全）
   └── 规模估算（日活、QPS、Token 消耗）

2. 高层架构
   ├── 用户接入层（API / CLI / Web）
   ├── Agent 编排层（Runtime / Workflow）
   ├── 工具层（Tools / Plugins）
   ├── 模型层（LLM 调用 / 路由）
   └── 数据层（向量库 / 缓存 / 持久化）

3. 深入设计
   ├── 模型选型与路由策略
   ├── 上下文管理（context window 优化）
   ├── 错误处理与重试
   ├── 安全与权限
   └── 可观测性

4. 规模化
   ├── 水平扩展
   ├── 成本优化
   └── 容灾与降级
```

### 📖 经典设计题

| 设计题 | 考察重点 |
|:---|:---|
| 设计一个 Coding Agent | 代码检索、Multi-Agent、Sandbox、Git 集成 |
| 设计一个 Research Agent | 搜索策略、信息整合、多轮迭代、引用追溯 |
| 设计一个企业知识库 Agent | RAG 架构、权限控制、多租户、数据时效性 |
| 设计一个客服 Agent | 意图识别、工作流路由、人机协作、SLA |
| 设计 Agent 间通信系统 | MCP/A2A 协议、服务发现、消息路由 |

### 📖 模型服务与推理优化

| 技术 | 说明 |
|:---|:---|
| [vLLM](https://github.com/vllm-project/vllm) | 高吞吐 LLM 推理引擎，PagedAttention |
| [TGI](https://github.com/huggingface/text-generation-inference) | HuggingFace 推理服务 |
| Continuous Batching | 动态批处理，提高 GPU 利用率 |
| 量化 (GPTQ/AWQ) | 模型压缩，降低显存需求 |
| Speculative Decoding | 用小模型加速大模型推理 |
| 模型路由 | 简单任务用小模型，复杂任务用大模型 |

### 🔨 练习

1. 白板设计一个 Coding Agent 系统（45 分钟限时）
2. 估算一个日活 10 万用户的 Agent 系统的 Token 成本和基础设施需求
3. 部署 vLLM 服务一个开源模型，做压力测试

---

## 第三阶段：第 6-8 周

### 🎯 评估体系 & 可观测性

> 行业最大痛点：怎么知道你的 Agent 到底行不行？

### 📖 Agent 评估维度

| 维度 | 指标 | 怎么测 |
|:---|:---|:---|
| **正确性** | 任务完成率、答案准确率 | 标注数据集 + 自动评估 |
| **效率** | Token 消耗、工具调用次数、端到端延迟 | 日志统计 |
| **可靠性** | 失败率、重试率、幻觉率 | 线上监控 |
| **安全性** | 拒绝率、越权率、有害输出率 | Red Team 测试 |
| **成本** | 每任务美元成本 | 计费统计 |

### 📖 评估方法

| 方法 | 说明 |
|:---|:---|
| Benchmark 测试 | 在标准数据集上测（SWE-bench、WebArena 等） |
| LLM-as-Judge | 用另一个 LLM 评估 Agent 的输出质量 |
| A/B 测试 | 线上对比不同版本 Agent 的效果 |
| Human Evaluation | 人工审核采样的 Agent 交互 |
| Regression Testing | 每次改动后跑回归测试，防止退化 |

### 📖 可观测性工具

| 工具 | 用途 |
|:---|:---|
| [LangFuse](https://github.com/langfuse/langfuse) | 开源 LLM 可观测平台，Trace + 成本追踪 |
| [Arize Phoenix](https://github.com/Arize-ai/phoenix) | LLM 应用的可观测性和评估 |
| [LangSmith](https://smith.langchain.com/) | LangChain 官方追踪和评估平台 |
| [Weights & Biases](https://wandb.ai/) | 实验追踪和模型评估 |
| OpenTelemetry | 通用可观测性框架，可用于 Agent 追踪 |

### 🔨 练习

1. 为你的 Agent 项目搭建 LangFuse 追踪，记录每一步 LLM 调用
2. 设计一个评估 pipeline：自动跑测试集 + LLM-as-Judge 打分 + 成本统计
3. 建立一个 Agent 质量 Dashboard（通过率、延迟 P50/P99、成本趋势）

---

## 第四阶段：第 9-10 周

### 🎯 安全、对齐与 Guardrails

> Agent 有执行权限（读写文件、调用 API、操作数据库）——安全是头等大事。

### 📖 Agent 安全风险

| 风险类别 | 具体风险 | 防御措施 |
|:---|:---|:---|
| **Prompt Injection** | 用户通过输入操纵 Agent 行为 | 输入过滤、指令隔离 |
| **权限越界** | Agent 访问不应触及的资源 | 最小权限原则、Sandbox |
| **幻觉执行** | Agent 基于错误信息执行操作 | 输出验证、Human-in-the-loop |
| **无限循环** | Agent 陷入重试死循环 | 最大步数限制、超时机制 |
| **数据泄露** | Agent 在响应中暴露敏感信息 | 输出过滤、PII 检测 |
| **供应链攻击** | 恶意工具或插件 | 工具审计、沙箱隔离 |

### 📖 防御实践

| 实践 | 说明 |
|:---|:---|
| Sandbox 执行 | 在隔离容器中运行 Agent 的工具调用 |
| Approval Gates | 高风险操作需要人工审批 |
| Input Guardrails | 检测并拒绝恶意/越界输入 |
| Output Guardrails | 验证 Agent 输出的安全性和准确性 |
| Red Teaming | 主动攻击自己的 Agent，发现漏洞 |
| 审计日志 | 记录 Agent 的每一个决策和行动 |

### 📚 推荐资源

| 类型 | 资源 | 说明 |
|:---|:---|:---|
| 指南 | [OWASP Top 10 for LLMs](https://owasp.org/www-project-top-10-for-large-language-model-applications/) | LLM 应用十大安全风险 |
| 工具 | [Guardrails AI](https://github.com/guardrails-ai/guardrails) | 输出验证框架 |
| 工具 | [NeMo Guardrails](https://github.com/NVIDIA/NeMo-Guardrails) | NVIDIA 的 AI 安全护栏 |

### 🔨 练习

1. 对你的 Agent 做一次 Red Team 测试：尝试 10 种 Prompt Injection 攻击
2. 实现一个完整的 Approval Gate：高风险操作（删除文件、执行命令）需要人工确认
3. 搭建一个 Sandbox：Agent 的代码执行在 Docker 容器中隔离运行

---

## 第五阶段：第 11-12 周

### 🎯 高级 RAG 与前沿技术

> 基础 RAG 人人都会，高级 RAG 才是差异化竞争力。

### 📖 高级 RAG 技术

| 技术 | 一句话解释 | 适用场景 |
|:---|:---|:---|
| Agentic RAG | Agent 自主决定何时检索、检索什么 | 复杂问答 |
| Graph RAG | 结合知识图谱的 RAG | 实体关系密集的领域 |
| Multi-modal RAG | 支持图片、表格、代码的检索 | 技术文档、产品手册 |
| Self-RAG | 模型自己判断是否需要检索 | 减少不必要的检索 |
| Corrective RAG (CRAG) | 检索后自动验证和修正 | 高准确性要求 |
| Hybrid Search | 向量检索 + BM25 关键词检索 | 通用场景 |
| Reranking | 对检索结果二次排序 | 提升检索精度 |
| HyDE | 先生成假设答案再检索 | 开放式问题 |

### 📖 前沿方向

| 方向 | 说明 |
|:---|:---|
| MCP 协议生态 | 标准化 Agent-工具连接，正在成为行业标准 |
| A2A 协议 | Agent 间通信标准，多 Agent 系统的基础设施 |
| Agent OS | 操作系统级的 Agent 运行环境 |
| 端侧 Agent | 在手机/边缘设备上运行的 Agent |
| 长期记忆 | 跨会话、跨任务的 Agent 记忆系统 |

### 🔨 练习

1. 实现一个 Agentic RAG：Agent 根据问题复杂度自动决定是否检索
2. 搭建一个 Graph RAG pipeline：用知识图谱增强检索
3. 实现 MCP Server：为你的 Agent 添加标准化工具接口

---

## 面试准备 Checklist

> 大厂 Agent 岗位面试通常包含以下环节：

### 🏗️ 系统设计面试

- [ ] 能在白板上画出完整的 Agent 系统架构
- [ ] 能估算 Token 成本、QPS、存储需求
- [ ] 能讨论模型选型的 trade-off（成本 vs 质量 vs 延迟）
- [ ] 能设计容错和降级策略

### 🧠 技术深度面试

- [ ] 能解释 Transformer/Attention 的工作原理
- [ ] 能讨论 LoRA/DPO 等微调技术的原理和适用场景
- [ ] 能解释为什么 RAG 能减少幻觉，以及它的局限性
- [ ] 能讨论 Agent 评估的难点和你的解决方案

### 💻 编码面试

- [ ] 能现场实现一个简单的 ReAct Agent
- [ ] 能实现 RAG pipeline 的核心组件
- [ ] 能实现 Tool Calling 的路由和调度

### 🎯 行为面试

- [ ] 能讲清楚你的 Agent 项目的设计决策和 trade-off
- [ ] 能描述你遇到的最难的 Agent 调试问题
- [ ] 能讨论 Agent 安全的实际挑战

---

## 推荐技术栈（完整）

| 类别 | 工具 |
|:---|:---|
| LLM 推理 | vLLM、TGI、Ollama |
| 微调 | Hugging Face Transformers、Unsloth、Axolotl |
| Agent 框架 | LangGraph、AutoGen、CrewAI |
| RAG | LlamaIndex、LangChain |
| 向量数据库 | FAISS、Milvus、ChromaDB |
| 可观测性 | LangFuse、Arize Phoenix、LangSmith |
| 安全 | Guardrails AI、NeMo Guardrails |
| 基础设施 | Redis、Temporal、Docker、Kubernetes |
| 模型服务 | vLLM、TGI、BentoML |

---

📌 *如果你成功拿到了大厂 Agent 岗位的 offer，欢迎回来分享你的面试经验和准备心得！[提交 PR](../CONTRIBUTING.md)*
