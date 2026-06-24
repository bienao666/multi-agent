# Multi-Agent Bootstrap

这个目录提供一份可复制到任意项目 AI 编程助手或 Agent 会话中的多 Agent 启动文档：

- `multi-agent-bootstrap.md`

它的作用是让 AI 编程助手在目标项目中初始化一套 Manager / Builder / Reviewer 协作机制，并自动创建 `.agents/`、`AGENTS.md`、任务日志、能力注册、复杂度分级、失败恢复和验收流程。

该机制默认关闭，适合提交到项目仓库中作为可选协作能力。团队其他成员不会被强制启用；需要使用的人可以在本地开启。

## 使用方式

在任意具体项目中打开一个新的 AI 编程助手或 Agent 会话，然后发送：

```text
请完整读取并执行下面这份 Multi-Agent Bootstrap Prompt。
执行后把协作规则写入当前项目，并初始化 .agents/ 和 AGENTS.md。
```

接着把 `multi-agent-bootstrap.md` 的全文粘贴进去。

AI 编程助手会自动：

- 扫描当前项目结构和技术栈。
- 创建或更新 `AGENTS.md`。
- 创建或更新 `.agents/` 协作目录。
- 初始化 Manager、Builder、Reviewer 三个基础 Agent。
- 建立任务协议、任务日志、验收清单和失败恢复流程。
- 探测当前环境可用的 Superpowers、skills、plugins、MCP tools 和项目本地工具。
- 创建 `.agents/settings.md`，默认 `multi_agent_default: off`、`real_subagents_default: off`。
- 创建 `.agents/session-registry.md`，用于在启用多 Agent 后记录 Builder / Reviewer 等独立会话。
- 后续只有在用户本地启用后，才按 Manager 分配、Builder 执行、Reviewer 验收、Manager 汇总的流程工作。

## 从旧版本升级

如果你的项目以前已经使用过旧版 `multi-agent-bootstrap.md`，不要手动删除旧的 `.agents/` 或 `AGENTS.md`。

在目标项目中打开 AI 编程助手，然后发送：

```text
请读取下面这份新版 Multi-Agent Bootstrap 文档，并对当前项目已有的 .agents/ 和 AGENTS.md 做兼容升级。
要求：
1. 不覆盖用户已有内容。
2. 不删除旧任务日志、决策记录、经验记录。
3. 只补齐缺失文件、缺失字段和新增规则。
4. 如果同一规则已存在，只更新为新版语义，不重复追加。
5. 升级完成后输出升级摘要。
```

然后粘贴新版 `multi-agent-bootstrap.md` 全文。

升级时重点检查：

- `.agents/settings.md` 是否包含带注释的 `multi_agent_default`、`reviewer_for_simple_default` 和 `real_subagents_default`。
- `.agents/local-settings.md` 是否已加入 `.gitignore`。
- `.agents/session-registry.md` 是否存在。
- 协议字段是否包含 `目标会话` 和 `来源会话`。
- 是否支持客户端原生 `sub-agent`、`spawn_agent`、`worker`、`explorer`。
- 是否支持 `reviewer_for_simple`，让简单任务也可选进入 Reviewer。
- Manager / Builder / Reviewer 输出字段是否已中文化。

建议让 AI 最后给出：

```md
## Upgrade Summary

已新增:
已更新:
保持不变:
需要人工确认:
```

## 初始化后怎么使用

初始化完成后，多 Agent 协作默认关闭。你可以把这些规则提交到项目仓库，让团队共享，但每个人可以选择是否启用。

本地启用方式：

```text
请在当前项目为我本地启用 Multi-Agent Mode。
创建 .agents/local-settings.md，写入 multi_agent: on，并自动把 .agents/local-settings.md 添加到项目根目录 .gitignore。
```

或者你也可以手动创建：

```text
.agents/local-settings.md
```

内容：

```text
multi_agent: on
```

