<div align="center">

# Claude Code

**Anthropic 官方 AI 编程助手 CLI 工具源代码**

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.x-blue?logo=typescript)](https://www.typescriptlang.org/)
[![Bun](https://img.shields.io/badge/Bun-Runtime-black?logo=bun)](https://bun.sh/)
[![React](https://img.shields.io/badge/React-Ink-61DAFB?logo=react)](https://github.com/vadimdemedes/ink)
[![Platform](https://img.shields.io/badge/Platform-macOS%20%7C%20Linux%20%7C%20Windows-lightgrey)](#)

[English](#english) | [中文](#中文)

</div>

---

## 中文

Claude Code 是 Anthropic 官方出品的 AI 编程助手命令行工具（CLI）的完整源代码。它将强大的 Claude 大语言模型直接集成到你的终端工作流中，提供代码编写、文件操作、Shell 命令执行、网络搜索等一系列 AI 增强能力，是目前最完整、功能最丰富的 AI 编程 CLI 工具之一。

---

## 目录

- [项目特性](#项目特性)
- [技术架构](#技术架构)
- [支持的模型](#支持的模型)
- [API 提供商](#api-提供商)
- [内置工具](#内置工具)
- [斜杠命令](#斜杠命令)
- [项目结构](#项目结构)
- [快速开始](#快速开始)
- [配置说明](#配置说明)
- [权限系统](#权限系统)
- [MCP 支持](#mcp-支持)
- [多智能体系统](#多智能体系统)
- [IDE 集成](#ide-集成)
- [语音模式](#语音模式)
- [远程会话](#远程会话)
- [贡献指南](#贡献指南)
- [许可证](#许可证)

---

## 项目特性

### 🤖 核心 AI 能力
- **多模型支持**：支持 Claude 4.5全系列模型（Haiku / Sonnet / Opus）
- **扩展思考**：支持模型级别的深度推理（Extended Thinking）
- **上下文感知**：自动读取 `CLAUDE.md` 项目配置文件，理解项目上下文
- **对话压缩**：智能压缩长对话历史，保持 token 效率

### 🛠️ 强大工具集
- **文件系统操作**：读取、写入、编辑文件，支持 Glob 匹配和 Grep 搜索
- **Shell 执行**：安全执行 Bash/PowerShell 命令，内置安全防护
- **Web 能力**：网络搜索与 URL 内容抓取
- **代码智能**：LSP（语言服务协议）集成，Jupyter Notebook 支持
- **任务管理**：内置 Todo / Task 管理工具

### 🏗️ 高级架构特性
- **多智能体 Swarm**：支持通过 Tmux / iTerm2 后端编排多个 AI 智能体协同工作
- **MCP 协议**：完整的 Model Context Protocol 客户端支持
- **插件系统**：可扩展的插件和 Skills 体系
- **远程会话**：通过 WebSocket/SSE 支持远程 Claude Code 会话

### 💻 优秀的终端 UI
- 基于 React + [Ink](https://github.com/vadimdemedes/ink) 构建的丰富终端界面
- 支持语法高亮、结构化 Diff 显示、Markdown 渲染
- 完整的 Vim 按键绑定支持
- 多主题系统

### 🔐 安全与合规
- 细粒度权限管理系统
- 沙箱模式（Sandbox Mode）
- MDM（移动设备管理）策略支持
- 支持企业级 SSO/OAuth 认证

---

## 技术架构

```
Claude Code
├── 运行时:     Bun (JavaScript/TypeScript 运行时 + 打包器)
├── UI 框架:    React + Ink (终端 UI)
├── 语言:       TypeScript 5.x
├── AI SDK:     @anthropic-ai/sdk
├── MCP SDK:    @modelcontextprotocol/sdk
└── 原生模块:   N-API (音频捕获、图像处理、URL Handler)
```

### 核心模块层次

![核心模块层次](assets/cc.png)

```
src/
├── entrypoints/          # 程序入口点 (CLI, MCP, SDK)
├── main.tsx              # 主启动逻辑
├── commands/             # 70+ 斜杠命令实现
├── tools/                # 30+ 内置工具实现
├── components/           # React 终端 UI 组件
├── screens/              # 主屏幕 (REPL, Doctor, ResumeConversation)
├── services/             # 后端服务 (API, MCP, OAuth, Analytics)
├── utils/                # 工具函数库
│   ├── model/            # 模型管理与多提供商支持
│   ├── permissions/      # 权限系统
│   ├── swarm/            # 多智能体编排
│   ├── settings/         # 配置管理
│   ├── telemetry/        # 遥测与追踪
│   └── shell/            # Shell 提供商 (Bash, PowerShell)
├── bridge/               # 远程桥接层
├── memdir/               # 持久化记忆管理
├── plugins/              # 插件系统
├── skills/               # Skills 体系
└── vim/                  # Vim 按键绑定引擎
```

---

## 支持的模型

| 模型系列 | 模型标识符 | 特点 |
|---------|-----------|------|
| **Claude Haiku 4.5** | `claude-haiku-4-5-20251001` | 轻量快速，适合简单任务 |
| **Claude Sonnet 4** | `claude-sonnet-4-20250514` | 均衡性能 |
| **Claude Sonnet 4.5** | `claude-sonnet-4-5-20250929` | 增强版 Sonnet |
| **Claude Sonnet 4.6** | `claude-sonnet-4-6` | 最新 Sonnet |
| **Claude Opus 4** | `claude-opus-4-20250514` | 旗舰推理能力 |
| **Claude Opus 4.1** | `claude-opus-4-1-20250805` | 增强版 Opus |
| **Claude Opus 4.5** | `claude-opus-4-5-20251101` | 高级 Opus |
| **Claude Opus 4.6** | `claude-opus-4-6` | 最新旗舰 |
| **Claude 3.7 Sonnet** | `claude-3-7-sonnet-20250219` | 扩展思考支持 |
| **Claude 3.5 Sonnet** | `claude-3-5-sonnet-20241022` | 经典高性能 |
| **Claude 3.5 Haiku** | `claude-3-5-haiku-20241022` | 经典轻量 |

---

## API 提供商

Claude Code 支持四种 API 提供商，通过环境变量切换：

| 提供商 | 环境变量 | 说明 |
|--------|---------|------|
| **Anthropic 官方** | 默认 | 直接调用 `api.anthropic.com` |
| **AWS Bedrock** | `CLAUDE_CODE_USE_BEDROCK=1` | 通过 AWS 托管服务调用 |
| **Google Vertex AI** | `CLAUDE_CODE_USE_VERTEX=1` | 通过 GCP 托管服务调用 |
| **Azure Foundry** | `CLAUDE_CODE_USE_FOUNDRY=1` | 通过 Azure AI Foundry 调用 |

自定义 API 端点：
```bash
export ANTHROPIC_BASE_URL=https://your-proxy.example.com
export ANTHROPIC_MODEL=claude-opus-4-6  # 指定默认模型
```

---

## 内置工具

Claude Code 内置了覆盖开发全场景的 30+ 工具：

### 文件与代码操作
| 工具 | 功能描述 |
|------|---------|
| `FileReadTool` | 读取文件内容，支持按行范围读取 |
| `FileWriteTool` | 写入/创建文件 |
| `FileEditTool` | 精准编辑文件（字符串替换、块替换） |
| `GlobTool` | 文件路径 Glob 模式匹配 |
| `GrepTool` | 在文件内容中进行正则搜索 |
| `NotebookEditTool` | 编辑 Jupyter Notebook 单元格 |
| `LSPTool` | 语言服务协议集成（代码诊断、跳转等） |

### Shell 与执行
| 工具 | 功能描述 |
|------|---------|
| `BashTool` | 执行 Bash 命令，内置安全检查与沙箱支持 |
| `PowerShellTool` | 执行 Windows PowerShell 命令 |
| `REPLTool` | 交互式 REPL 环境 |

### 网络与信息
| 工具 | 功能描述 |
|------|---------|
| `WebFetchTool` | 抓取网页内容并转换为 Markdown |
| `WebSearchTool` | 执行网络搜索 |

### 智能体与任务
| 工具 | 功能描述 |
|------|---------|
| `AgentTool` | 启动子智能体执行复杂任务 |
| `TaskCreateTool` | 创建后台异步任务 |
| `TaskListTool` | 列出所有任务 |
| `TaskGetTool` | 获取任务详情 |
| `TaskUpdateTool` | 更新任务状态 |
| `TaskOutputTool` | 获取任务输出 |
| `TaskStopTool` | 停止任务 |

### 协作与系统
| 工具 | 功能描述 |
|------|---------|
| `MCPTool` | 调用 MCP 服务器提供的工具 |
| `TeamCreateTool` | 创建多智能体团队 |
| `TeamDeleteTool` | 解散多智能体团队 |
| `TodoWriteTool` | 管理 Todo 列表 |
| `SkillTool` | 执行自定义 Skill |
| `ScheduleCronTool` | 创建定时任务 |
| `SleepTool` | 等待指定时间 |
| `AskUserQuestionTool` | 向用户提问并等待回答 |
| `ConfigTool` | 读取/修改配置 |
| `SendMessageTool` | 向团队成员发送消息 |
| `ToolSearchTool` | 搜索可用工具 |
| `RemoteTriggerTool` | 触发远程操作 |
| `BriefTool` | 生成简报（需 KAIROS 特性） |

---

## 斜杠命令

在 REPL 中输入 `/` 可触发 70+ 内置斜杠命令：

### 项目与会话管理
| 命令 | 功能 |
|------|------|
| `/init` | 初始化项目，生成 `CLAUDE.md` |
| `/resume` | 恢复历史会话 |
| `/compact` | 压缩当前对话历史 |
| `/clear` | 清除当前对话 |
| `/exit` | 退出 Claude Code |
| `/session` | 管理会话 |
| `/rename` | 重命名当前会话 |

### 代码与 Git 操作
| 命令 | 功能 |
|------|------|
| `/commit` | 生成并提交 Git commit |
| `/commit-push-pr` | 提交、推送并创建 PR |
| `/diff` | 显示 Git diff |
| `/branch` | 管理 Git 分支 |
| `/review` | AI 代码审查 |
| `/security-review` | 安全审查 |
| `/pr_comments` | 处理 PR 评论 |
| `/worktree` | Git Worktree 模式操作 |

### AI 与模型
| 命令 | 功能 |
|------|------|
| `/model` | 切换模型 |
| `/effort` | 调整推理力度 |
| `/think` | 切换思考模式 |
| `/fast` | 切换快速模式 |
| `/plan` | 进入计划模式 |
| `/memory` | 管理 AI 记忆 |
| `/context` | 查看上下文信息 |

### 工具与配置
| 命令 | 功能 |
|------|------|
| `/config` | 查看/修改配置 |
| `/permissions` | 管理工具权限 |
| `/mcp` | 管理 MCP 服务器 |
| `/hooks` | 管理 Hooks |
| `/skills` | 管理 Skills |
| `/plugins` | 管理插件 |
| `/env` | 管理环境变量 |
| `/keybindings` | 查看/修改快捷键 |

### 辅助工具
| 命令 | 功能 |
|------|------|
| `/help` | 显示帮助信息 |
| `/doctor` | 诊断环境问题 |
| `/cost` | 查看 token 消耗与费用 |
| `/stats` | 查看使用统计 |
| `/status` | 查看系统状态 |
| `/feedback` | 发送反馈 |
| `/share` | 分享会话 |
| `/export` | 导出会话内容 |
| `/theme` | 切换主题 |
| `/vim` | 切换 Vim 模式 |
| `/voice` | 切换语音模式 |
| `/upgrade` | 升级 Claude Code |
| `/version` | 显示版本信息 |
| `/agents` | 管理智能体 |
| `/tasks` | 查看任务列表 |
| `/teleport` | 远程环境传送 |
| `/ide` | IDE 集成管理 |
| `/summary` | 生成会话摘要 |
| `/output-style` | 设置输出风格 |

---

## 项目结构

```
.
├── src/
│   ├── assistant/              # Assistant 模式 (KAIROS 特性)
│   ├── bootstrap/              # 启动状态管理
│   ├── bridge/                 # 远程桥接 (WebSocket/SSE)
│   ├── buddy/                  # Companion 精灵系统
│   ├── cli/                    # CLI 传输层与打印工具
│   ├── commands/               # 斜杠命令实现 (70+)
│   ├── components/             # React/Ink UI 组件 (100+)
│   ├── constants/              # 全局常量与系统提示词
│   ├── context/                # React Context (通知、统计)
│   ├── coordinator/            # 协调者模式
│   ├── entrypoints/            # 入口点 (CLI, MCP, SDK)
│   ├── hooks/                  # React Hooks
│   ├── ink/                    # Ink 终端渲染扩展
│   ├── keybindings/            # 快捷键系统
│   ├── memdir/                 # 持久化记忆目录
│   ├── migrations/             # 数据迁移脚本
│   ├── native-ts/              # 原生模块 TypeScript 绑定
│   ├── outputStyles/           # 输出样式定义
│   ├── plugins/                # 插件加载器与内置插件
│   ├── query/                  # 查询引擎
│   ├── remote/                 # 远程会话组件
│   ├── schemas/                # JSON Schema 定义
│   ├── screens/                # 主屏幕 (REPL, Doctor 等)
│   ├── server/                 # 内置服务器
│   ├── services/               # 后端服务
│   │   ├── analytics/          # 分析与 GrowthBook 特性标志
│   │   ├── api/                # Anthropic API 客户端
│   │   ├── mcp/                # MCP 客户端
│   │   ├── oauth/              # OAuth 2.0 认证
│   │   ├── policyLimits/       # 策略限制
│   │   └── remoteManagedSettings/ # 远程托管配置
│   ├── skills/                 # Skills 体系
│   ├── state/                  # 全局状态管理
│   ├── tasks/                  # 任务系统 (本地/Teammate)
│   ├── tools/                  # 内置工具实现 (30+)
│   ├── types/                  # TypeScript 类型定义
│   ├── upstreamproxy/          # 代理支持
│   ├── utils/                  # 工具函数
│   │   ├── claudeInChrome/     # Chrome 原生宿主集成
│   │   ├── ide/                # IDE 集成工具
│   │   ├── model/              # 模型管理
│   │   ├── permissions/        # 权限系统
│   │   ├── sandbox/            # 沙箱适配器
│   │   ├── secureStorage/      # 安全存储 (macOS Keychain)
│   │   ├── settings/           # 配置管理
│   │   ├── shell/              # Shell 提供商
│   │   ├── swarm/              # 多智能体编排
│   │   ├── task/               # 任务框架
│   │   ├── teleport/           # 远程传送功能
│   │   └── telemetry/          # 遥测与追踪
│   ├── vim/                    # Vim 按键引擎
│   └── voice/                  # 语音模式
└── vendor/
    ├── audio-capture-src/      # 原生音频捕获模块 (N-API)
    ├── image-processor-src/    # 原生图像处理模块 (Sharp 兼容)
    ├── modifiers-napi-src/     # 原生修饰键检测模块
    └── url-handler-src/        # 原生 URL 处理模块
```

---

## 快速开始

### 环境要求

- **Node.js** 18+ 或 **Bun** 1.x
- **操作系统**：macOS、Linux 或 Windows
- **Anthropic API Key** 或兼容的云服务凭证

### 安装依赖

```bash
# 克隆仓库
git clone https://github.com/your-username/claude-code-open.git
cd claude-code-open

# 使用 Bun 安装依赖（推荐）
bun install

# 或使用 npm
npm install
```

### 认证配置

**方式一：API Key（推荐入门）**
```bash
export ANTHROPIC_API_KEY=sk-ant-xxxxxxxxxxxxxxxxxxxx
```

**方式二：OAuth（claude.ai 订阅用户）**
```bash
# 运行后会自动打开浏览器完成 OAuth 授权
bun run src/entrypoints/cli.tsx login
```

**方式三：AWS Bedrock**
```bash
export CLAUDE_CODE_USE_BEDROCK=1
export AWS_REGION=us-east-1
# 确保已配置 AWS 凭证 (~/.aws/credentials 或环境变量)
```

**方式四：Google Vertex AI**
```bash
export CLAUDE_CODE_USE_VERTEX=1
export ANTHROPIC_VERTEX_PROJECT_ID=your-project-id
export CLOUD_ML_REGION=us-central1
# 确保已配置 Google Cloud 凭证
```

### 启动开发模式

```bash
# 启动交互式 REPL
bun run src/entrypoints/cli.tsx

# 非交互模式执行单次任务
bun run src/entrypoints/cli.tsx -p "帮我分析这个项目的架构"

# 指定工作目录
bun run src/entrypoints/cli.tsx --cwd /path/to/your/project

# 指定模型
bun run src/entrypoints/cli.tsx --model claude-opus-4-6
```

### 构建

```bash
# 构建生产版本
bun build src/entrypoints/cli.tsx --outfile dist/claude-code --target bun

# 查看版本
./dist/claude-code --version
```

---

## 配置说明

### 全局配置

全局配置文件位于 `~/.claude/` 目录：

```
~/.claude/
├── settings.json          # 全局用户配置
├── .credentials.json      # OAuth 凭证（加密存储）
└── memories/              # AI 记忆存储
```

### 项目配置

在项目根目录创建 `CLAUDE.md` 文件，Claude Code 会自动读取并作为项目上下文：

```markdown
# 项目说明

这是一个 TypeScript + React 项目，使用以下技术栈：
- Framework: Next.js 14
- Database: PostgreSQL + Prisma
- Testing: Vitest

## 编码规范
- 使用 ESLint + Prettier
- 提交前运行 `npm test`
- 分支命名: feature/xxx, fix/xxx

## 重要文件
- `src/app/` - 主应用代码
- `prisma/schema.prisma` - 数据库 Schema
```

项目级配置文件 `.claude/settings.json`：

```json
{
  "allowedTools": ["BashTool", "FileEditTool", "FileReadTool"],
  "mcpServers": {
    "my-server": {
      "command": "node",
      "args": ["./mcp-server/index.js"]
    }
  }
}
```

### 主要配置项

| 配置项 | 类型 | 说明 |
|--------|------|------|
| `model` | string | 默认使用的 Claude 模型 |
| `allowedTools` | string[] | 允许使用的工具列表 |
| `mcpServers` | object | MCP 服务器配置 |
| `theme` | string | UI 主题 (`dark`/`light`/`system`) |
| `vim` | boolean | 是否启用 Vim 按键绑定 |
| `notifications` | object | 通知配置 |
| `autoUpdater` | object | 自动更新配置 |

### 环境变量

| 变量名 | 说明 |
|--------|------|
| `ANTHROPIC_API_KEY` | Anthropic API 密钥 |
| `ANTHROPIC_BASE_URL` | 自定义 API 端点 |
| `ANTHROPIC_MODEL` | 默认模型覆盖 |
| `CLAUDE_CODE_USE_BEDROCK` | 启用 AWS Bedrock |
| `CLAUDE_CODE_USE_VERTEX` | 启用 Google Vertex AI |
| `CLAUDE_CODE_USE_FOUNDRY` | 启用 Azure Foundry |
| `CLAUDE_CODE_REMOTE` | 标记为远程模式 |
| `DISABLE_AUTO_COMPACT` | 禁用自动压缩 |
| `CLAUDE_CODE_DISABLE_THINKING` | 禁用思考模式 |
| `CLAUDE_CODE_DISABLE_AUTO_MEMORY` | 禁用自动记忆 |

---

## 权限系统

Claude Code 内置了细粒度的权限管理系统，防止 AI 执行未授权的操作。

### 权限模式

| 模式 | 说明 |
|------|------|
| `default` | 默认模式，需要对敏感操作进行确认 |
| `auto` | 自动模式，自动批准安全操作 |
| `bypass` | 绕过模式，跳过所有权限检查（慎用） |

### 权限规则配置

在项目配置中设置允许/拒绝规则：

```json
{
  "allowedTools": [
    "BashTool(git *)",
    "BashTool(npm *)",
    "FileEditTool",
    "FileReadTool"
  ]
}
```

### 沙箱模式

在沙箱模式下，所有文件操作和 Shell 命令将在隔离环境中执行：

```bash
# 启用沙箱
claude /sandbox-toggle
```

---

## MCP 支持

Claude Code 提供完整的 [Model Context Protocol (MCP)](https://modelcontextprotocol.io/) 客户端支持。

### 添加 MCP 服务器

```bash
# 交互式添加
claude /mcp add

# 或直接编辑配置文件
```

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "/tmp"]
    },
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_TOKEN": "your-token"
      }
    },
    "remote-server": {
      "type": "sse",
      "url": "https://mcp.example.com/sse"
    }
  }
}
```

### 支持的传输类型

- **stdio**：通过标准输入/输出与本地进程通信
- **SSE**：服务器发送事件（HTTP 长连接）
- **WebSocket**：双向实时通信
- **In-Process**：进程内通信（内置服务器）

### MCP 认证

支持 OAuth 2.0 认证的 MCP 服务器：

```bash
# 对需要认证的 MCP 服务器进行授权
claude /mcp auth <server-name>
```

---

## 多智能体系统

Claude Code 支持通过 **Swarm（蜂群）** 模式协调多个 AI 智能体并行工作。

### 工作原理

```
Leader Agent (领导智能体)
    ├── Worker Agent 1 (工作智能体 1) → Tmux Pane / iTerm2 Tab
    ├── Worker Agent 2 (工作智能体 2) → Tmux Pane / iTerm2 Tab
    └── Worker Agent 3 (工作智能体 3) → In-Process
```

### 支持的后端

| 后端 | 说明 | 要求 |
|------|------|------|
| `TmuxBackend` | 在 Tmux 窗格中启动 Worker | 需要 Tmux |
| `ITermBackend` | 在 iTerm2 标签页中启动 Worker | 需要 iTerm2 (macOS) |
| `InProcessBackend` | 在同一进程内启动 Worker | 无额外要求 |

### 使用示例

```bash
# 创建团队并分配任务
claude /agents

# 在 REPL 中直接编排
> 请用3个并行智能体，分别重构 auth、api 和 ui 模块
```

### 权限同步

多智能体模式下，Worker 的权限请求会通过邮箱（Mailbox）系统同步给 Leader 智能体进行审批，确保安全可控。

---

## IDE 集成

### VS Code 集成

Claude Code 支持与 VS Code 深度集成，通过本地 Socket 进行通信：

```bash
# 在 Claude Code 中启用 IDE 集成
claude /ide connect
```

集成功能包括：
- 在 VS Code 中打开文件（支持跳转到指定行）
- 实时同步诊断信息（错误、警告）
- 获取当前选中代码/文件上下文
- 在 VS Code 终端中运行命令

### LSP 集成

Claude Code 内置 LSP 客户端，可直接使用语言服务器获取：
- 代码诊断（错误/警告）
- 跳转到定义
- 悬浮文档
- 代码补全建议

---

## 语音模式

Claude Code 支持语音输入/输出，通过原生音频模块实现低延迟录音。

### 平台支持

| 平台 | 录音 | 播放 | 麦克风授权检测 |
|------|------|------|-------------|
| macOS | ✅ | ✅ | ✅ (TCC) |
| Linux | ✅ | ✅ | N/A (默认授权) |
| Windows | ✅ | ✅ | ✅ (注册表) |

### 启用语音模式

```bash
# 在 REPL 中切换语音模式
claude /voice

# 或通过命令行启动
claude --voice
```

---

## 远程会话

### Claude Code Remote (CCR)

通过 `CLAUDE_CODE_REMOTE=true` 启动远程模式，使用 WebSocket 或 SSE 传输：

```bash
# 启动远程会话
export CLAUDE_CODE_REMOTE=true
claude

# 通过 claude.ai 网页端访问
# 访问: https://claude.ai/code/<session-id>
```

### Bridge 模式

Bridge 模式允许通过 claude.ai 平台建立与本地 Claude Code 实例的安全连接：

```bash
# 启动 Bridge 服务
claude /bridge start
```

### Teleport 功能

Teleport 允许将本地项目"传送"到远程开发环境：

```bash
# 传送到远程环境
claude /teleport
```

---

## 贡献指南

欢迎提交 Pull Request 和 Issue！在贡献之前，请阅读以下规范：

### 开发环境设置

```bash
# 1. Fork 并克隆仓库
git clone https://github.com/your-username/claude-code-open.git
cd claude-code-open

# 2. 安装依赖
bun install

# 3. 创建功能分支
git checkout -b feature/your-feature-name

# 4. 启动开发模式
bun run src/entrypoints/cli.tsx
```

### 代码规范

- 使用 **TypeScript** 严格模式
- 遵循项目现有的 **ESLint** 和 **Biome** 配置
- 组件使用 **React Functional Components** + Hooks
- 文件命名：组件使用 `PascalCase.tsx`，工具函数使用 `camelCase.ts`

### 添加新工具

1. 在 `src/tools/` 下创建新目录（参考 `BashTool` 结构）
2. 实现 `Tool` 接口
3. 在 `src/tools.ts` 中注册工具
4. 在 `src/constants/tools.ts` 中添加工具名称常量

```typescript
// src/tools/MyTool/MyTool.ts
import type { Tool } from '../../Tool.js'

export const MyTool: Tool = {
  name: 'MyTool',
  description: '工具描述',
  inputSchema: {
    type: 'object',
    properties: {
      input: { type: 'string', description: '输入参数' }
    },
    required: ['input']
  },
  async call({ input }, context) {
    // 工具实现
    return { result: `处理结果: ${input}` }
  }
}
```

### 添加新命令

1. 在 `src/commands/` 下创建新目录
2. 实现 `Command` 接口
3. 在 `src/commands.ts` 中导入并注册

### 提交规范

遵循 [Conventional Commits](https://www.conventionalcommits.org/) 规范：

```
feat: 添加新的 WebSocket 传输层
fix: 修复 BashTool 在 Windows 下的路径问题
docs: 更新 MCP 配置文档
refactor: 重构权限系统模块
test: 添加 FileEditTool 单元测试
```

### Pull Request 流程

1. 确保代码通过 lint 检查：`bun run lint`
2. 确保所有测试通过：`bun test`
3. 更新相关文档
4. 提交 PR 并填写详细描述

---

## 安全说明

> ⚠️ **重要**：此项目包含可执行 Shell 命令、读写文件系统、发起网络请求的能力。请在使用前充分理解权限系统，避免在生产环境中使用 `bypass` 权限模式。

- **API Key 保护**：永远不要将 API Key 提交到版本控制系统
- **沙箱使用**：在处理不可信代码时启用沙箱模式
- **权限最小化**：仅在 `allowedTools` 中配置必要的工具
- **审查输出**：在自动模式下定期审查 AI 执行的操作

---

## 常见问题

**Q: 如何切换到不同的 Claude 模型？**
```bash
# 在 REPL 中
/model

# 通过命令行参数
claude --model claude-opus-4-6

# 通过环境变量
export ANTHROPIC_MODEL=claude-opus-4-6
```

**Q: 如何禁用自动更新？**
```bash
export CLAUDE_CODE_DISABLE_AUTO_UPDATER=1
```

**Q: 如何在 CI/CD 环境中使用？**
```bash
# 非交互式模式
claude -p "运行测试并修复所有失败" --no-interactive

# 使用 API Key 认证
export ANTHROPIC_API_KEY=your-key
claude -p "检查代码质量"
```

**Q: 如何查看 token 消耗？**
```bash
# 在 REPL 中
/cost
```

**Q: 项目上下文如何工作？**

Claude Code 会自动读取当前目录及父目录中的 `CLAUDE.md` 文件，将其内容注入系统提示词作为项目上下文。同时支持 `.claude/` 目录下的配置文件。

---

## 许可证

本项目基于 [MIT License](LICENSE) 开源。

```
MIT License

Copyright (c) 2024 Anthropic

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

---

## 致谢

感谢以下开源项目的支持：

- [Anthropic SDK](https://github.com/anthropic-ai/anthropic-sdk-typescript) - TypeScript API 客户端
- [Ink](https://github.com/vadimdemedes/ink) - React 终端 UI 框架
- [Model Context Protocol](https://github.com/modelcontextprotocol) - MCP 标准协议
- [Bun](https://bun.sh/) - 高性能 JavaScript 运行时与打包器
- [Commander.js](https://github.com/tj/commander.js) - CLI 参数解析
- [GrowthBook](https://www.growthbook.io/) - 特性标志管理

---

<div align="center">

**Claude Code** — 让 AI 成为你最强大的编程伙伴

[报告 Bug](https://github.com/your-username/claude-code-open/issues) · [功能建议](https://github.com/your-username/claude-code-open/issues) · [讨论](https://github.com/your-username/claude-code-open/discussions)

</div>

---

## English

Claude Code is the complete source code of Anthropic's official AI coding assistant CLI tool. It integrates the powerful Claude large language model directly into your terminal workflow, providing AI-enhanced capabilities including code writing, file operations, shell command execution, web search, and more.

### Quick Start

```bash
# Clone the repository
git clone https://github.com/your-username/claude-code-open.git
cd claude-code-open

# Install dependencies
bun install

# Set your API key
export ANTHROPIC_API_KEY=sk-ant-xxxxxxxxxxxxxxxxxxxx

# Start the interactive REPL
bun run src/entrypoints/cli.tsx
```

### Key Features

- **Multi-model support**: Claude 3.5, 3.7, Claude 4.x series (Haiku / Sonnet / Opus)
- **30+ built-in tools**: File operations, shell execution, web search, LSP integration, and more
- **70+ slash commands**: Git operations, code review, memory management, MCP server management
- **Multi-agent Swarm**: Orchestrate multiple AI agents via Tmux/iTerm2 backends
- **MCP Protocol**: Full Model Context Protocol client support
- **Multiple API providers**: Anthropic, AWS Bedrock, Google Vertex AI, Azure Foundry
- **Voice mode**: Native audio capture for voice input/output
- **IDE integration**: VS Code deep integration with LSP support
- **Remote sessions**: WebSocket/SSE-based remote Claude Code sessions
- **Rich terminal UI**: React + Ink with themes, Vim keybindings, syntax highlighting

### Supported Platforms

| Platform | Status |
|----------|--------|
| macOS | ✅ Full support |
| Linux | ✅ Full support |
| Windows | ✅ Full support (PowerShell) |

### License

MIT License — See [LICENSE](LICENSE) for details.
