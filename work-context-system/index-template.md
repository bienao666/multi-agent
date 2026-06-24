# Work Context Index Template

把这个模板复制到目标项目或知识库的：

```text
.work-context/index.md
```

这个索引是 AI 读取 `.work-context/` 的入口。每次任务开始时，先读索引，再按需读取相关人物、项目、事件和模板。

## 当前重点项目

| 项目 | 文件 | 状态 | 当前重点 | 相关人物 | 最近事件 |
| --- | --- | --- | --- | --- | --- |
| 示例项目 | `projects/example-project.md` | 进行中 | 明确下一步方案 | `people/leader-direct.md` | `events/2026-01-01-example-meeting.md` |

## 常用人物画像

| 人物角色 | 文件 | 关注点 | 适合场景 |
| --- | --- | --- | --- |
| 直属领导 | `people/leader-direct.md` | 结果、风险、资源、决策点 | 向上汇报、方案审批 |
| 客户决策人 | `people/client-decision-maker.md` | 价值、确定性、进度、风险控制 | 客户汇报、方案沟通 |
| 产品协作方 | `people/teammate-product.md` | 需求边界、用户价值、排期影响 | 需求评审、产品方案 |

## 常用产出模板

| 模板 | 文件 | 用途 |
| --- | --- | --- |
| 领导汇报 | `templates/leader-report.md` | 向上汇报进展、风险和决策点 |
| 技术差异分析 | `templates/tech-diff-report.md` | 对比新旧逻辑或方案差异 |
| 会议纪要 | `templates/meeting-minutes.md` | 沉淀会议事实、结论和后续动作 |
| 追问模拟 | `templates/question-simulation.md` | 模拟不同对象可能追问的问题 |

## 最近事件

| 日期 | 事件 | 文件 | 相关项目 | 后续动作 |
| --- | --- | --- | --- | --- |
| YYYY-MM-DD | 示例会议 | `events/YYYY-MM-DD-example.md` | 示例项目 | 更新项目方案 |

## AI 读取顺序

生成汇报、方案、复盘或分析时，按以下顺序读取：

1. `.work-context/index.md`
2. 相关人物画像
3. 相关项目文件
4. 相关事件文件
5. 相关产出模板
6. 必要时读取历史输出

## 维护规则

- 新增人物画像后，更新“常用人物画像”表。
- 新增项目后，更新“当前重点项目”表。
- 重要会议、沟通、决策后，新增事件并更新“最近事件”表。
- 新增常用模板后，更新“常用产出模板”表。

