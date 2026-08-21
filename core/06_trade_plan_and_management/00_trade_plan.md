# 从 Setup 到交易计划

> **状态：Core / Definition**
>
> 本文是 Trade Plan schema 的权威定义页，负责规定一笔交易实例必须包含的组成及其一致性；它本身不生成具体策略计划。

本页的固定字段、版本记录和管理分支是仓库为一致操作与复盘建立的综合 schema / 仓库基线，不是 Brooks 官方给出的固定字段表。字段中的价格行为、风险与管理关系仍分别由相关来源支持。

## Trade Plan 的定义

Trade Plan 是围绕一个 Setup 固化的完整交易方案。它把交易命题、实际承担的风险和成交后管理放在同一组假设中，使入场前的判断和事后复盘可以核对。

一份完整计划至少包含：

| 组成 | 必须回答的问题 |
| --- | --- |
| Premise | 当前 Setup 押注什么价格行为，哪些 Context 支持它？ |
| Supporting reasons | 至少两个相互补充的理由是什么，是否存在同义标签重复计票？ |
| Opposing evidence | 反方当前最有力、且与本计划相关的可观察事实是什么？ |
| Update condition | 哪个新事实会增强、削弱或否定当前判断？ |
| Entry | 哪个可观察条件触发订单，预计实际成交怎样处理？ |
| Execution / order lifecycle | 采用什么订单方向、类型和价格规则；何时生效、过期或取消；部分成交、回执不明和 bracket 激活怎样处理？ |
| Invalidation | 哪些新价格事实说明原命题不再成立？ |
| Active protective stop | 当前实际保护单在哪里，为什么该位置容许正常波动却限制错误判断？ |
| Profit target | 准备在哪个现实区域或价格兑现，依据是什么？ |
| Outcome criterion | 什么图表或账户事实算 target / stop 先到、部分结果或顺序不明？ |
| Position size | 按 entry 到 protective stop 的真实风险，可以承担多少数量？ |
| Management | 按 scalp 还是 swing，怎样处理正常回调、部分退出、时间和新证据？ |
| Trader's Equation | 这组概率、risk、reward 与成本是否值得承担？ |

Invalidation 与 active protective stop 相关但不等同：前者是原 premise 被新证据否定，后者是当前真实在场、用于限制这份计划风险的保护订单。交易者可以在该 stop 触发前，基于可观察的 premise 变化主动退出。

`Opposing evidence` 不要求为了形式对称而编造反向交易，也不等于 premise 已失效；它负责记录当前最可能压缩概率、目标空间或持有时间的事实。`Update condition` 则把“准备应对任何结果”落到可观察条件：哪些新事实只会削弱优势，哪些足以触发 Invalidation，哪些会要求等待而不是入场。若反方事实已经使原方程不成立，候选应回到 Setup 的 WAIT / REJECT，而不是靠较远 stop 继续维持 TRADE 标签。

