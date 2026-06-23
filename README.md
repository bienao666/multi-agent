# Multi-Agent Bootstrap

这个目录提供一份可复制到任意项目 AI 编程助手或 Agent 会话中的多 Agent 启动文档：

- `multi-agent-bootstrap.md`

它的作用是让 AI 编程助手在目标项目中初始化一套 Manager / Builder / Reviewer 协作机制，并自动创建 `.agents/`、`AGENTS.md`、任务日志、能力注册、复杂度分级、失败恢复和验收流程。

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
- 后续按 Manager 分配、Builder 执行、Reviewer 验收、Manager 汇总的流程工作。

## 初始化后怎么使用

初始化完成后，在同一个项目里不需要再重复说“按多 Agent 流程”或“按 Manager / Builder / Reviewer 流程”。

你可以直接像平常一样提需求：

```text
修复登录页按钮点击无响应的问题
```

或者：

```text
给订单列表增加导出 CSV 的功能
```

AI 编程助手应自动：

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

## 注意事项

- 直接把文档喂给当前 AI 编程助手，只能保证当前会话知道这些规则。
- 让 AI 编程助手把规则写入 `AGENTS.md` 和 `.agents/` 后，新会话更容易自动继承这些规则。
- 初始化完成后，多 Agent 流程应成为项目默认工作模式。
- 后续正常提需求即可，不需要重复提示助手使用该流程。
- 如果目标项目已经有 `AGENTS.md`，助手应保留原内容，只追加缺失的多 Agent 规则。
- 如果当前环境不支持真实 thread、subagent 或跨会话消息，助手会在同一会话中用明确角色切换模拟多 Agent 协作。
- 如果当前环境没有 Superpowers 或类似增强能力，助手会自动降级为普通本地多 Agent 流程。
