# Core → Strategy 思想覆盖表

> **状态：Strategy / Index（思想覆盖核验工具）**
>
> 本表先按 `core/README.md` 的 Definition 权威注册表核验概念入口，再单独复核全部 Core / Application 命题和高风险 Reference 边界。它回答“某项 Core 思想在策略层扮演什么角色、由哪里承接”，不要求每个术语各有一页策略。

## 判定规则

Core 思想进入策略层只有四种合法角色：

| 角色 | 是否需要独立策略页 | 判定标准 |
| --- | --- | --- |
| 交易母命题 | 必须有通用承接 | 会独立改变 premise、方向、触发、失效或直接预期 |
| 命名子型 | 仅在产生更具体交易边界时需要 | 相比母命题收紧 Context、触发、失效或目标 |
| 证据输入 / 状态约束 | 不需要 | 只描述看到什么、当前状态或怎样更新判断，不能独立提供交易许可 |
| Trade Plan / 管理约束 | 不需要 | 在候选选定后约束 entry、stop、target、数量、持有方式或风险 |

若某个新概念只改变形态名称而不改变交易命题，不新增策略页；若 Core 新增了不能由现有母命题解释的 premise，必须先补通用承接，再决定是否增加命名子型。

## 方法、状态与 Context

| Core 权威思想 | 策略层角色 | 当前落点 | 覆盖结论 |
| --- | --- | --- | --- |
| [Brooks 方法主线 / Price Action](../core/00_method/00_al_brooks_thesis.md) | 证据输入 | [选择链](README.md#选择链) | 通过价格事实而非外部叙事选择候选；证据按当前周期与状态保持、削弱、失效或重置，不独立成策略 |
| [Trader's Equation / Probability Language](../core/00_method/01_probability_risk_reward.md) | 管理约束 | [执行清单](README.md#执行清单从策略页到-trade-plan)、覆盖矩阵 PSEL | 所有承担风险决定统一检查 |
| [Market Cycle / Reversal / Minor Reversal](../core/01_market_cycle/00_market_cycle.md) | 状态约束 + 家族路由 | [趋势](trend/README.md)、[区间](range/README.md)、[反转](reversal/README.md)、[覆盖矩阵](coverage_matrix.md) | 基础状态与 minor/MTR 边界均有路由 |
| [Trend / Channel / Pullback / Leg](../core/01_market_cycle/01_trends_and_channels.md) | 状态约束 + 趋势母命题 | [普通趋势回调延续](trend/pullback_continuation.md)及趋势子型 | 通用回调由兜底承接，命名结构用专页收紧 |
| [Trading Range](../core/01_market_cycle/02_trading_ranges.md) | 状态约束 + fade 母命题 | [边缘确认 fade](range/edge_fade_confirmed.md)及区间子型 | 边缘回归、突破成功、中部/TTR 回避均有落点 |
| [Breakout Event / Test / Mode / BTC-STC](../core/01_market_cycle/03_breakouts_and_breakout_mode.md) | 状态约束 + 突破母命题/子型 | [双向突破模式](breakout/breakout_mode.md)、[BTC/STC](breakout/buy_sell_the_close.md)、[突破回踩](breakout/breakout_pullback_test.md) | 通用 BOM 不再局限于压缩结构 |
| [Climax / Transition](../core/01_market_cycle/04_climax_and_transition.md) | 状态约束 + minor 子型 | [高潮后修正](reversal/climax_correction.md)、矩阵 WATCH/transition 行 | 高潮式推进本身不提供逆势许可 |
| [Context / Location / Control / Always In](../core/02_context/00_context_location_control.md) | 证据输入 | [选择链](README.md#选择链)及各策略情景判定 | 所有策略先检查位置、控制与空间 |
| [Support / Resistance / Target / Test / Confluence](../core/02_context/01_support_resistance_targets.md) | 证据输入 + 管理约束 | 各页“适用情景”“目标与管理”、[量度目标构造](breakout/measured_move_breakout.md) | Test 需要 reaction / follow-through 才能解释结果；汇合增加位置理由但不独立生成 entry，同源对象不重复计票 |
| [Timeframe / Session / Opening](../core/02_context/02_time_and_timeframes.md) | 证据输入 + 覆盖层 | [时段覆盖层](session/README.md) | 多周期、opening 与尾盘只改变候选/时间约束 |

## 订单、接受与形态语言

| Core 权威思想 | 策略层角色 | 当前落点 | 覆盖结论 |
| --- | --- | --- | --- |
| [Stop Entry / Protective Stop](../core/03_acceptance_and_order_logic/00_stop_entry_vs_protective_stop.md) | 管理约束 | [跨情景基线](README.md#跨情景基线全部链接-core不在此重复定义)、各策略触发与 stop 锚点 | 入场触发与持仓保护保持分离 |
| [Acceptance / Failure](../core/03_acceptance_and_order_logic/01_acceptance_and_failure.md) | 证据输入 + premise 更新 | 各策略失效段、[覆盖矩阵](coverage_matrix.md) | Follow-through、重新接受、失望与失败参与候选更新 |
| [Limit Entry / LOM / Fade / Countertrend](../core/03_acceptance_and_order_logic/02_limit_order_market.md) | 证据输入 + 区间子型 | [限价探针与预设加仓](range/edge_fade_limit_scalein.md)、[宽通道参与区](trend/broad_channel_buy_zone.md) | 限价行为服从上层 premise，不独立建家族 |
| [Second Signal / Second Entry / Trap](../core/03_acceptance_and_order_logic/03_second_entries_and_traps.md) | 触发顺序 | [趋势第二次恢复](trend/second_signal_continuation.md)、[区间第二次信号](range/edge_second_signal.md)、[Failed Failure](breakout/failed_failure_continuation.md) | 在不同上层母命题中分别落地 |
| [Pattern / Pattern Evolution](../core/04_patterns/00_patterns_are_language.md) | 证据输入 | 全部命名子型 | 只描述当前结构，不直接提供许可；演化后按新状态重建候选，最终标签不回填早期理由 |
| [Bar Types / Bar Roles / Implied Pullback](../core/04_patterns/01_bar_types.md) | 证据输入 | Signal/entry 触发、[普通趋势回调](trend/pullback_continuation.md)、[通用逆势修正](reversal/minor_reversal_scalp.md) | 几何与角色按 Context 消费，不逐 K 线类型建策略 |
| [H1 / H2 / L1 / L2](../core/04_patterns/02_h1_h2_l1_l2.md) | 触发语言 + 子型 | [趋势第二次恢复](trend/second_signal_continuation.md)、[区间第二次信号](range/edge_second_signal.md) | H1/L1 本身不是策略；普通合法回调由趋势兜底承接 |
| [Wedge / Parabolic Wedge](../core/04_patterns/03_wedges.md) | 命名子型 | [楔形回调](trend/wedge_pullback_continuation.md)、[楔形反转](reversal/wedge_reversal.md) | 同一形态的顺势与逆势解释分开 |
| [Double Top / Double Bottom](../core/04_patterns/04_double_tops_bottoms.md) | 命名子型 | [双测试旗形](trend/double_flag_continuation.md)、[双顶双底逆势修正](reversal/double_top_bottom_reversal.md)、区间边缘策略、完整 MTR 链 | 由外层状态决定延续、fade、minor scalp 或 MTR 结构证据归属；形态名不降低 MTR 门槛 |
| [Final Flag](../core/04_patterns/05_final_flags.md) | 命名子型 | [最终旗形反转](reversal/final_flag_reversal.md) | Candidate、失败与 result evidence 分开 |
| [Triangle / Expanding Triangle / ii / ioi / oo](../core/04_patterns/06_triangles_ii_ioi_oo.md) | 命名子型 / BOM 输入 | [双向突破模式](breakout/breakout_mode.md)、[扩张三角形 MTR](reversal/expanding_triangle_mtr.md) | 收敛/压缩与扩张反转职责分开 |
| [Gap Family](../core/04_patterns/07_gaps.md) | 证据输入 + 命名子型/目标 | [均线缺口回调](trend/moving_average_gap_bar.md)、[量度目标构造](breakout/measured_move_breakout.md)、opening 页 | Gap 名称不自动产生方向或回补目标 |

## Setup 与管理

| Core 权威思想 | 策略层角色 | 当前落点 | 覆盖结论 |
| --- | --- | --- | --- |
| [Setup / Evidence Convergence / Candidate Decision](../core/05_setups/00_what_is_a_setup.md) | 组织边界 + 候选资格 | [页面类型](README.md#页面类型)、[选择链](README.md#选择链)、23 个实际策略页 | 每个可交易候选至少有两个相互补充的理由；Core TRADE / WAIT / REJECT 分别映射 Strategy STRATEGY / WATCH / NO_TRADE，不生成具体价格 |
| [Trade Plan](../core/06_trade_plan_and_management/00_trade_plan.md) | 管理 schema | [执行清单](README.md#执行清单从策略页到-trade-plan) | 候选通过后实例化 supporting reasons、opposing evidence、update condition 和订单/管理字段，不新增策略家族 |
| [Scalp / Swing / TBTL](../core/06_trade_plan_and_management/01_scalp_vs_swing.md) | 管理约束 | 各策略“目标与管理”、时段覆盖层 | 入场前绑定持有方式；TBTL 不作价格目标 |
| [Scaling In / Scaling Out](../core/06_trade_plan_and_management/02_scaling_in_out.md) | 数量与管理约束 | [跨情景基线](README.md#跨情景基线全部链接-core不在此重复定义)、[限价探针与预设加仓](range/edge_fade_limit_scalein.md) | Scale-in/out 不改变上层 premise；趋势盈利加仓等变体在原策略 Trade Plan 中处理，不另立 entry 策略 |

Core 的风险与心理纪律是 `Core / Application`，不在 Definition 注册表中；策略层通过执行清单、仓位约束、FOMO/OPM/沉没纪律与连续亏损后的暂停规则横向继承，不把心理状态改写为入场策略。

## Core / Application 命题级复核

Definition 注册表只能证明概念入口没有遗漏；以下六个 `Core / Application` 页面还包含会改变策略资格、直接预期或管理的命题，必须单独核对。

| Core Application | 不可丢失的命题 | Strategy 落点 | Reference 复核 |
| --- | --- | --- | --- |
| [趋势延续 Setup](../core/05_setups/01_trend_continuation.md) | 原方向控制仍有效；回调未破坏主要结构；顺势恢复触发；直接预期旧极值或延续 | [普通趋势回调](trend/pullback_continuation.md)作为母命题兜底，R01/R08/R14/R37–R39 为命名子型 | [14A](../reference/course/14A.md)、[45C](../reference/course/45C.md) |
| [突破延续 Setup](../core/05_setups/02_breakout_continuation.md) | 交易新价格获得接受，不交易单次越界；预判版与确认版必须分别计算 | [Breakout Mode](breakout/breakout_mode.md)、[BTC/STC](breakout/buy_sell_the_close.md)、[突破回踩](breakout/breakout_pullback_test.md)及 failed-failure/opening 子型 | [15A](../reference/course/15A.md)、[18B](../reference/course/18B.md) |
| [交易区间 Fade Setup](../core/05_setups/03_trading_range_fade.md) | 成熟区间边缘的外部价格未获接受；目标先回区间内部；中部与不可交易 barbwire 不提供优势 | [边缘确认 fade](range/edge_fade_confirmed.md)作为承接，R17–R19 收紧进入方式，R23/R24 作为候选相关硬约束 | [18D](../reference/course/18D.md)、[48J](../reference/course/48J.md) |
| [主要趋势反转](../core/05_setups/04_major_trend_reversal.md) | 成熟趋势失控、通道/趋势线破坏、旧极值测试失败和反方触发构成完整链；早期/确认是两份计划 | [MTR 早期与确认](reversal/mtr_early_and_confirmed.md)承接 R30/R31；合格 ET 用 R43；形态名不能替代完整链 | [22A](../reference/course/22A.md)、[38A](../reference/course/38A.md) |
| [逆势修正 Scalp](../core/05_setups/05_minor_reversal_scalp.md) | 第一次逆势反转默认只期待两腿修正或区间；升级 MTR 只走预写 runner 或退出后新计划 | [通用 minor](reversal/minor_reversal_scalp.md)承接 R48，R07/R12/R32/R33/R42 为命名子型 | [21A](../reference/course/21A.md)、[42C](../reference/course/42C.md) |
| [风险与心理纪律](../core/06_trade_plan_and_management/03_risk_psychology.md) | 合理 stop 远时缩仓或放弃；OPM/沉没/FOMO 不改变 premise；连续失误后的暂停属于风险控制 | [执行清单](README.md#执行清单从策略页到-trade-plan)与[跨情景基线](README.md#跨情景基线全部链接-core不在此重复定义)，不新增入场策略 | [36B](../reference/course/36B.md)、[51D](../reference/course/51D.md) |

## 高风险边界的 Core + Reference 交叉结论

| 边界 | Core 裁决 | Reference 证据 | Matrix / Flow 处理 |
| --- | --- | --- | --- |
| 模糊基础状态与 BOM | trend/range 不清时以 trading range 作为管理假设；BOM 是可叠加于任意基础状态的双向候选，不是第三种基础状态 | [12B](../reference/course/12B.md)说明长区间进入 BOM；[26A](../reference/course/26A.md)说明形态职责取决于外层状态 | R35 产生 WATCH 但不授权未成熟 fade；R26 由全局 collector 并行收集，不能被 R35 截断 |
| 双顶/双底与 MTR | 双测试只是形态语言；完整 MTR 仍需结构破坏、旧极值测试失败和反方控制触发 | [25A](../reference/course/25A.md)明确“不足以构成 MTR 的双顶底只是次要反转”；[27A](../reference/course/27A.md)保留完整头肩/MTR 骨架 | R42 归 minor scalp；完整链改走 R30/R31，双顶/双底只作为结构证据 |
| ET 与 MTR | 合格尺度和反向压力先建立 ET MTR 候选；反向突破、follow-through 与 acceptance 才确认控制转移 | [26B](../reference/course/26B.md)区分 TTR 内 minor ET 与大型合格 ET | R43 进入 MTR collector；TTR 内弱 ET 退回 range/minor，不借用 R43 |
| 尾盘时间风险 | 时间、target、stop 与持有方式属于同一 Trade Plan 和 Trader's Equation；时间不足只否定相应计划 | [48I](../reference/course/48I.md)、[48J](../reference/course/48J.md)说明尾盘 swing、宽 stop 和小利润窗口的差异 | R28 在候选形成后逐候选过滤；一个 swing 失败不删除独立合格 scalp，全部候选失败才全局 NO_TRADE |
| Broad channel transition | 趋势线突破、回调加深和双边增加只增加转换证据，不自动结束仍有效的外层控制 | [16E](../reference/course/16E.md)、[45C](../reference/course/45C.md)说明反向突破常先形成区间且外层宽通道可继续有效 | R14 STRATEGY 与 R15 WATCH_FLAG 可以并存；R15 不提前截断 R14 |
| 概率与经验数字 | 每个概率必须绑定状态、事件、分母和时间窗；同名形态不能借用另一版本概率 | [边界与冲突](../reference/course/boundaries_and_conflicts.md)集中登记分母冲突 | 数字只放可选“语境数字与先验”；PSEL 使用候选自己的 entry/stop/target/management 方程 |

维护时应把 `core/README.md` 的 Definition 注册表、全部 Core / Application 正文与本页逐项对照。直接链接只能证明入口已登记，不能代替上述 Core + Reference 命题级语义复核。

## 当前结论与维护触发

在当前 Core 注册表下：

- 五个已登记 Setup 家族都有母命题承接；
- 普通趋势回调与通用 minor reversal 已有兜底，命名子型不再承担整个母命题；
- Breakout Mode 已覆盖压缩与非压缩双向候选；
- 其余 Definition 思想均被登记为证据输入、状态约束或 Trade Plan / 管理约束，不因缺少独立策略页构成遗漏。

以下变化必须同步更新本表、[覆盖矩阵](coverage_matrix.md)和[决策流程](decision_flow.md)：

1. Core 新增或改变一个会独立改变 premise 的 Setup 家族；
2. 新 Pattern 产生了现有母命题无法表达的触发、失效或直接预期；
3. 现有兜底被发现不能承接一类合法 Core 交易；
4. 某项证据输入开始独立提供交易许可。