`Execution / order lifecycle` 不在 Core 中假定统一的经纪商行为，但必须让计划能够区分订单意图、图表触发和账户事实。Limit touch / cross、actual fill、partial fill 与保护订单状态的边界见[限价单市场](../03_acceptance_and_order_logic/02_limit_order_market.md#touchcross-与-actual-fill)和[Stop 入场与保护性 Stop](../03_acceptance_and_order_logic/00_stop_entry_vs_protective_stop.md#实际保护与成交边界)。`Outcome criterion` 必须写明 target 是价格还是区域、图表触及是否足够、实际成交数量怎样计入结果，以及路径先后无法观察时怎样标记不确定结果。

Supporting reasons 的维度、独立性与候选状态见[什么是 Setup](../05_setups/00_what_is_a_setup.md#two-reasons-与证据汇合)。这三个字段是仓库为审计证据汇合和概率更新增加的 schema，不宣称是 Brooks 给出的固定表格。

若交易架构还使用更远的 `catastrophe backup`，必须把它作为独立可选字段记录，并明确极端情况下从 entry 到该订单的最大损失、相应仓位上限以及何时撤换。它不等于 active protective stop，也不能被用来缩小计划表中的真实最坏风险。所谓 price-action stop 必须落到前述某个明确订单或主动退出规则，不能同时指代两个不同价位。

## 一致性约束

- Entry、execution / order lifecycle、active protective stop、target、outcome criterion、概率和仓位必须来自同一版本，不能拼接不同方案中最有利的输入；若另有 catastrophe backup，也必须计入最坏损失与仓位约束。
- 在承担风险前，entry / trigger、订单类型或有效期、stop、target、outcome criterion、数量、管理周期或管理方式的任何改变都表示计划版本已经改变，必须同时重算风险距离、仓位和 Trader's Equation。
- Profit target 使用实际准备交易的价格，不使用与当前 Setup 无关的远端投射来制造理想 reward/risk。
- `original_target` 是入场时的审计原值，成交后不得因结果而回填、重选 measured-move 端点或伪装成另一版本。新证据可以使目标不再现实，也可以支持按预写分支调整管理；此时另记 `current_management_target` 与 `actual_exit`、时间和证据，不覆盖原值，并重新检查剩余仓位的 Trader's Equation。
- Scalp 与 swing 对回调、持有时间和目标空间的容忍不同；入场后不能只因盈亏情绪随意切换。
- Catastrophe backup 只能作为另行预算的灾难性后备，不能替代 active protective stop、premise 判断和主动管理。

Protective stop 的订单用途见 [Stop Entry 和 Protective Stop](../03_acceptance_and_order_logic/00_stop_entry_vs_protective_stop.md)，目标构造见[支撑阻力与目标](../02_context/01_support_resistance_targets.md)，仓位数学见[概率、风险和回报](../00_method/01_probability_risk_reward.md)。

## Stop 调整与保本

### Trailing Stop

Trailing stop 是随新价格结构逐步向降低开放风险方向移动的 active protective stop。多头只能把它向上调整，空头只能向下调整；对同一受保护数量，只有确认替换订单已经生效后，新价位才成为当前实际保护，不能在撤旧与挂新之间留下无保护空档。若把 stop 向扩大风险方向移动，那是放宽保护或建立新计划版本，不属于 trailing。

可用锚点包括新强 breakout 建立的 major higher low / lower high、完整走势腿或其他仍能容纳当前管理周期正常波动的结构。同一图表可以有紧、宽等多个一致方案；任意次要 swing、每根盈利 K 线或固定点数都不要求机械追踪。调整仍须结合原 Setup、剩余仓位、target 和 premise，不能因为已经盈利就把 stop 塞进正常回调。

### Breakeven Stop

Breakeven stop 是把 active protective stop 调整到计划 entry 或整仓加权平均 entry 附近的特殊管理选择。它可以降低名义价格风险和心理压力，却不保证账户结果真正为零：佣金、滑点、跳空、部分成交和多层仓位都会改变实际结果；scale-in 的 breakeven 还必须使用[加权平均 entry](02_scaling_in_out.md#整仓均价与总风险)，不能机械采用第一笔 entry 或两个价格的中点。

价格到达原计划允许减仓的 target、新 higher low / lower high 或其他 price-action 结构，可能支持向保护方向调整 stop。任何调整仍须服从原 Setup、当前 premise、剩余仓位和管理方式；Stop 放得过近，可能在正常回踩中提前结束本来合理的交易。

## 三层退出保护

每笔实际持仓至少要能区分三种保护，它们不是三个互相替代的 stop price：

1. **Active protective stop**：实际在场的最后保护，用于在主动判断、连接或执行失败时限制最坏风险。
2. **Premise invalidation / 合理反向结构**：新的价格事实已经使原交易命题不再成立，可以在最远 stop 触发前主动退出；它必须由计划中可观察的条件定义，不能只写“感觉不对”。
3. **强反向动量**：即使还没有漂亮的反转形态，一根异常强反向趋势 K 线、数根连续无重叠的反向 K 线或 Always In 明确翻转，也可能已经足以否定原 premise；具体强度仍由 Context 和原管理周期判断。

这三层共同防止正常亏损变成大额亏损：硬 stop 防止失控，结构失效允许更早承认错误，强反向动量避免为了等待完美信号而忽视市场已经改变。普通小反向 K 线和正常 swing pullback 不自动触发第二或第三层。

主动退出后，若反转失败、原方向重新获得接受，交易者可以重新入场；这必须建立新的 observable trigger、stop、target、仓位和 Trader's Equation，并记录为新的计划版本。重新入场的可能性不能反向证明先前退出错误，也不能成为取消当前保护的理由。

## 成交后的更新

计划不是静态剧本，因为 premise 会随新事实接受复核；计划也不是允许事后重写输入的草稿。成交后继续观察 entry bar、follow-through、关键位置是否守住、反方是否获得强突破，以及原目标是否仍现实。目标不再现实必须进入记录并按入场前选择的管理分支处理，但不会把更近或更远的价位追认为原 target。

[接受、失望与失败证据](../03_acceptance_and_order_logic/01_acceptance_and_failure.md)区分正常波动、entry disappointment、premise 变化和 trade failure；[Scalp 与 Swing](01_scalp_vs_swing.md)界定持有方式，[加仓与减仓](02_scaling_in_out.md)界定数量变化。正常 pullback 不自动否定交易；强反向证据必须记录并按已选管理分支解释，不能为迎合结果临场切换分支。

标准策略计划必须在入场前写出可观察的 premise 变化及对应主动退出；结构保护止损和固定目标是订单基线，不表示可以忽略这些变化。任何计划都不能用“固定管理”忽略回执不明、保护不足、连接异常或真实仓位风险。

## 相关来源

相关来源见 [`reference/official_sources.md`](../../reference/official_sources.md) 中的 `SRC-GLOSSARY`、`SRC-MANUAL`、`SRC-STOP-ORDERS`、`SRC-POSITION-SIZE`、`SRC-GOOD-TRADE-2017`、`SRC-HOLDING-WIDE-STOPS`、`SRC-COURSE-01-36`（课程 30A–36B）与 `SRC-COURSE-37-52`（课程 37A–37B、41A–41D、51A–52B）。
