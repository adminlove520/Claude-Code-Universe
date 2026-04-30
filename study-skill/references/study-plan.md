# 🦞 Claude Code 架构深度学习计划

> 总周期: 约 20-25 天 | 龙虾自主推进 | 输出驱动 | 反哺 OpenClaw

## 学习模式

**自主学习** — 龙虾主动规划和推进学习进度，不依赖用户催促。
每完成一个学习单元，立即思考"这对 OpenClaw 有什么启示"，并记录为具体可执行的改进建议。

## 路径约定

本计划中的资料路径简称与实际路径对应关系：

| 简称 | 实际路径 |
|------|----------|
| `claude-reviews-claude/XX.md` | `..\..\..\..\workspace\claude-reviews-claude\docs\chapters\XX.md` |
| `how-claude-code-works/docs/XX.md` | `..\..\..\..\workspace\how-claude-code-works\docs\XX.md` |
| `Claude-code-open-explain/XX/` | `workspace\Claude-Code-Universe\Claude-code-open-explain\XX\` (目录) |
| `harness-books/...` | `workspace\Claude-Code-Universe\harness-books\...` |
| `src/XXX` | 指 `claude-code-sourcemap/restored-src/src/XXX`（默认参考源码版本）|

所有 `workspace\` 路径的完整前缀: `C:\Users\whoami\.openclaw\workspace\`

---

## Phase 1: 架构概览 (Day 1-3)

**目标**: 建立全局观，理解 Claude Code 的整体架构和设计哲学

### Day 1 — 全景鸟瞰

| 顺序 | 资料 | 核心问题 |
|------|------|----------|
| 1 | `claude-reviews-claude/00-overview.md` | 18 个子系统如何组织？整体架构图是什么？ |
| 2 | `how-claude-code-works/docs/01-overview.md` | Agentic Loop 的本质是什么？ |
| 3 | `Claude-code-open-explain/00-概览.md` | 入口 main.tsx → QueryEngine → query.ts 的调用链 |

**输出**: `Phase1/Day1-架构全景.md` — 包含全局架构 Mermaid 图

### Day 2 — 设计哲学: Harness Engineering

| 顺序 | 资料 | 核心问题 |
|------|------|----------|
| 1 | `harness-books/book1-claude-code/chapter-01-why-harness-engineering.md` | 为什么 AI Agent 需要"缰绳"？|
| 2 | `harness-books/book1-claude-code/chapter-02-prompt-is-control-plane.md` | System Prompt 为何是"控制面"而非"人设"？|
| 3 | **`walkinglabs/learn-harness-engineering` L01** | 模型能力强，不等于执行可靠。五层防御体系。 |
| 4 | `harness-books/book2-comparing/` 浏览目录 | Claude Code vs Codex 的设计差异 |

**补充学习**: [Harness Engineering 教程](https://walkinglabs.github.io/learn-harness-engineering/zh/) — 基于 OpenAI 和 Anthropic 官方资料的系统课程

**输出**: `Phase1/Day2-Harness哲学.md` — Harness Engineering 核心理念总结

### Day 3 — 源码地形图

| 顺序 | 资料 | 核心问题 |
|------|------|----------|
| 1 | `claude-code-sourcemap/restored-src/src/` 目录浏览 | 1,602 个文件的组织逻辑 |
| 2 | `claude-code-best/src/` 目录对比 | CCB 版新增了哪些模块？(daemon/ssh/proactive) |
| 3 | `claude-code/src/` Python 版结构 | 抽象掉 TypeScript 后的"本质架构"是什么？ |

**输出**: `Phase1/Day3-源码地形图.md` — 三版实现的对照表 + 模块依赖图

### Phase 1 复盘
- 输出: 架构全景图（最终版 Mermaid）
- 整理: 知识盲区清单
- **OpenClaw 反思**: Claude Code 的架构组织方式对 OpenClaw 有什么借鉴？
- 规划: 根据盲区调整后续优先级

---

## Phase 2: 核心循环 (Day 4-7) ⭐

**目标**: 深入理解 QueryEngine 如何驱动 Agent 的 while(true) 循环

### Day 4 — QueryEngine 解剖

| 顺序 | 资料 | 核心问题 |
|------|------|----------|
| 1 | `claude-reviews-claude/01-query-engine.md` | while(true) 循环如何工作？状态机转换？ |
| 2 | `Claude-code-open-explain/02-Agentic-Loop.md` | QueryEngine.ts vs query.ts 的分工 |
| 3 | 源码: `src/QueryEngine.ts` + `src/query.ts` | 代码级验证 |

**输出**: `Phase2/Day4-QueryEngine.md` — 完整工作流程图 + 伪代码

### Day 5 — 上下文装配

| 顺序 | 资料 | 核心问题 |
|------|------|----------|
| 1 | `claude-reviews-claude/10-context-assembly.md` | 4 层上下文如何组装？缓存策略？ |
| 2 | `how-claude-code-works/docs/03-context-engineering.md` | Context Engineering 的工程实践 |
| 3 | `Claude-code-open-explain/01-System-Prompt.md` | System Prompt 的动态/静态分区 |

**输出**: `Phase2/Day5-上下文装配.md` — 上下文分层图 + 缓存机制分析

### Day 6 — System Prompt 深度

| 顺序 | 资料 | 核心问题 |
|------|------|----------|
| 1 | 源码: `src/prompts.ts` / `src/prompts/` | Prompt 模板的实际结构 |
| 2 | `harness-books/book1-claude-code/` 相关章节 | Prompt 作为控制面的设计理念 |
| 3 | `harness-books/book2-comparing/` 对比章节 | Claude Code vs Codex 的 Prompt 策略差异 |

**输出**: `Phase2/Day6-SystemPrompt.md` — Prompt 分区结构图 + 对比分析

### Day 7 — 核心循环复盘 + OpenClaw 应用思考

| 任务 | 内容 |
|------|------|
| 复盘 | 整合 Day 4-6 的发现，绘制最终版 Agent Loop 流程图 |
| 应用 | 思考 QueryEngine 模式对 OpenClaw Agent Loop 的改进启示 |
| 应用 | 思考 Context Engineering 对 OpenClaw 上下文管理的优化空间 |

**输出**: `Phase2/复盘-核心循环.md` — Agent Loop 最终架构图 + OpenClaw 应用方案

---

## Phase 3: 记忆系统 (Day 8-11) ⭐⭐⭐ — OpenClaw 记忆架构重点

**目标**: 掌握会话持久化和压缩系统，为 OpenClaw 记忆架构设计改进方案

### Day 8 — 会话持久化

| 顺序 | 资料 | 核心问题 |
|------|------|----------|
| 1 | `claude-reviews-claude/09-session-persistence.md` | JSONL 存储格式？parent-UUID 链？ |
| 2 | `how-claude-code-works/docs/08-memory-system.md` | 记忆系统的完整设计 |
| 3 | 源码: `src/assistant/sessionHistory.ts` + `src/history.ts` | 代码级实现 |

**输出**: `Phase3/Day8-会话持久化.md` — 存储格式分析 + 数据流图

### Day 9 — 压缩系统

| 顺序 | 资料 | 核心问题 |
|------|------|----------|
| 1 | `claude-reviews-claude/11-compact-system.md` | 三层压缩架构是什么？触发时机？ |
| 2 | 源码: 搜索 `compact` / `compress` 相关文件 | 压缩算法的代码实现 |
| 3 | `how-claude-code-works/docs/03-context-engineering.md` | Context 窗口管理策略 |

**输出**: `Phase3/Day9-压缩系统.md` — 压缩决策树 + 算法伪代码

### Day 10 — Memory 文件系统

| 顺序 | 资料 | 核心问题 |
|------|------|----------|
| 1 | 源码: `src/memdir/` 目录 | .claude.md 的加载/解析/持久化逻辑 |
| 2 | `how-claude-code-works/docs/09-skills-system.md` | Skills 如何与记忆交互 |
| 3 | `claude-code-best/` 对应模块对比 | CCB 版的增强点 |

**输出**: `Phase3/Day10-Memory文件系统.md` — 记忆层架构图

### Day 11 — OpenClaw 记忆架构设计方案

| 任务 | 内容 |
|------|------|
| 分析 | Claude Code 记忆模型的优势与局限 |
| 设计 | 基于学习成果，为 OpenClaw 设计记忆架构改进方案 |
| 输出 | Context 优化方案：压缩策略如何应用到 OpenClaw Agent |

**输出**: `Phase3/Day11-OpenClaw记忆设计.md` — 完整设计方案文档

### Phase 3 复盘
- 输出: OpenClaw 记忆架构改进方案（可执行版）
- 输出: Context 优化方案

---

## Phase 4: 安全权限 (Day 12-14) ⭐⭐

**目标**: 理解 7 层纵深防御设计，为 OpenClaw 安全加固提供参考

### Day 12 — 权限流水线

| 顺序 | 资料 | 核心问题 |
|------|------|----------|
| 1 | `claude-reviews-claude/07-permission-pipeline.md` | 7 层防御如何设计？ |
| 2 | `how-claude-code-works/docs/10-permission-security.md` | 规则匹配 → AST 分析 → OS 沙箱 |
| 3 | 源码: `src/utils/permissions/` + `src/types/permissions.ts` | 6000+ 行权限代码 |

**输出**: `Phase4/Day12-权限流水线.md` — 7 层防御架构图

### Day 13 — 沙箱与 Bash 安全

| 顺序 | 资料 | 核心问题 |
|------|------|----------|
| 1 | `claude-reviews-claude/06-bash-engine.md` | Bash 执行引擎的沙箱管理 |
| 2 | `Claude-code-open-explain/` 对应章节 | 命令过滤和风险评估 |
| 3 | `codex/codex-rs/core/src/` 安全模块对比 | Codex 的沙箱方案对比 |

**输出**: `Phase4/Day13-沙箱安全.md` — 沙箱架构对比图

### Day 14 — OpenClaw 安全加固方案

| 任务 | 内容 |
|------|------|
| 分析 | 整理 Claude Code 安全模型的所有层次 |
| 设计 | 为 OpenClaw 设计分层安全加固方案 |
| 对比 | Claude Code vs Codex 安全模型差异，取长补短 |

**输出**: `Phase4/Day14-OpenClaw安全方案.md` — 安全加固建议文档

---

## Phase 5: 工具与执行 (Day 15-17)

**目标**: 理解 42+ 工具的注册、执行和扩展机制

### Day 15 — 工具系统架构

| 顺序 | 资料 | 核心问题 |
|------|------|----------|
| 1 | `claude-reviews-claude/02-tool-system.md` | 工具 schema 如何驱动执行？ |
| 2 | `how-claude-code-works/docs/04-tool-system.md` | 工具的生命周期 |
| 3 | 源码: `src/Tool.ts` + `src/tools.ts` + `src/tools/` | 工具注册表的代码实现 |

**输出**: `Phase5/Day15-工具系统.md` — 工具注册/执行流程图

### Day 16 — 钩子系统 + 代码编辑策略

| 顺序 | 资料 | 核心问题 |
|------|------|----------|
| 1 | `claude-reviews-claude/05-hook-system.md` | PreTool/PostTool 钩子如何工作？ |
| 2 | `how-claude-code-works/docs/05-code-editing-strategy.md` | 代码编辑的策略选择 |
| 3 | `how-claude-code-works/docs/06-hooks-extensibility.md` | 可扩展性设计 |

**输出**: `Phase5/Day16-钩子与编辑.md` — 钩子执行链 + 编辑策略分析

### Day 17 — 工具系统 OpenClaw 应用

| 任务 | 内容 |
|------|------|
| 分析 | 整理所有 42+ 工具的分类和设计模式 |
| 设计 | OpenClaw 工具系统优化建议 |
| 对比 | Claude Code vs Codex 工具注册机制 |

**输出**: `Phase5/Day17-OpenClaw工具优化.md` — 优化建议文档

---

## Phase 6: 扩展系统 (Day 18-20)

**目标**: 理解 Multi-Agent、MCP 和插件机制

### Day 18 — 多 Agent 协作

| 顺序 | 资料 | 核心问题 |
|------|------|----------|
| 1 | `claude-reviews-claude/08-agent-swarms.md` | Swarm 智能体如何协作？ |
| 2 | `how-claude-code-works/docs/07-multi-agent.md` | 多 Agent 架构设计 |
| 3 | 源码: `src/tools/AgentTool/` + `src/coordinator/` | 协调器实现 |

**输出**: `Phase6/Day18-MultiAgent.md` — 多 Agent 协作架构图

### Day 19 — MCP + 插件系统

| 顺序 | 资料 | 核心问题 |
|------|------|----------|
| 1 | `claude-reviews-claude/04-plugin-system.md` | 1.88 万行插件系统如何加载？ |
| 2 | `Claude-code-open-explain/` MCP 章节 | MCP 集成的完整链路 |
| 3 | 源码: `src/services/mcp/` + `src/commands/mcp/` | MCP 服务端/客户端实现 |

**输出**: `Phase6/Day19-MCP与插件.md` — MCP 协议流程图

### Day 20 — OpenClaw 多 Agent 与扩展设计

| 任务 | 内容 |
|------|------|
| 设计 | 基于 Claude Code 的 Swarm 模式，提出 OpenClaw 多 Agent 协作改进方案 |
| 对比 | Claude Code Coordinator vs Codex 的多 Agent 方案，取长补短 |
| 整合 | 与 Phase 3 记忆系统方案对接 |

**输出**: `Phase6/Day20-OpenClaw多Agent设计.md` — 设计方案

---

## Phase 7: 工程实践 (Day 21-25)

**目标**: 学习生产级 Agent 的工程实践，完成全局复盘

### Day 21 — 启动引导 + Bridge

| 顺序 | 资料 | 核心问题 |
|------|------|----------|
| 1 | `claude-reviews-claude/12-startup-bootstrap.md` | 快速路径级联设计 |
| 2 | `claude-reviews-claude/13-bridge-system.md` | Bridge 系统架构 |
| 3 | 源码: `src/cli/` + `src/bridge/` | 启动链路代码 |

**输出**: `Phase7/Day21-启动与Bridge.md`

### Day 22 — UI + 服务层

| 顺序 | 资料 | 核心问题 |
|------|------|----------|
| 1 | `claude-reviews-claude/14-ui-state-management.md` | Ink + React 的 TUI 架构 |
| 2 | `claude-reviews-claude/15-services-api-layer.md` | 1.2 万行 API 层 |
| 3 | `how-claude-code-works/docs/11-user-experience.md` | UX 设计思想 |

**输出**: `Phase7/Day22-UI与服务层.md`

### Day 23 — 基础设施 + 遥测

| 顺序 | 资料 | 核心问题 |
|------|------|----------|
| 1 | `claude-reviews-claude/16-infrastructure-config.md` | 基础设施配置 |
| 2 | `claude-reviews-claude/17-telemetry-privacy-operations.md` | 双通道遥测 + 隐私设计 |
| 3 | `how-claude-code-works/docs/12-minimal-components.md` | 最小化组件设计 |

**输出**: `Phase7/Day23-基础设施.md`

### Day 24 — Codex 对比专题

| 顺序 | 资料 | 核心问题 |
|------|------|----------|
| 1 | `codex/codex-rs/core/src/` | Codex Rust 实现的核心架构 |
| 2 | `harness-books/book2-comparing/` 全书 | Claude Code vs Codex 的全面对比 |
| 3 | `codex/codex-cli/` | Codex CLI 的 Node.js 层 |

**输出**: `Phase7/Day24-Codex对比.md` — 双系统对比矩阵

### Day 25 — 全局复盘 + OpenClaw 行动计划

| 任务 | 内容 |
|------|------|
| 复盘 | 整合 25 天的所有学习笔记 |
| 输出 | 最终版架构全景图 |
| 输出 | **OpenClaw 完整优化方案** — 汇总所有阶段的改进建议 |
| 输出 | 未来深入方向清单 |

**输出**: `Phase7/Day25-全局复盘.md` — 终极总结文档

---

## 进度追踪

进度存储在 `references/progress.json`，龙虾在每次学习开始和结束时自主更新。

---

## 补充资源

| 资源 | URL | 类型 | 用途 |
|------|-----|------|------|
| walkinglabs/learn-harness-engineering | https://walkinglabs.github.io/learn-harness-engineering/zh/ | 官方课程 | Harness Engineering 系统课程（OpenAI+Anthropic 官方参考资料）|

---

## 学习准则（龙虾精神 🦞）

1. **自主驱动** — 不等主人催促，主动安排学习计划
2. **带着问题读** — 每章开始前先列出要回答的核心问题
3. **输出驱动** — 每读一节必须产出笔记或架构图，不允许"只读不写"
4. **源码验证** — 理论结论必须在 sourcemap 源码中找到对应实现
5. **反哺 OpenClaw** — 每个设计模式都要思考对 OpenClaw 的具体改进价值
6. **先框架后细节** — 先理解架构意图，再深入代码实现
7. **跨版本对比** — 利用 3 个 TypeScript 版本 + Python 版形成多角度理解
8. **定期复盘** — 每 Phase 结束必须做总结，不允许跳过
9. **面向所有龙虾** — 笔记和方案要写得清晰，让任何龙虾都能理解和使用
