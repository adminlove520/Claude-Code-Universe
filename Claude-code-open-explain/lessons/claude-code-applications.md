# Claude Code 应用到 OpenClaw 的想法

## 待实现

### 高优先级

#### 1. Harness 设计模式
**来源**: claw-code/src/
**想法**: Agent 和工具的连接方式
**应用**: OpenClaw 的 skill 调用可以借鉴 harness 模式，更清晰

#### 2. 权限校验模型
**来源**: 04-permission-model
**想法**: 工具执行前做权限校验
**应用**: 小溪执行敏感操作前的确认机制

#### 3. 上下文压缩策略
**来源**: 05-context-management
**想法**: 对话太长时的压缩和续跑
**应用**: 改进 OpenClaw 的 compaction 策略

---

## 已实现

(暂无)

---

## 废弃/不可行

(记录不合适的想法)
