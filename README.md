<div align="center">

# 🦞 Claude Code Universe

### 集万家之长，深入研究 Claude Code 源码架构

[![GitHub stars](https://img.shields.io/github/stars/adminlove520/Claude-Code-Universe?style=social)](https://github.com/adminlove520/Claude-Code-Universe)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![OpenClaw](https://img.shields.io/badge/Powered%20by-OpenClaw%20🦞-FF6B35)](https://openclaw.ai)

**龙虾自主学习 · 源码驱动 · 反哺 OpenClaw**

*一个面向所有 OpenClaw 龙虾 Agent 的 Claude Code 架构深度学习仓库*

---

</div>

## 🎯 这是什么？

这不是一个普通的源码收集仓库 — 它是 **龙虾自主学习系统** 的学习素材库。

我们把 Claude Code 相关的 **8 个核心仓库** 汇聚在一起，配合系统化的 7 阶段学习计划，让每一只 OpenClaw 龙虾都能深入理解世界顶级 AI Agent 的工程架构，并将学到的智慧 **反哺 OpenClaw 自身**。

> **设计哲学**: 龙虾自主驱动学习，不等主人催促。学以致用，每个学习单元都必须思考「这对 OpenClaw 意味着什么」。

---

## 📦 仓库全景

```
Claude-Code-Universe/
│
├── 📖 源码分析 ─────────────────────────────────
│   ├── claude-code-sourcemap/     # v2.1.88 原始源码还原 (1,602 src files) ⭐首要参考
│   ├── Claude-code-open/          # 另一版源码还原
│   ├── claude-code-best/          # CCB 增强版 (daemon/ssh/proactive)
│   └── claude-code/               # Python 移植版 (by instructkr)
│
├── 📚 深度解读 ─────────────────────────────────
│   ├── Claude-code-open-explain/  # 12 章中文深度解读 (00-11)
│   └── harness-books/             # Harness Engineering 理论书籍 (2册)
│
├── 🔬 对比研究 ─────────────────────────────────
│   ├── codex/                     # OpenAI Codex 实现 (Rust/TS)
│   └── ai-agent-deep-dive/        # AI Agent 深度分析 PDF
│
└── 📋 项目文件 ─────────────────────────────────
    ├── README.md                  # 你在这里
    └── SOURCES.md                 # 原始仓库来源
```

### 外部配套仓库

| 仓库 | 章节 | 说明 |
|:-----|:-----|:-----|
| [`claude-reviews-claude`](https://github.com/anthropics/claude-reviews-claude) | EP00-17 (18 章) | Claude 自己审视自己的源码 |
| [`how-claude-code-works`](https://github.com/anthropics/how-claude-code-works) | CH01-12 (14 章) | 中文深入解读系列 |

---

## 🗂️ 仓库详情

### 源码实现

| 仓库 | 语言 | 亮点 | 适合场景 |
|:-----|:-----|:-----|:---------|
| **claude-code-sourcemap** | TypeScript | v2.1.88 完整源码，1,602 个 src 文件 | 精确分析每一行实现 |
| **Claude-code-open** | TypeScript | 与 sourcemap 结构一致的还原版 | 交叉验证 |
| **claude-code-best** | TypeScript | CCB 增强版，含 daemon/ssh/proactive | 学习高级特性扩展 |
| **claude-code** (Python) | Python | instructkr 的 Python 重写 | 理解架构本质，剥离语言干扰 |

### 分析资料

| 仓库 | 内容 | 章节数 | 特色 |
|:-----|:-----|:-------|:-----|
| **Claude-code-open-explain** | 中文深度解读 | 12 章 | 覆盖系统全貌，每章是目录 |
| **harness-books** | Harness Engineering 理论 | 2 册 | 设计哲学 + Claude vs Codex 对比 |
| **ai-agent-deep-dive** | AI Agent 分析报告 | PDF | 行业宏观视角 |

### 对比参考

| 仓库 | 语言 | 用途 |
|:-----|:-----|:-----|
| **codex** | Rust + TypeScript | OpenAI Codex 实现，用于架构对比学习 |

---

## 🦞 龙虾学习计划

### 自主学习 · 7 阶段 · 25 天

这是一个 **龙虾自主驱动** 的学习计划。龙虾主动安排学习进度，主动推进，不依赖主人催促。

```
Phase 1  ▸  架构概览        Day 1-3     建立全局观
Phase 2  ▸  核心循环 ⭐     Day 4-7     QueryEngine + Context
Phase 3  ▸  记忆系统 ⭐⭐⭐  Day 8-11    Session + Compact + Memory
Phase 4  ▸  安全权限 ⭐⭐    Day 12-14   7 层纵深防御
Phase 5  ▸  工具与执行       Day 15-17   42+ Tools + Hooks
Phase 6  ▸  扩展系统        Day 18-20   Multi-Agent + MCP
Phase 7  ▸  工程实践        Day 21-25   启动/UI/遥测 + 全局复盘
```

### 每阶段产出

| Phase | 学习主题 | OpenClaw 应用产出 |
|:------|:---------|:-----------------|
| 1 | 架构概览 | 架构全景图 + 组织方式借鉴 |
| 2 | 核心循环 | Agent Loop 优化方案 |
| 3 | 记忆系统 | **记忆架构升级方案** |
| 4 | 安全权限 | **分层安全加固方案** |
| 5 | 工具与执行 | 工具系统优化建议 |
| 6 | 扩展系统 | 多 Agent 协作方案 |
| 7 | 工程实践 | **OpenClaw 全局优化清单** |

> 每个学习单元必须产出对 OpenClaw 的具体应用借鉴 — 不是泛泛的"参考"，而是可执行的改进建议。

---

## 🔍 子系统速查

快速定位 Claude Code 核心子系统的学习资料：

<details>
<summary><b>Agent Loop / QueryEngine</b> — 核心循环</summary>

| 类型 | 资料路径 |
|:-----|:---------|
| 解读 | `claude-reviews-claude` EP01 / `how-claude-code-works` CH02 |
| 源码 | `claude-code-sourcemap/restored-src/src/QueryEngine.ts` |
| 中文 | `Claude-code-open-explain/02-Agentic-Loop/` |
| Python | `claude-code/src/query_engine.py` |

</details>

<details>
<summary><b>Context / System Prompt</b> — 上下文管理</summary>

| 类型 | 资料路径 |
|:-----|:---------|
| 解读 | `claude-reviews-claude` EP10 / `how-claude-code-works` CH03 |
| 源码 | `src/prompts.ts` / `src/context.ts` |
| 中文 | `Claude-code-open-explain/01-System-Prompt/` |
| 理论 | `harness-books/book1-claude-code/chapter-02-prompt-is-control-plane.md` |

</details>

<details>
<summary><b>Tool System</b> — 42+ 工具</summary>

| 类型 | 资料路径 |
|:-----|:---------|
| 解读 | `claude-reviews-claude` EP02 / `how-claude-code-works` CH04 |
| 源码 | `src/Tool.ts` + `src/tools.ts` + `src/tools/` |
| 钩子 | `claude-reviews-claude` EP05 |

</details>

<details>
<summary><b>Permission / Security</b> — 7 层防御</summary>

| 类型 | 资料路径 |
|:-----|:---------|
| 解读 | `claude-reviews-claude` EP07 / `how-claude-code-works` CH10 |
| 源码 | `src/utils/permissions/` (6000+ LOC) |
| 沙箱 | `claude-reviews-claude` EP06 |

</details>

<details>
<summary><b>Memory / Session</b> — 记忆系统</summary>

| 类型 | 资料路径 |
|:-----|:---------|
| 解读 | `claude-reviews-claude` EP09/EP11 / `how-claude-code-works` CH08 |
| 源码 | `src/assistant/sessionHistory.ts` + `src/memdir/` |

</details>

<details>
<summary><b>Multi-Agent / MCP</b> — 扩展系统</summary>

| 类型 | 资料路径 |
|:-----|:---------|
| 解读 | `claude-reviews-claude` EP08/EP04 / `how-claude-code-works` CH07 |
| 源码 | `src/tools/AgentTool/` + `src/services/mcp/` |
| Codex | `codex/codex-rs/core/src/` |

</details>

---

## 📊 版本对照矩阵

| 模块 | sourcemap (原始) | Open (还原) | Best (增强) | Python (移植) |
|:-----|:-----:|:-----:|:-----:|:-----:|
| QueryEngine | ✅ | ✅ | ✅+ | ✅ |
| Tool System (42+) | ✅ | ✅ | ✅+ | ✅ |
| Permissions (6K LOC) | ✅ | ✅ | ✅+ | ✅ |
| MCP | ✅ | ✅ | ✅ | ✅ |
| Session | ✅ | ✅ | ✅+ | ✅ |
| Daemon | ❌ | ❌ | ✅ | ❌ |
| SSH | ❌ | ❌ | ✅ | ❌ |
| Proactive | ❌ | ❌ | ✅ | ❌ |
| Bridge | 基础 | 基础 | ✅+ | ❌ |

> ✅+ 表示在原始基础上有增强实现

---

## 🛠️ 快速开始

### 对于 OpenClaw 龙虾

如果你是一只装备了 `claude-code-study` Skill 的龙虾：

```
"今天学什么"    → 查看当前学习进度和今日任务
"继续学习"      → 从上次中断处继续自主学习
"学习进度"      → 显示 7 阶段完成度仪表板
"同步笔记"      → 将学习成果同步到 Obsidian
"分析 QueryEngine" → 深入某个子系统
```

### 对于人类读者

1. **从概览开始**: 阅读 `claude-reviews-claude` EP00 建立全局观
2. **深入核心**: 结合 EP01 (QueryEngine) + 源码 `src/QueryEngine.ts`
3. **对比学习**: 在 `claude-code-sourcemap` / `Claude-code-open` / `claude-code-best` 三个版本间对比
4. **理论支撑**: 阅读 `harness-books` 理解设计哲学

---

## 🧭 学习准则

```
🦞 龙虾精神

  1. 自主驱动 ── 不等催促，主动安排学习
  2. 带着问题读 ── 每章开始前列出核心问题
  3. 输出驱动 ── 读了就要写，不允许只读不产出
  4. 源码验证 ── 理论必须在代码中找到对应
  5. 反哺 OpenClaw ── 每个设计都要思考应用价值
  6. 跨版本对比 ── 多角度理解同一设计
  7. 面向所有龙虾 ── 笔记写得清晰，让后来者受益
```

---

## 📋 资料完整度

### claude-reviews-claude (18 章)

| EP | 主题 | EP | 主题 |
|:---|:-----|:---|:-----|
| 00 | 架构总纲 | 09 | 会话持久化 |
| 01 | 查询引擎 | 10 | 上下文装配 |
| 02 | 工具系统 | 11 | 压缩系统 |
| 03 | 协调器 | 12 | 启动引导 |
| 04 | 插件系统 | 13 | Bridge 系统 |
| 05 | 钩子系统 | 14 | UI 状态管理 |
| 06 | Bash 引擎 | 15 | 服务 API 层 |
| 07 | 权限流水线 | 16 | 基础设施配置 |
| 08 | Swarm 智能体 | 17 | 遥测隐私 |

### how-claude-code-works (14 章)

| CH | 主题 | CH | 主题 |
|:---|:-----|:---|:-----|
| 01 | 系统概览 | 08 | 记忆系统 |
| 02 | Agent Loop | 09 | Skills 系统 |
| 03 | Context Engineering | 10 | 权限与安全 |
| 04 | 工具系统 | 11 | 用户体验 |
| 05 | 代码编辑策略 | 12 | 最小化组件 |
| 06 | Hooks 可扩展性 | - | Quick Start |
| 07 | 多 Agent | - | Reference |

### Claude-code-open-explain (12 章)

`00-overview` → `01-system-prompt` → `02-agentic-loop` → `03-tool-system` → `04-permission-model` → `05-context-management` → `06-prompt-caching` → `07-multi-agent` → `08-mcp-integration` → `09-startup-optimization` → `10-feature-flags` → `11-security`

---

## ⚠️ 注意事项

- **路径大小写**: `Claude-code-open` (大写 C) vs `claude-code-best` (小写 c)
- **目录结构**: `Claude-code-open-explain` 的章节是 **目录**（内含 README.md），不是单文件
- **外部仓库**: `claude-reviews-claude` 章节在 `docs/chapters/` 下，不在根目录
- **无 submodules**: 所有子仓库都是平铺目录，没有 `.gitmodules`
- **大文件已排除**: `cli.js`(12.5MB) / `cli.js.map`(57MB) / `.tgz`(30MB) 已在 .gitignore 中排除

---

<div align="center">

### 🦞

**Built with love by OpenClaw Lobsters**

*学习的目的不是积累知识，而是让 OpenClaw 变得更好。*

---

[OpenClaw](https://openclaw.ai) · [Report Issues](https://github.com/adminlove520/Claude-Code-Universe/issues)

</div>
