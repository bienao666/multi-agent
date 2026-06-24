# Work Context System

懂项目、懂人、懂场景、能预判反馈的工作替身

核心思想：

```text
人物库 + 项目库 + 事件库 + 产出模板库
  -> 标准版产出
  -> 按读者画像改写
  -> 模拟反馈和追问
  -> 形成可复用的个人复利工作系统
```

## 目录结构

建议在目标项目或个人知识库中创建：

```text
.work-context/
  index.md
  version.md
  people/
  projects/
  events/
  templates/
  outputs/
```

说明：

- `index.md`：上下文入口索引，记录重点项目、常用人物、常用模板和最近事件。
- `version.md`：记录 Work Context System 在当前项目中的 Prompt 版本和变更历史。
- `people/`：人物画像，记录领导、客户、同事、协作方的关注点和表达偏好。
- `projects/`：项目库，记录项目背景、目标、进展、关键风险和当前待办。
- `events/`：事件库，记录会议、沟通、决策、冲突、变更和历史上下文。
- `templates/`：产出模板，定义汇报、方案、复盘、技术分析等固定格式。
- `outputs/`：可选，保存 AI 生成后的最终产出或历史版本。

初始化时可以参考：

- `index-template.md`
- `privacy-and-sanitization.md`
- `operating-playbook.md`
- `templates/question-simulation.md`

## 版本管理

本 Work Context System 在目标项目中落地后，必须维护版本号。

- 首次初始化时创建 `.work-context/version.md`，版本号写为 `v0.1.0`。
- 如果 `.work-context/version.md` 已存在，不要覆盖历史记录；读取当前版本后按变更级别递增。
- 仅文案、错别字、说明补充，不改变行为：递增 patch，例如 `v0.1.0 -> v0.1.1`。
- 新增可选模板、目录、字段、维护流程或兼容规则，但不破坏旧行为：递增 minor，例如 `v0.1.0 -> v0.2.0`。
- 改变默认目录结构、删除能力、改变隐私规则或核心工作流：递增 major，例如 `v0.1.0 -> v1.0.0`。
- 每次版本变化都必须记录日期、版本号、变更摘要、变更级别和是否需要人工确认。
- 如果只是新增人物、项目、事件或产出内容，没有修改系统规则和模板结构，不要递增版本号。

`.work-context/version.md` 初始内容：

```md
# Work Context Version

Current Version: v0.1.0

## Versioning Rules

- patch：文案、说明、错别字、示例补充，不改变行为。
- minor：新增可选模板、目录、字段、维护流程或兼容规则，不破坏旧行为。
- major：改变默认目录结构、删除能力、改变隐私规则或核心工作流。

## Changelog

| Version | Date | Change Type | Summary | Requires Manual Review |
| --- | --- | --- | --- | --- |
| v0.1.0 | YYYY-MM-DD | initial | 初始化 Work Context System。 | No |
```

## 人物库

路径示例：

```text
.work-context/people/leader-direct.md
.work-context/people/client-decision-maker.md
.work-context/people/teammate-product.md
```

模板：

```md
# 人物画像：<姓名或称呼>

## 角色

例如：直属领导、客户决策人、产品负责人、技术负责人、协作方。

## 与我的关系

说明汇报、协作、审批、交付或利益关系。

## 关注点

- 关注点 1
- 关注点 2
- 关注点 3

## 表达偏好

- 喜欢先结论后过程
- 喜欢数字和对比
- 喜欢风险和预案
- 不喜欢长背景

## 忌讳点

- 只讲过程不讲结果
- 没有明确下一步
- 没有资源需求
- 没有风险预案

## 常问问题

- 这个事情值不值得做？
- 需要多少资源？
- 什么时候能看到结果？
- 风险在哪里？

## 历史反馈

- 日期：反馈内容
- 日期：反馈内容
```

## 项目库

路径示例：

```text
.work-context/projects/subscribe-system.md
.work-context/projects/ai-agent-template.md
```

模板：

```md
# 项目：<项目名称>

## 背景

为什么做这个项目。

## 目标

要解决什么问题，成功标准是什么。

## 当前进展

已经完成什么，正在做什么，卡在哪里。

## 关键模块

- 模块 1
- 模块 2
- 模块 3

## 关键风险

- 风险 1
- 风险 2
- 风险 3

## 相关人物

- 人物 A：角色和关注点
- 人物 B：角色和关注点

## 当前待办

- 待办 1
- 待办 2
```

