# Multi Agents

这个仓库收集可复制到项目中的多 Agent 协作启动模板。目标是让 AI 编程助手在项目里建立可选的 Manager / Builder / Reviewer 协作机制，同时保持默认关闭，避免影响不想启用该流程的团队成员。

每个目录都是一个独立版本。进入对应目录后，阅读该目录的 `README.md`，再把其中的 `multi-agent-bootstrap.md` 复制到目标项目的 AI 编程助手会话中执行。

## 目录说明

| 目录 | 功能 | 适合场景 | 默认状态 |
| --- | --- | --- | --- |
| `multi-agent-superpowers` | 多 Agent 协作模板，支持自动探测 Superpowers、skills、plugins、MCP tools 和项目本地工具。 | 想要基础 Manager / Builder / Reviewer 流程，并让助手按可用增强能力执行任务。 | 默认关闭，本地可启用 |
| `multi-agent-superpowers-agentskills` | 多 Agent 协作模板，额外集成 `addyosmani/agent-skills` 或兼容技能库，支持 `/spec`、`/plan`、`/build`、`/test`、`/review`、`/ship` 等生命周期路由。 | 想把多 Agent 协作和工程生命周期技能结合起来，适合更规范的需求、计划、实现、测试、审查流程。 | 默认关闭，本地可启用 |

## 通用使用流程

1. 选择一个目录。
2. 打开该目录的 `README.md`。
3. 在目标项目中打开 AI 编程助手或 Agent 会话。
4. 按目录 README 的说明，把 `multi-agent-bootstrap.md` 全文喂给助手。
5. 让助手把规则写入目标项目的 `AGENTS.md` 和 `.agents/`。

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
