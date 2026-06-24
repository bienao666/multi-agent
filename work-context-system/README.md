# Work Context System

这个目录提供一份“AI 工作上下文系统”模板：

- `work-context-system.md`

它用于把 AI 从临时写作工具升级成更懂你工作场景的助手。核心是建立四类长期可复用资料：

- 人物库
- 项目库
- 事件库
- 产出模板库

## 适合场景

- 经常写周报、汇报、复盘、方案、会议纪要。
- 希望 AI 知道材料是写给谁看的。
- 希望 AI 根据不同领导、客户、同事的关注点调整表达。
- 希望把会议纪要、聊天记录、邮件往来沉淀成可复用上下文。
- 希望构建自己的“个人复利工作系统”。

## 推荐目录结构

把 `work-context-system.md` 喂给 AI 后，可以让它在目标项目或个人知识库中创建：

```text
.work-context/
  people/
  projects/
  events/
  templates/
  outputs/
```

## 使用方式

在任意项目或知识库中打开 AI 编程助手或通用 AI 助手，然后发送：

```text
请完整读取并执行下面这份 Work Context System 文档。
在当前目录中初始化 .work-context/，并创建 people、projects、events、templates、outputs 子目录。
```

接着把 `work-context-system.md` 的全文粘贴进去。

## 常用工作流

```text
会议纪要 / 聊天记录 / 邮件 / 项目材料
  -> 提取人物画像
  -> 更新项目库和事件库
  -> 选择产出模板
  -> 生成标准版
  -> 按不同读者画像改写
  -> 模拟追问和应对
```

## 和多 Agent 模板的关系

这个目录不负责创建 Manager / Builder / Reviewer 多 Agent 协作机制。

它更像一个“工作上下文资料库”。你可以单独使用，也可以和其他多 Agent 模板组合：

- 多 Agent 模板负责组织 AI 怎么分工。
- Work Context System 负责提供 AI 工作所需的长期上下文。

组合使用时，可以让 Manager 在任务开始前读取 `.work-context/`，再决定如何分配任务。