## 事件库

路径示例：

```text
.work-context/events/2026-06-24-subscribe-review.md
```

模板：

```md
# 事件：<事件名称>

## 时间

YYYY-MM-DD

## 参与人

我、领导、客户、产品、研发等。

## 发生了什么

用简洁语言记录事实。

## 关键结论

- 结论 1
- 结论 2
- 结论 3

## 分歧或风险

- 分歧 1
- 风险 1

## 相关人物态度

- 人物 A：关注什么，支持还是反对
- 人物 B：关注什么，支持还是反对

## 后续动作

- 动作 1
- 动作 2
```

## 产出模板库

路径示例：

```text
.work-context/templates/leader-report.md
.work-context/templates/tech-diff-report.md
.work-context/templates/review-summary.md
.work-context/templates/meeting-minutes.md
```

### 技术差异分析模板

```md
# 技术差异分析

## 结论先行

一句话说明是否有变化，以及是否有风险。

## 对比范围

- Controller
- Service
- Mapper / SQL
- 分页
- 筛选
- 排序
- 返回结构

## 差异明细

| 层级 | 旧逻辑 | 新逻辑 | 是否变化 | 影响 |
| --- | --- | --- | --- | --- |

## 风险点

- 风险 1
- 风险 2

## 建议

只读分析 / 可修改 / 需要确认。

## 可能追问

| 问题 | 建议回答 |
| --- | --- |
```

### 领导汇报模板

```md
# 汇报：<主题>

## 一句话结论

先给结论。

## 当前状态

说明进展、结果和关键数字。

## 影响

说明对业务、项目、资源、排期的影响。

## 风险与预案

- 风险：
- 预案：

## 需要决策

需要领导拍板或提供资源的事项。

## 下一步

明确后续动作和时间。
```

## 推荐工作流

```text
收集材料
  -> 放入事件库 / 项目库 / 人物库
  -> 选择产出模板
  -> 让 AI 生成标准版
  -> 指定读者画像
  -> 让 AI 改写成对应版本
  -> 模拟对方追问
  -> 补充应对策略
```

## 常用提示词

### 初始化

```text
请根据这份 Work Context System 文档，在当前项目中创建 .work-context/ 目录，并初始化 people、projects、events、templates、outputs 五个子目录。
同时创建 .work-context/version.md，初始版本号为 v0.1.0；后续如果修改系统规则或模板结构，按版本管理规则自动递增版本号。
```

### 从材料提取人物画像

```text
请从下面的会议纪要、聊天记录或邮件中，提取相关人物画像。
输出到 .work-context/people/，每个人一个 Markdown 文件。
重点提取：角色、关注点、表达偏好、忌讳点、常问问题、历史反馈。
```

### 从会议纪要生成事件

```text
请把下面的会议纪要整理为事件记录。
输出格式参考 .work-context/events/ 模板。
重点记录：发生了什么、关键结论、分歧或风险、相关人物态度、后续动作。
```

### 生成面向某人的汇报

```text
请读取：
- .work-context/people/<人物画像>.md
- .work-context/projects/<项目>.md
- .work-context/events/<事件>.md
- .work-context/templates/<模板>.md

生成一份面向该人物的汇报。
要求：
1. 按该人物关注点调整重点。
2. 使用该人物偏好的表达方式。
3. 避开忌讳点。
4. 最后模拟对方可能追问的 5 个问题，并给出建议回答。
```

### 生成标准版再改写

```text
请先基于项目库和事件库生成一份标准版报告。
然后分别基于以下人物画像改写：
- <人物 A>
- <人物 B>
- <人物 C>

输出三版差异，并说明每一版为什么这样调整。
```

## 使用原则

- 不要让 AI 凭空猜人物画像，要尽量来自会议纪要、聊天记录、邮件和历史反馈。
- 敏感信息进入 AI 前应先脱敏。
- 每次任务开始时先读 `.work-context/index.md`，再按需读取相关文件，不要默认读取整个目录。
- 人物画像不是评价人，而是记录工作协作中的表达偏好和决策关注点。
- 每次重要会议或反馈后，更新事件库和人物库。
- 模板越稳定，AI 产出越稳定。
- 先生成标准版，再按对象改写，效果通常更好。
- 重要材料生成后，使用追问模拟模板预判对方可能提出的问题。
