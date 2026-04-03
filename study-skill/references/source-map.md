# 仓库交叉引用地图

> 快速查找：概念 → 对应源码/资料

## ⚠️ 路径注意事项

资料引用路径的实际位置：

| 简称 | 实际基础路径 |
|------|-------------|
| `claude-reviews-claude/XX-name.md` | 实际位于 `C:\Users\whoami\.openclaw\workspace\claude-reviews-claude\docs\chapters\XX-name.md` |
| `how-claude-code-works/docs/XX-name.md` | 实际位于 `C:\Users\whoami\.openclaw\workspace\how-claude-code-works\docs\XX-name.md` |
| `Claude-code-open-explain/XX-name/` | 实际位于 `C:\Users\whoami\.openclaw\workspace\Claude-Code-Universe\Claude-code-open-explain\XX-name\`（注意是**目录**，内含 README.md 或 index.md）|
| 其他仓库内路径 | 相对于 `C:\Users\whoami\.openclaw\workspace\Claude-Code-Universe\` |

`Claude-code-open-explain` 的 12 章是**目录**（非单文件）：
```
00-overview/  01-system-prompt/  02-agentic-loop/  03-tool-system/
04-permission-model/  05-context-management/  06-prompt-caching/
07-multi-agent/  08-mcp-integration/  09-startup-optimization/
10-feature-flags/  11-security/
```

---

## 核心子系统 → 资料映射

### 1. Agent Loop / QueryEngine

| 层次 | 资料路径 |
|------|----------|
| **理论** | `harness-books/book1-claude-code/chapter-03-*.md` (Query Loop) |
| **解读 A** | `claude-reviews-claude/docs/chapters/01-query-engine.md` (EP01) |
| **解读 B** | `how-claude-code-works/docs/02-agent-loop.md` (CH02) |
| **解读 C** | `Claude-code-open-explain/02-Agentic-Loop.md` |
| **源码 (原始)** | `claude-code-sourcemap/restored-src/src/QueryEngine.ts` |
| **源码 (原始)** | `claude-code-sourcemap/restored-src/src/query.ts` |
| **源码 (Open)** | `Claude-code-open/src/QueryEngine.ts` |
| **源码 (CCB)** | `claude-code-best/src/QueryEngine.ts` |
| **源码 (Python)** | `claude-code/src/query_engine.py` |

### 2. System Prompt / Context Assembly

| 层次 | 资料路径 |
|------|----------|
| **理论** | `harness-books/book1-claude-code/chapter-02-prompt-is-control-plane.md` |
| **解读 A** | `claude-reviews-claude/10-context-assembly.md` (EP10) |
| **解读 B** | `how-claude-code-works/docs/03-context-engineering.md` (CH03) |
| **解读 C** | `Claude-code-open-explain/01-System-Prompt.md` |
| **源码** | `src/prompts.ts` / `src/prompts/` |
| **源码** | `src/context.ts` |

### 3. Tool System

| 层次 | 资料路径 |
|------|----------|
| **解读 A** | `claude-reviews-claude/02-tool-system.md` (EP02) |
| **解读 B** | `how-claude-code-works/docs/04-tool-system.md` (CH04) |
| **解读 C** | `Claude-code-open-explain/` 对应章节 |
| **源码** | `src/Tool.ts` — 工具基类 |
| **源码** | `src/tools.ts` — 注册表 |
| **源码** | `src/tools/` — 42+ 工具实现 |
| **CCB 增强** | `src/tools/AgentTool/` — 多 Agent 工具 |

### 4. Permission / Security

| 层次 | 资料路径 |
|------|----------|
| **解读 A** | `claude-reviews-claude/07-permission-pipeline.md` (EP07) |
| **解读 B** | `how-claude-code-works/docs/10-permission-security.md` (CH10) |
| **源码** | `src/types/permissions.ts` |
| **源码** | `src/utils/permissions/` |
| **源码** | `src/components/BypassPermissionsModeDialog.tsx` |

### 5. Session Persistence / Memory

| 层次 | 资料路径 |
|------|----------|
| **解读 A** | `claude-reviews-claude/09-session-persistence.md` (EP09) |
| **解读 B** | `how-claude-code-works/docs/08-memory-system.md` (CH08) |
| **源码** | `src/assistant/sessionHistory.ts` |
| **源码** | `src/history.ts` |
| **源码** | `src/memdir/` — Memory 文件系统 |

### 6. Compact / Compression

| 层次 | 资料路径 |
|------|----------|
| **解读 A** | `claude-reviews-claude/11-compact-system.md` (EP11) |
| **解读 B** | `how-claude-code-works/docs/03-context-engineering.md` (Context 部分) |
| **源码** | 搜索: `compact`, `compress`, `summarize` 关键词 |

### 7. Hook System

| 层次 | 资料路径 |
|------|----------|
| **解读 A** | `claude-reviews-claude/05-hook-system.md` (EP05) |
| **解读 B** | `how-claude-code-works/docs/06-hooks-extensibility.md` (CH06) |
| **源码** | `src/hooks/` |

### 8. Bash Execution Engine

| 层次 | 资料路径 |
|------|----------|
| **解读** | `claude-reviews-claude/06-bash-engine.md` (EP06) |
| **源码** | `src/tools/BashTool/` |

### 9. Multi-Agent / Swarm

| 层次 | 资料路径 |
|------|----------|
| **解读 A** | `claude-reviews-claude/08-agent-swarms.md` (EP08) |
| **解读 B** | `how-claude-code-works/docs/07-multi-agent.md` (CH07) |
| **源码** | `src/tools/AgentTool/` |
| **源码** | `src/coordinator/` (部分版本) |
| **CCB 增强** | `src/Task.ts`, `src/tasks.ts` |

### 10. Plugin / MCP

| 层次 | 资料路径 |
|------|----------|
| **解读 A** | `claude-reviews-claude/04-plugin-system.md` (EP04) |
| **解读 C** | `Claude-code-open-explain/` MCP 章节 |
| **源码** | `src/services/mcp/` |
| **源码** | `src/commands/mcp/` |
| **Codex 对比** | `codex/codex-rs/core/src/` MCP 模块 |

### 11. Coordinator (claude-reviews-claude EP03)

| 层次 | 资料路径 |
|------|----------|
| **解读** | `claude-reviews-claude/03-coordinator.md` (EP03) |
| **源码** | `src/coordinator/` |

### 12. Startup / Bootstrap

| 层次 | 资料路径 |
|------|----------|
| **解读** | `claude-reviews-claude/12-startup-bootstrap.md` (EP12) |
| **源码** | `src/cli/`, `src/main.tsx`, `src/entrypoints/` |

### 13. Bridge System

| 层次 | 资料路径 |
|------|----------|
| **解读** | `claude-reviews-claude/13-bridge-system.md` (EP13) |
| **源码** | `src/bridge/` (CCB 版) |

### 14. UI / State Management

| 层次 | 资料路径 |
|------|----------|
| **解读 A** | `claude-reviews-claude/14-ui-state-management.md` (EP14) |
| **解读 B** | `how-claude-code-works/docs/11-user-experience.md` (CH11) |
| **源码** | `src/components/` |
| **源码** | `src/ink.ts` |

### 15. Services / API Layer

| 层次 | 资料路径 |
|------|----------|
| **解读** | `claude-reviews-claude/15-services-api-layer.md` (EP15) |
| **源码** | `src/services/` |

### 16. Infrastructure / Config

| 层次 | 资料路径 |
|------|----------|
| **解读** | `claude-reviews-claude/16-infrastructure-config.md` (EP16) |

### 17. Telemetry / Privacy

| 层次 | 资料路径 |
|------|----------|
| **解读** | `claude-reviews-claude/17-telemetry-privacy-operations.md` (EP17) |

### 18. Skills System

| 层次 | 资料路径 |
|------|----------|
| **解读** | `how-claude-code-works/docs/09-skills-system.md` (CH09) |
| **源码** | `src/commands/skills/` |
| **参考** | `claude-code-best/src/skills/` |

### 19. Code Editing Strategy

| 层次 | 资料路径 |
|------|----------|
| **解读** | `how-claude-code-works/docs/05-code-editing-strategy.md` (CH05) |
| **源码** | `src/tools/FileEditTool/` |

---

## 版本对照表

| 模块 | sourcemap (原始) | Open (还原) | Best (增强) | Python (移植) |
|------|-----------------|-------------|-------------|---------------|
| QueryEngine | ✅ | ✅ | ✅ + 增强 | ✅ |
| Tool System | ✅ 42+ | ✅ | ✅ + AgentTool | ✅ (简化) |
| Permissions | ✅ | ✅ | ✅ 6000+ LOC | ✅ (简化) |
| MCP | ✅ | ✅ | ✅ | ✅ |
| Session | ✅ | ✅ | ✅ + Recovery | ✅ |
| Daemon | ❌ | ❌ | ✅ | ❌ |
| SSH | ❌ | ❌ | ✅ | ❌ |
| Proactive | ❌ | ❌ | ✅ | ❌ |
| Bridge | 基础 | 基础 | ✅ 增强 | ❌ |

---

## 资料完整度检查

### claude-reviews-claude (18 章)

| EP | 标题 | 文件 |
|----|------|------|
| 00 | 架构总纲 | `00-overview.md` |
| 01 | 查询引擎 | `01-query-engine.md` |
| 02 | 工具系统 | `02-tool-system.md` |
| 03 | 协调器 | `03-coordinator.md` |
| 04 | 插件系统 | `04-plugin-system.md` |
| 05 | 钩子系统 | `05-hook-system.md` |
| 06 | Bash 引擎 | `06-bash-engine.md` |
| 07 | 权限流水线 | `07-permission-pipeline.md` |
| 08 | Swarm 智能体 | `08-agent-swarms.md` |
| 09 | 会话持久化 | `09-session-persistence.md` |
| 10 | 上下文装配 | `10-context-assembly.md` |
| 11 | 压缩系统 | `11-compact-system.md` |
| 12 | 启动引导 | `12-startup-bootstrap.md` |
| 13 | Bridge 系统 | `13-bridge-system.md` |
| 14 | UI 状态管理 | `14-ui-state-management.md` / `14-ui-state-rendering.md` |
| 15 | 服务 API 层 | `15-services-api-layer.md` |
| 16 | 基础设施配置 | `16-infrastructure-config.md` |
| 17 | 遥测隐私 | `17-telemetry-privacy-operations.md` |

### how-claude-code-works (14 章)

| CH | 标题 | 文件 |
|----|------|------|
| 01 | 系统概览 | `docs/01-overview.md` |
| 02 | Agent Loop | `docs/02-agent-loop.md` |
| 03 | Context Engineering | `docs/03-context-engineering.md` |
| 04 | Tool System | `docs/04-tool-system.md` |
| 05 | Code Editing Strategy | `docs/05-code-editing-strategy.md` |
| 06 | Hooks & Extensibility | `docs/06-hooks-extensibility.md` |
| 07 | Multi-Agent | `docs/07-multi-agent.md` |
| 08 | Memory System | `docs/08-memory-system.md` |
| 09 | Skills System | `docs/09-skills-system.md` |
| 10 | Permission & Security | `docs/10-permission-security.md` |
| 11 | User Experience | `docs/11-user-experience.md` |
| 12 | Minimal Components | `docs/12-minimal-components.md` |
| - | Quick Start | `docs/quick-start.md` |
| - | Reference | `docs/reference.md` |

### Claude-code-open-explain (12 章)

章节编号 00-11，具体标题需在使用时读取确认。
