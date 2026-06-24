# Vibe Coding Preflight

这个目录提供一份可复制到新项目 AI 编程助手会话中的开发前准备模板：

- `vibe-coding-preflight.md`

它用于在写代码前完成项目整理、MVP 定义、里程碑拆分、基础文档和 Git 检查，避免一上来就让 AI 写代码导致项目变乱。

## 适合场景

- 新手用 AI 做网页、工具、小产品。
- 还没明确 MVP，就想开始写代码。
- 项目还没有 README、docs 或 Git 仓库。
- 希望 AI 在开发前先按 Manager / Builder / Reviewer 的统一角色体系完成准备。
- 希望每个新项目都有统一的开发前准备流程。

## 使用方式

在任意新项目目录中打开 AI 编程助手或 Agent 会话，然后发送：

```text
请完整读取并执行下面这份 Vibe Coding Preflight 文档。
先不要写业务代码，先完成开发前准备。
```

接着把 `vibe-coding-preflight.md` 的全文粘贴进去。

AI 助手会自动：

- 扫描当前目录结构。
- 创建或更新 `README.md`。
- 创建或更新 `docs/`。
- 明确产品目标。
- 定义 MVP。
- 拆分里程碑。
- 定义成功标准。
- 建立验证计划。
- 建立执行循环。
- 建立初始架构说明。
- 定义后续 AI 协作角色，并与 `multi-agent-superpowers` 的 Manager / Builder / Reviewer 模式保持一致。
- 创建 `docs/prompt-version.md`，初始版本为 `v0.1.0`，后续规则变动自动递增版本号。
- 在准备工作需要时自动查询合适的插件、skill、MCP tool 或项目本地工具辅助。
- 检查 Git 状态。
- 完成后询问是否进入编码阶段。

## Token 消耗优化

新版默认采用“骨架先行、细节按需补齐”的方式运行：

- 先创建文档骨架和关键结论，不把所有文档全文输出到对话里。
- 扫描项目时优先看目录、README、配置文件和 Git 状态，不全量读取源码。
- 已有长文档只读取相关小节。
- Preflight Summary 默认输出精简摘要。
- 只有准备进入编码、高风险决策或用户要求详细版时，才展开完整细节。

## 按需能力发现

Preflight 过程中，如果需要识别技术栈、处理附件、生成结构化文档、做技术选型、隐私脱敏、浏览器检查或设计稿分析，AI 会自动查询合适的插件、skill、MCP tool 或项目本地工具。

查询原则：

- 只查当前准备步骤相关能力。
- 找到合适能力时说明能力名称、使用原因和降级方案。
- 没有合适能力时继续使用本地 Markdown 流程。
- 不为了调用能力而提前写业务代码。

## 版本号规则

初始化后会生成 `docs/prompt-version.md`：

- 初始版本：`v0.1.0`
- 文案或说明补充：递增 patch，例如 `v0.1.1`
- 新增可选文档、检查项或准备步骤：递增 minor，例如 `v0.2.0`
- 改变默认流程、删除准备步骤或改变进入编码条件：递增 major，例如 `v1.0.0`

只有修改 Preflight 规则、`docs/` 准备结构或 README 入口时才递增版本；普通业务开发任务不递增。

## 生成的文档结构

```text
docs/
  product.md
  mvp.md
  milestones.md
  success-criteria.md
  validation-plan.md
  execution-loop.md
  architecture.md
  agent-roles.md
  prompt-version.md
  decisions.md
  task-log.md
README.md
```

## 注意事项

- 这个模板默认不写业务代码。
- 如果项目没有 Git 仓库，AI 应先询问是否执行 `git init`。
- AI 不应自动提交代码。
- AI 不应自动创建远程仓库。
- 只有产品目标、MVP、M1 里程碑、成功标准、验证计划、执行循环和 Git 状态明确后，才建议进入编码阶段。
