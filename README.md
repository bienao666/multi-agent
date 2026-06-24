# AI Agent Playbook

这个仓库收集可复制到项目中的 AI 使用技巧、工作流模板和 Agent 协作方法。目标是把零散的 AI 使用经验沉淀成可复用的 Markdown Playbook，方便在不同项目、不同工具和不同工作场景中快速启用。

当前内容包括多 Agent 协作、Superpowers / skills 自动调用、agent-skills 生命周期路由，以及 AI 工作上下文系统。后续也可以继续扩展更多 AI 编程、办公、知识管理、自动化和团队协作技巧。

每个目录都是一个独立能力包。进入对应目录后，阅读该目录的 `README.md`，再把其中的 Markdown 文档复制到目标项目或 AI 助手会话中执行。

## 目录说明

| 目录 | 功能 | 适合场景 | 默认状态 |
| --- | --- | --- | --- |
| `multi-agent-superpowers` | 多 Agent 协作模板，支持自动探测 Superpowers、skills、plugins、MCP tools 和项目本地工具。 | 想要基础 Manager / Builder / Reviewer 流程，并让助手按可用增强能力执行任务。 | 默认关闭，本地可启用 |
| `multi-agent-superpowers-agentskills` | 多 Agent 协作模板，额外集成 `addyosmani/agent-skills` 或兼容技能库，支持 `/spec`、`/plan`、`/build`、`/test`、`/review`、`/ship` 等生命周期路由。 | 想把多 Agent 协作和工程生命周期技能结合起来，适合更规范的需求、计划、实现、测试、审查流程。 | 默认关闭，本地可启用 |
| `work-context-system` | AI 工作上下文系统模板，提供人物库、项目库、事件库、产出模板库的 Markdown 结构和提示词。 | 想让 AI 更懂“写给谁看”、项目背景、历史事件和固定产出格式，适合汇报、复盘、方案、会议纪要等职场场景。 | 手动初始化 |

## 通用使用流程

1. 选择一个目录。
2. 打开该目录的 `README.md`。
3. 在目标项目中打开 AI 编程助手或 Agent 会话。
4. 按目录 README 的说明，把对应 Markdown 文档全文喂给助手。
5. 让助手把规则、模板或上下文结构写入目标项目。

如果选择 `work-context-system`，则按该目录 README 初始化 `.work-context/`，它不依赖 `.agents/` 或多 Agent 开关。

## 开关机制

模板默认创建项目级设置：

```text
.agents/settings.md
multi_agent_default: off
```

个人本地启用：

```text
.agents/local-settings.md
multi_agent: on
```

启用本地设置时，助手应自动把它加入目标项目的 `.gitignore`：

```gitignore
.agents/local-settings.md
```

如果目标项目没有 `.gitignore`，助手应创建一个并写入该规则。这样可以把多 Agent 协作模板提交到仓库，但不会强制所有同事启用。
