# 价格行为交易系统

> **状态：Trading System / Index**

本目录是仓库唯一的交易运行权威。系统从可观察的市场与账户事实出发，以 Safety Gate 和 Event Gate 选择增量更新或完整重构，持续更新 `Frame → Environment → Location → Price Action Now → Active Test + Views → Paths`，再依次通过 Market Gate、Risk Plan、Execution Gate 和 Action；入场前后运行同一认知循环，并在订单、持仓、退出和复盘中保持事实与风险闭环。

系统不由预设策略、Setup 家族或形态信号驱动。Trend Continuation、Range Fade、MTR 等名称只能在需要时概括已经形成的价格路径，不能选择另一套运行逻辑。每一笔交易都使用同一个闭环：

```text
价格与账户事实
→ Frame、Environment 与 Location
→ Price Action Now：Gap、Pressure、Control、Follow-through 等事实
→ Active Test + 同源 Views
→ 向上 / 向下 / Pending Opportunity Set
→ 当前条件匹配各自目标概率
→ Entry / Invalidation / Stop 表达该路径
→ Reward / Risk / Cost / Time 检查
→ 执行 / 等待 / 不交易
→ 持仓中持续更新所选与对手路径
→ 退出、结果与复盘
```

## 文件

1. [交易系统总流程](overall_flow.md)：唯一运行入口；规定 `Frame → Environment → Location → Price Action Now → Active Test + Views → Paths → Market Gate → Risk Plan → Execution Gate → Action` 的直接运行顺序，以及 Safety / Event Gates、状态分派与闭环。
2. [市场结构与结果路径](market_structure_and_paths.md)：定义 Market Read 各观察对象、Active Test、双向目标和 Market Paths，并把 Pattern 放回同源视图。
3. [交易决策与计划](decision_and_plan.md)：独立评价双向路径，实例化当前适用规则，以 Entry、Invalidation、Stop、Target、仓位和管理构造交易方程，并拥有 Trade Plan 与 Decision Record 格式。
4. [执行、持仓与复盘](execution_management_and_review.md)：处理订单、成交、实际保护、持仓中的持续路径更新、退出、执行事件记录、结果判定和行为纪律。
5. [条件规则台账](conditional_rules_registry.md)：保存可匹配规则模板、背景、替代顺序和隔离项；模板完成当前目标、周期、horizon 与时点实例化后才可运行。
6. [完整流程演练](worked_examples.md)：用 5 分钟图上的宽通道第三推、区间下沿 scalp 和 ii / ioi 压缩演示同一条运行链，不新增规则。

## 权威边界

| 位置 | 职责 | 是否直接许可交易 |
| --- | --- | --- |
| `trading_system/` | 完整运行语义、条件规则与实际闭环 | 是，只能由完整流程得出 |
| `reference/` | 正式来源、课程证据、重复、冲突和派生索引 | 否，只用于核验和追溯 |

系统必须在不打开 `reference/` 的情况下完成一次市场判断、交易计划、执行和复盘；重要关系与概率则应能回到 `reference/` 核验。新说法必须先回到 Reference 查明依据、条件与冲突，不能因旧笔记或单个案例已经写出就自动吸收。

## 使用层级

`trading_system/` 同时提供三种不同接口，不得将它们混成一套高频填表流程：

1. **系统知识与内部模型**：保持完整的事实、状态、路径、决策、风险与复盘契约；它规定交易者必须正确理解什么，不规定每次都要写什么。
2. **实盘检查清单**：初次看图或 Reframe 按“Frame → Environment → Location → Price Action Now → Active Test + Views → Paths”完整扫描；普通新 K 线只问 Location / Price Action Now、Environment / Active Test 和 Paths / Gates / Action 是否改变，再叠加当前订单或持仓状态清单。
3. **必要记录**：只在新建或实质修改计划、改变风险、发生成交/退出/异常，或交易与路径结束时，保存最小充分信息。

具体负担上限、状态化检查清单和事件—记录矩阵见[交易系统总流程](overall_flow.md#三层使用接口)。

## 使用原则

- 结构先生成目标事件，概率只属于条件、目标、周期、时间范围和判断时点完全明确的路径。
- 规则台账中的模板和背景数字不能直接进入方程；当前 Rule Match 必须补齐目标、周期、horizon 和判断时点，并检查更具体条件是否已经替代旧模板。
- 每个现实 Primary Test 都考虑向上、向下与 Pending 结果；双向考虑不表示概率机械互补或必须同时交易。
- 初始化和 Reframe Event 完整重构市场解释；普通 Observation Event 只更新相对上次判断的新增事实。
- 普通新 K 线若没有改变结构、路径、风险或动作，只继续观察，不产生人工记录。
- 不要把“交易者必须检查的内容”都转化为“交易者必须书面记录的内容”。
- Pattern 是结构、次序、空间或角色的压缩描述，不是系统路由，也不提供交易许可。
- 同一事实的多个名称只形成一份证据；不同周期、结构来源或后续反应才可能增加信息。
- 一个 Trade Plan 只能选择一个 Primary Test 下、一条明确周期和时间范围的 Market Path；其他测试和路径保留为反方、背景或替代事实。
- 每个相关事件可以增强、保持、削弱、完成、失效或替代路径；认知更新不自动产生交易动作。
- Reference 中不能改变结构、目标、路径、概率、风险、执行或复盘的材料，不进入运行系统。
- 看不清必要边界、目标事件或路径失效条件时，正确结果是等待或不交易。
