# Al Brooks 价格行为交易系统

本仓库把 Al Brooks 价格行为证据融合为一套从市场事实、结构和目标路径运行到交易计划、执行、管理与复盘的完整系统。它不是形态信号清单、预设策略集合、收益证明或针对某个市场的交易建议。

## 两个入口

| 目标 | 入口 |
| --- | --- |
| 运行完整交易系统 | [价格行为交易系统](trading_system/README.md)，从[交易系统总流程](trading_system/overall_flow.md)开始 |
| 核对来源、课程证据、重复和冲突 | [参考资料](reference/README.md) |

## 权威关系

```text
Reference 提供证据、来源和冲突
           ↓
Trading System 选择、归并和条件化
           ↓
Market Context + Location + Primary Test
→ Bull / Bear / Pending Opportunity Set
→ 条件概率 → Entry / Invalidation / Stop → 交易方程
→ 执行、持续更新、管理与复盘
```

| 目录 | 唯一职责 |
| --- | --- |
| [trading_system](trading_system/README.md) | 唯一运行权威；定义完整交易语义和闭环 |
| [reference](reference/README.md) | 保存正式来源、逐讲证据、派生索引、重复与冲突，不直接许可交易 |

## 系统原则

- 系统不选择某个预设策略。所有方向都经过同一套 Market Context、Location、Current Structural Test、双向路径、条件概率和风险方程。
- Pattern、Market Cycle、Context、H/L、Wedge、Double Test、Flag、MTR 等是流程中的派生描述，不是独立交易路由。
- 每个现实 Primary Test 都考虑 Bull、Bear 与 Pending 结果；系统比较双方当前完整风险交换，不按理由数量或裸概率选择方向。
- Target 是概率和 Entry 之前的上游对象；没有明确目标事件，不匹配概率，也不建立交易。
- 同一来源事实的多个名称只形成一份证据；不同周期、结构来源或后续反应才可能增加信息。
- 系统必须能够独立运行；Reference 用于核验，不是临场缺失语义的补丁。
- 看不清结构边界、目标事件、路径失效或真实风险时，正确输出是等待或不交易。

课程证据怎样进入系统见[01–52 课程与交易系统对齐](reference/course/course_to_system_alignment.md)，数字、数学和来源表述的限制见[边界与冲突](reference/course/boundaries_and_conflicts.md)。
