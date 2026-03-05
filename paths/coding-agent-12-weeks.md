# 🛠️ 从零构建 Coding Agent（12 周实战路线）

> **适合谁**：有编程基础（Python）的开发者
> **时长**：12 周（每周 10-15 小时）
> **最终产出**：一个类 OpenCode / Cursor 的完整 Coding Agent 系统
> **核心理念**：用 Coding Agent 作为载体，把 Agent、系统架构、RAG、工具调用、多智能体编排全部学一遍

---

## 总目标

最终做出一个 Coding Agent 系统，具备以下能力：

```
读 repo → 理解需求 → 搜索代码 → 生成修改 → 应用 patch → 运行测试 → 自动修复 → 生成 PR
```

最终架构：

```
CLI / TUI
   ↓
Agent Runtime
   ↓
Tools (search, read, write, test)
   ↓
LLM
   ↓
Repo
```

---

## 第一阶段：第 1-2 周

### 🎯 目标：Coding Agent V0（最小可用 Agent）

> 做一个能修改 repo 文件的 agent。先不用框架，手写核心循环。

### 📖 要学的核心概念

- **Agent 核心循环**：Thought → Action → Observation（即 [ReAct](https://arxiv.org/abs/2210.03629) 范式）
- **Tool Use**：LLM 通过 Function Calling 调用外部工具
- **Prompt Engineering 基础**：System Prompt 设计、Few-shot 示例

### 🔨 要实现的功能

**工具集：**

| 工具 | 功能 |
|:---|:---|
| `list_files` | 列出目录结构 |
| `read_file` | 读取文件内容 |
| `search_code` | 搜索代码（基于 ripgrep） |
| `write_file` | 写入/修改文件 |
| `run_tests` | 执行测试命令 |

**Agent 流程：**

```
用户需求 → LLM 生成计划 → 调用工具 → 修改代码 → 运行测试 → 输出 patch
```

### ✅ 产出

实现命令：
```bash
agent fix "null pointer bug in user service"
```

输出：patch + test result + explanation

### 🧰 技术栈

Python、OpenAI / Claude API、ripgrep、subprocess

---

## 第二阶段：第 3-4 周

### 🎯 目标：Repo 理解能力

> 解决 Agent 最大问题：不知道 repo 结构，盲目修改。

### 📖 要学的核心概念

- **代码检索策略**：symbol search、text search、dependency search
- **上下文窗口管理**：如何在有限 token 内传递最相关的代码
- **代码知识图谱**：文件间的依赖与调用关系

### 🔨 要实现的功能

实现 **RepoScout** 模块：

| 工具 | 功能 |
|:---|:---|
| `search_symbol` | 搜索函数/类定义 |
| `search_text` | 全文搜索 |
| `list_related_files` | 找到相关文件（import/调用关系） |

**流程升级：**

```
问题 → RepoScout（定位相关文件） → Agent（精准修改） → 测试
```

### ✅ 产出

实现命令：
```bash
agent explain src/user/service.cs
```

输出：文件作用 + 依赖关系 + 调用链

---

## 第三阶段：第 5-6 周

### 🎯 目标：Multi-Agent Coding Agent

> 把单一 Agent 拆成多个角色，各司其职。

### 📖 要学的核心概念

- **Multi-Agent Orchestration**：多智能体协作编排
- **角色分工**：Planner / Coder / Tester / Reviewer 的职责划分
- **框架学习**：[LangGraph](https://github.com/langchain-ai/langgraph)、[AutoGen](https://github.com/microsoft/autogen)

### 🔨 要实现的功能

**Agent 角色：**

| Agent | 职责 |
|:---|:---|
| RepoScout | 分析 repo，定位相关文件 |
| Planner | 拆解任务，制定执行计划 |
| Coder | 编写和修改代码 |
| Tester | 运行测试，验证结果 |
| Reviewer | 代码审查，判断是否通过 |

**流程：**

```
用户需求 → RepoScout 找文件 → Planner 拆任务 → Coder 写代码 → Tester 跑测试 → Reviewer 审查
```

### ✅ 产出

实现命令：
```bash
agent add-feature "add caching to user service"
```

Agent 自动完成：找文件 → 生成实现 → 修改代码 → 运行测试

---

## 第四阶段：第 7-8 周

### 🎯 目标：Agent Runtime

> 从"脚本"进化为"系统"。把 Agent 做成一个可扩展的运行时。

### 📖 要学的核心概念

- **Agent Runtime 组件**：Planner、Executor、Tool Manager、Memory、Scheduler
- **状态管理**：任务状态机、Agent 循环控制
- **类比学习**：Workflow Engine（Temporal、Azure Durable Functions）

### 🔨 要实现的功能

**项目结构：**

```
agent/
├── runtime/
│   ├── planner.py
│   ├── executor.py
│   ├── memory.py
│   └── scheduler.py
├── tools/
│   ├── search.py
│   ├── file.py
│   └── test.py
└── cli.py
```

**新增能力：**

| 能力 | 说明 |
|:---|:---|
| Task State | 任务状态追踪与持久化 |
| Agent Loop | 可控的推理-行动循环 |
| Tool Routing | 根据任务动态选择工具 |

### ✅ 产出

一个结构清晰、可扩展的 Agent Runtime 系统

---

## 第五阶段：第 9-10 周

### 🎯 目标：Production Coding Agent

> 让 Agent 在真实 repo 上安全、可靠地工作。

### 📖 要学的核心概念

- **安全机制**：Sandbox、Approval Gates、权限控制
- **上下文优化**：避免 token 爆炸，只读取相关代码片段
- **错误恢复**：失败重试、回退策略

### 🔨 要实现的功能

| 能力 | 实现方式 |
|:---|:---|
| 🛡️ 安全机制 | 防止删除大量文件/执行危险命令；实现 approval gates + sandbox |
| 📦 上下文优化 | 智能代码片段提取，避免整文件塞入 prompt |
| 🔄 失败重试 | 最多 5 轮自动修复循环 |

### ✅ 产出

Agent 能安全地在真实项目上工作，失败时自动重试

---

## 第六阶段：第 11-12 周

### 🎯 目标：OpenCode 级体验

> 从工具 → 产品。打磨用户体验。

### 🔨 要实现的功能

**CLI 命令：**
```bash
agent chat       # 交互式对话
agent fix        # 修复 bug
agent explain    # 解释代码
```

**Git 集成：**
- 自动创建 branch
- 自动提交 commit
- 自动生成 PR

**TUI 界面（可选）：**
```
┌─────────────────────┬──────────────────────┐
│                     │                      │
│    💬 聊天区域       │    📝 Diff 预览       │
│                     │                      │
└─────────────────────┴──────────────────────┘
```

### ✅ 最终产出

```
TUI
 ↓
Agent Runtime (Planner → Coder → Tester → Reviewer)
 ↓
Tools (search, read, write, test, git)
 ↓
Repo
```

---

## 12 周后你将掌握

| 领域 | 具体技能 |
|:---|:---|
| **AI** | LLM API、Prompt Engineering、RAG、Tool Use、Agent 循环 |
| **系统架构** | Agent Runtime、Workflow、Task Scheduling、Tool Orchestration |
| **AI Infra** | Token 成本优化、Observability、Evaluation |
| **工程实践** | CLI/TUI 开发、Git 集成、安全机制、错误恢复 |

---

## 为什么 Coding Agent 是最佳学习入口

因为一个 Coding Agent 天然包含了 Agent 领域的所有核心技术：

- ✅ ReAct 循环
- ✅ Tool Use（文件读写、代码搜索、测试执行）
- ✅ RAG（代码检索）
- ✅ Multi-Agent（Planner / Coder / Tester / Reviewer）
- ✅ Planning（任务分解）
- ✅ Memory（对话上下文 + 代码上下文）
- ✅ System Design（Runtime 架构）

---

📌 *如果你有更好的项目建议或阶段优化，欢迎 [提交 PR](../CONTRIBUTING.md)！*