如果希望简单任务也由 Reviewer 复核，可以写成：

```text
#### 本地启用多 Agent 协作模式
multi_agent: on

#### 简单任务也启用 Reviewer 复核
reviewer_for_simple: on

#### 明确授权自动创建真实 sub-agent
real_subagents: on
```

启用时助手应自动把它加入 `.gitignore`：

```gitignore
.agents/local-settings.md
```

启用后，在同一个项目里不需要再重复说“按多 Agent 流程”或“按 Manager / Builder / Reviewer 流程”。

如果当前 AI 工具支持 `sub-agent`、`spawn_agent`、`worker`、`explorer` 等原生子智能体工具，Manager 会优先创建真实子智能体；这类客户端可能会在界面中展示子智能体列表和各自的改动统计。  
如果只支持 thread 或独立会话，Manager 会创建或复用 Builder / Reviewer 独立会话；如果都不支持，则在当前会话中模拟角色切换。

你可以直接像平常一样提需求：

```text
修复登录页按钮点击无响应的问题
```

或者：

```text
给订单列表增加导出 CSV 的功能
```

AI 编程助手应自动：

- 检查 Multi-Agent Mode 是否已启用。
- 把请求交给 Manager intake。
- 判断任务复杂度。
- 判断是否需要 Builder、Reviewer 或临时 Agent。
- 判断是否有 Superpowers、skills、plugins 或 MCP tools 可以使用。
- 按合适流程执行、验收并汇总。

如果当前环境安装了 Superpowers 或其他 skills，可以这样说：

```text
这个任务可以优先使用 Superpowers 里的相关能力。
```

这不是必需提示，只是当你想特别强调使用 Superpowers 时可以加上。

## 建议确认项

第一次粘贴文档后，可以让 AI 编程助手确认：

```text
请确认你已经创建或更新 AGENTS.md 和 .agents/*，并说明之后你会如何按 Manager / Builder / Reviewer 流程工作。
```

确认通过后，这个项目就具备了项目级多 Agent 协作规则。

## 开关规则

默认关闭：

```text
.agents/settings.md
#### 项目默认不启用多 Agent，适合提交到团队仓库
multi_agent_default: off

#### 简单任务默认不启用 Reviewer
reviewer_for_simple_default: off

#### 默认不预授权真实 sub-agent；需要本地开启后才可自动创建 Builder / Reviewer
real_subagents_default: off
```

个人本地开启：

```text
.agents/local-settings.md
#### 本地启用多 Agent
multi_agent: on

#### 本地启用简单任务 Reviewer
reviewer_for_simple: on

#### 本地授权真实 sub-agent 自动创建
real_subagents: on
```

个人本地关闭：

```text
.agents/local-settings.md
#### 本地关闭多 Agent
multi_agent: off

#### 本地关闭简单任务 Reviewer
reviewer_for_simple: off

#### 本地关闭真实 sub-agent 自动创建
real_subagents: off
```

当前消息也可以临时控制：

```text
这次启用多 Agent 处理。
```

或：

```text
这次不要使用多 Agent，直接处理。
```

## 注意事项

- 直接把文档喂给当前 AI 编程助手，只能保证当前会话知道这些规则。
- 让 AI 编程助手把规则写入 `AGENTS.md` 和 `.agents/` 后，新会话更容易自动继承这些规则。
- 初始化完成后，多 Agent 流程默认关闭，避免影响不想启用的同事。
- 启用后正常提需求即可，不需要重复提示助手使用该流程。
- 如果目标项目已经有 `AGENTS.md`，助手应保留原内容，只追加缺失的多 Agent 规则。
- 如果当前环境不支持真实 thread、subagent 或跨会话消息，助手会在同一会话中用明确角色切换模拟多 Agent 协作。
- 如果当前环境没有 Superpowers 或类似增强能力，助手会自动降级为普通本地多 Agent 流程。
