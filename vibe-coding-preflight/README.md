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
- 检查 Git 状态。
- 完成后询问是否进入编码阶段。

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
