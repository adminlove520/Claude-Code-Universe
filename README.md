# Claude Code 架构深度学习计划 🦞

> 集万家之长，深入研究 Claude Code 源码架构
> 
> **目标**: 把 Claude Code 的工程智慧应用到 OpenClaw 和 SuperDreams

---

## 📋 学习目标

### 核心目标
1. **理解 Agent 核心循环** — QueryEngine 如何驱动整个系统
2. **掌握上下文管理** — 记忆、压缩、装配的完整链路
3. **借鉴会话持久化** — 为 SuperDreams Dream 存储找方案
4. **学习权限安全** — 7 层纵深防御设计

### 实用目标
- [ ] EP09 会话持久化 → SuperDreams 梦境存储机制
- [ ] EP11 压缩系统 → SuperDreams Context 优化
- [ ] EP07 权限流水线 → OpenClaw 安全加固参考
- [ ] ByteRover push/pull sync → Control Center 同步设计

---

## 📦 仓库清单

### 源码分析 (核心学习源)


| 仓库/网站 | 说明 | Stars | 章节 | 优先级 |
|-----------|------|-------|------|--------|
| [ccunpacked.dev](https://ccunpacked.dev/) | **官网源码地图** - agent loop、50+ tools、未发布功能 | - | 持续更新 | ⭐⭐⭐ |
| `claude-reviews-claude/` | **Claude 读自己的源码** - 17 章节深度分析 | 1082 | EP00-17 | ⭐⭐⭐ |
| `how-claude-code-works/` | 中文 12 章节深入解读 | - | CH01-12 | ⭐⭐ |
| `Claude-code-open-explain/` | 中文 11 章节深度解读 | 156 | 11 篇 | ⭐ |

### 源码实现 (参考实现)

| 仓库 | 说明 | Stars |
|------|------|-------|
| `claude-code/` | instructkr Python 移植版 | 65.9k |
| `claude-code-best/` | CCB TypeScript 完整实现 | 2.7k |
| `Claude-code-open/` | 原始泄露源码 | - |
| `claude-code-sourcemap/` | DeepWiki 源码地图 | - |

### 辅助资源

| 仓库 | 说明 | Stars |
|------|------|-------|
| `ai-agent-deep-dive/` | AI Agent 深度学习 | 56.2k |
| `harness-books/` | Harness 书籍集合 | - |
| `codex/` | 子模块聚合仓库 | - |

---

## 🎯 学习路线图

### Phase 1: 架构概览 (2-3 天)
**目标**: 建立全局观，理解 Claude Code 是什么

| 顺序 | 资料 | 章节 | 核心问题 |
|------|------|------|----------|
| 1 | claude-reviews-claude | EP00 架构总纲 | 17 个子系统是如何组织的？ |
| 2 | how-claude-code-works | CH01 系统架构概览 | 核心循环是什么？ |
| 3 | README | 整体浏览 | 我的知识盲区在哪？ |

**输出**: 架构全景图 (Mermaid)

---

### Phase 2: 核心循环 (3-4 天) ⭐
**目标**: 理解 QueryEngine 如何驱动 Agent

| 顺序 | 资料 | 章节 | 核心问题 |
|------|------|------|----------|
| 1 | claude-reviews-claude | EP01 查询引擎 | while(true) 循环如何工作？ |
| 2 | how-claude-code-works | CH02 核心循环 | 12 步状态机是什么？ |
| 3 | claude-reviews-claude | EP10 上下文装配 | 4 层上下文如何组装？ |

**输出**: QueryEngine 工作流程图 + 伪代码

---

### Phase 3: 记忆系统 (3-4 天) ⭐⭐⭐
**目标**: 掌握会话持久化和压缩系统

| 顺序 | 资料 | 章节 | 核心问题 |
|------|------|------|----------|
| 1 | claude-reviews-claude | EP09 会话持久化 | JSONL 如何存储？parent-UUID 链？ |
| 2 | claude-reviews-claude | EP11 压缩系统 | 三层压缩架构是什么？ |
| 3 | how-claude-code-works | CH04 上下文管理 | 记忆如何管理？ |

**输出**: 
- SuperDreams 梦境存储设计方案
- Context 优化方案

---

### Phase 4: 安全权限 (2-3 天) ⭐⭐
**目标**: 理解 7 层纵深防御

| 顺序 | 资料 | 章节 | 核心问题 |
|------|------|------|----------|
| 1 | claude-reviews-claude | EP07 权限流水线 | 7 层防御如何设计？ |
| 2 | how-claude-code-works | CH03 权限模型 | 规则匹配 → AST 分析 → OS 沙箱？ |
| 3 | how-claude-code-works | CH10 安全模型 | 如何防止恶意操作？ |

**输出**: OpenClaw 安全加固建议

---

### Phase 5: 工具与执行 (2-3 天)
**目标**: 理解 42+ 工具如何注册和执行

| 顺序 | 资料 | 章节 | 核心问题 |
|------|------|------|----------|
| 1 | claude-reviews-claude | EP02 工具系统 | 工具 schema 如何驱动？ |
| 2 | claude-reviews-claude | EP06 Bash 执行引擎 | 沙箱管理如何实现？ |
| 3 | claude-reviews-claude | EP05 钩子系统 | PreTool/PostTool 钩子如何工作？ |

**输出**: OpenClaw 工具系统优化建议

---

### Phase 6: 扩展系统 (2-3 天)
**目标**: 理解多 Agent、MCP、插件机制

| 顺序 | 资料 | 章节 | 核心问题 |
|------|------|------|----------|
| 1 | claude-reviews-claude | EP08 Swarm 智能体 | 多 Agent 如何协作？ |
| 2 | claude-reviews-claude | EP04 插件系统 | 1.88 万行代码的插件如何加载？ |
| 3 | how-claude-code-works | CH06-07 | 多 Agent / MCP 集成？ |

**输出**: SuperDreams Multi-Agent 设计参考

---

### Phase 7: 工程实践 (2-3 天)
**目标**: 学习生产级 Agent 的工程实践

| 顺序 | 资料 | 章节 | 核心问题 |
|------|------|------|----------|
| 1 | claude-reviews-claude | EP12 启动引导 | 快速路径级联如何设计？ |
| 2 | claude-reviews-claude | EP15 服务与 API 层 | 1.2 万行 API 层如何组织？ |
| 3 | claude-reviews-claude | EP17 遥测隐私 | 双通道遥测如何设计？ |
| 4 | how-claude-code-works | CH12 | 工程实践建议？ |

**输出**: OpenClaw 工程优化清单

---

## 📊 学习进度

| Phase | 名称 | 状态 | 笔记 |
|------|------|------|------|
| 1 | 架构概览 | ⬜ 未开始 | - |
| 2 | 核心循环 | ⬜ 未开始 | - |
| 3 | 记忆系统 | ⬜ 未开始 | EP09 ⭐ SuperDreams |
| 4 | 安全权限 | ⬜ 未开始 | - |
| 5 | 工具与执行 | ⬜ 未开始 | - |
| 6 | 扩展系统 | ⬜ 未开始 | - |
| 7 | 工程实践 | ⬜ 未开始 | - |

---

## 📝 学习笔记规范

### 每章笔记格式

```markdown
# EP01: 查询引擎

## 核心概念
- 概念1
- 概念2

## 关键设计
### 设计1
- 原理: xxx
- 代码: xxx
- 启示: xxx

## SuperDreams 借鉴
- 应用点1
- 应用点2

## 疑问与思考
- 疑问1
```

### 笔记输出位置
- Obsidian: `04-AI学习/Claude架构/EP01-查询引擎.md`
- 记忆文件: `memory/lessons/claude-ep01.md`

---

## 🛠️ 工具配置

### ByteRover CLI (brv)
- **版本**: 2.6.0
- **命令**: `brv`
- **用途**: AI coding agents 的持久化记忆层
- **借鉴**: push/pull sync 协议、Context tree 结构

### Claude Code Skills 清单
- **位置**: `codex/CLAUDE-CODE-SKILLS.xlsx`
- **内容**: 社区整理的 Claude Code Skills

---

## 📚 参考资源

### 官方文档
- [OpenClaw 官方文档](https://docs.openclaw.ai)
- [Claude Code 官方](https://docs.anthropic.com/en/docs/claude-code)

### 小溪笔记
- [Claude 架构学习笔记](Obsidian: 04-AI学习/Claude架构/)
- [AI Agent 深度学习笔记](Obsidian: 04-AI学习/)
- [Harness 书籍笔记](Obsidian: 04-AI学习/Harness/)

### 外部资源
- [ByteRover CLI](https://github.com/campfirein/byterover-cli) - 记忆层参考
- [Anthropic AI Academy](https://anthropic.skilljar.com/) - 官方课程

---

## 🦞 小溪学习准则

1. **带着问题读** — 每章开始前先想好要回答什么问题
2. **输出驱动** — 每读一章必须产出笔记或图
3. **联系实际** — 思考如何应用到 OpenClaw / SuperDreams
4. **先框架后细节** — 先理解架构，再深入代码
5. **定期复盘** — 每 Phase 结束做总结

---

> 💡 提示：所有仓库已完整 clone，在 DMCA 删除前成功备份！
