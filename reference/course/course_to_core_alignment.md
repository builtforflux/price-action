# 01–52 课程综合与 Core 对齐

> 本文把 01–52 全部课程材料串成一套完整思想，展示各章的知识职责、在 Core / Reference 中的落点及边界。

## 一、覆盖范围与使用方式

本文覆盖：

- 01–52 共 52 个课程主编号；
- 191 个实际分讲 Markdown；
- `core/` 七个专题目录下的 32 篇正文；
- 课程中的定义、镜像、状态转换、规则—案例、数学张力和管理边界。

逐讲证据仍以本目录的编号文件为准；全部分讲入口见[完整课程索引](lesson_index.md)，文本与视觉验收状态见[课程覆盖清单](coverage_manifest.md)，跨讲重复见[重复矩阵](repetition_matrix.md)，数字和规则冲突见[边界与冲突](boundaries_and_conflicts.md)。本文只负责回答三个问题：

1. 每一章在完整课程中承担什么职责？
2. 这项思想应该进入 Core 还是 Reference？
3. Core 承担什么权威职责，与其他知识层的边界是什么？

本文映射以本仓库现有 `reference/course` 为基线，不表示课程中的经验百分比已经获得外部统计验证。固定参数、产品知识和平台机制留在 Reference，不作为通用 Core 定义。

## 二、01–52 串联后的完整思想

课程的完整思想不是一组形态信号，而是一条持续更新的判断链：

```text
价格与成交形成可观察图表
    ↓
判断 Market Cycle：trend / trading range
    ↓
若为 trend，再判断 breakout phase / tight channel / broad channel
    ↓
结合 Context：位置、压力、Always In、支撑阻力、周期与剩余时间
    ↓
Pattern 只描述当前结构，不直接生成交易
    ↓
Setup 把状态、位置、触发和失效事实组合成一个交易命题
    ↓
Trader's Equation 检查同一方案的概率、风险、回报和成本
    ↓
Trade Plan 固定 entry、protective stop、target、仓位和管理方式
    ↓
成交后观察 acceptance、disappointment、failure 与 premise 变化
    ↓
继续持有、主动退出、分批处理或在新信号下重新入场
```

这条链有七个不能拆开的原则：

1. **状态优先于形态。** 同一个 H2、楔形、双底或强 K 线，在紧密趋势、宽通道和交易区间中的意义不同。
2. **位置与路径决定形态是否有价值。** 支撑阻力、旧高低点、突破点、测量目标、入场价和剩余时间会改变现实回报。
3. **概率只能属于定义清楚的事件。** 40%、60%、70%、75%、80%、90% 的分母、目标距离和观察时点不同，不能互相替换或相乘。
4. **确认与价格存在交换。** 早入获得较好价格和较近结构，但概率较低；等待突破与跟进提高确认，却常带来更远止损和更小剩余空间。
5. **管理必须继承原交易构造。** Scalp、swing、stop entry、limit entry、单次入场和分批建仓分别拥有不同的止损、目标和结果分布，不能成交后随意互换。
6. **前提必须随新证据更新。** 正常回调不自动否定 swing；强反向突破、持续跟进、交易区间化或 Always In 翻转则可能要求提前退出。退出后可以重新入场。
7. **风险控制独立于方向判断。** 小止损不等于好交易，宽止损不等于账户风险大；结构决定止损，仓位决定金额风险，计划内总敞口决定最坏损失。

## 三、01–52 每章职责与知识去向

| 课程 | 在完整体系中的职责 | 主要增量 | 仓库去向 |
| --- | --- | --- | --- |
| [01](lesson_index.md#course-01) | 建立术语和基础框架 | 把趋势、区间、K 线、scalp/swing 等词放进同一语言系统 | Core 方法主线与 Glossary |
| [02A–D](lesson_index.md#course-02) | 解释图表、价格行为和市场反应 | 成交量、新闻、Pain Trade、Context、Momentum；重点是观察价格反应而非猜参与者 | Price Action 的可观察证据边界进入 Core 方法，Pain Trade 进入 Acceptance；市场机制和事实断言留 Reference |
| [03A–E](lesson_index.md#course-03) | 补充外汇产品知识 | 报价、pip、点差、保证金、rollover、carry 和损益换算 | Reference-only；不进入通用价格行为 Core |
| [04](lesson_index.md#course-04) | 建立交易环境和周期分工 | 交易周期、大周期、均线及观察设置怎样服务 Context | 周期分工进入 Core；20-bar EMA 等默认图表设置留 Reference / 观察约定，不作为通用信号 |
| [05](lesson_index.md#course-05) | 讨论程序化交易和市场操纵叙事 | 算法、高频和操纵观点不能替代可观察价格证据 | 方法边界；具体事实留 Reference |
| [06](lesson_index.md#course-06) | 描述成功交易所需行为 | 纪律、耐心、客观、风格适配和风险承受 | Core 风险心理；执行纪律 |
| [07A–B](lesson_index.md#course-07) | 把学习起步连接到实际选择 | 市场和周期选择、选择性交易、情绪及客观执行 | Core 时间周期与风险心理 |
| [08A–D](lesson_index.md#course-08) | 建立 K 线与 signal 语言 | Trend/TR bar、反转、内外包、ii、signal bar 与 Context | Core Pattern、Bar Types、Setup 边界 |
| [09A–C](lesson_index.md#course-09) | 定义回调和 H/L 计数 | actual/implied pullback、H1/H2/L1/L2、高阶嵌套、breakout 后重置、endless pullback、多周期计数 | Core H/L、趋势延续、二次入场 |
| [10A–B](lesson_index.md#course-10) | 建立买卖压力语言 | 收盘、连续性、影线、广义 gap 和区间压力怎样显示控制变化 | Core Context、Acceptance、Gap |
| [11A–D](lesson_index.md#course-11) | 系统定义 Gap 家族 | session gap、Gap Open Bar、micro、MA gap bar、measuring/exhaustion gap、staircase 和目标 | Core Gaps、趋势/通道、支撑阻力、趋势延续 |
| [12A–C](lesson_index.md#course-12) | 建立 Market Cycle | 突破、通道、交易区间、转换，以及趋势/区间惯性 | Core Market Cycle |
| [13A–C](lesson_index.md#course-13) | 连接 Always In、方程和管理 | 方向控制、概率—风险—回报、scalp/swing 选择 | Core Context、Trader's Equation、Scalp/Swing |
| [14A–E](lesson_index.md#course-14) | 系统解释趋势和通道 | 趋势结构止损、急速—通道、紧密/宽幅、小回调趋势 | Core Trends and Channels |
| [15A–G](lesson_index.md#course-15) | 系统解释突破与失败 | Breakout attempt、跟进、surprise、第二腿、第二腿陷阱、测量/衰竭 gap | Core Breakouts、Acceptance、Second Entries |
| [16A–F](lesson_index.md#course-16) | 展开通道的构造和演化 | 动态重画、边界测试、70/30 经验、周期嵌套、通道向区间演化 | Core Trends/Channels、Transition、Context |
| [17A–B](lesson_index.md#course-17) | 细化紧密通道和微型结构 | 微型通道、小回调趋势、首次反转危险和紧密区间 | Core Trends/Channels、Trading Ranges |
| [18A–F](lesson_index.md#course-18) | 系统解释交易区间 | 区间连续谱、BLSHS、BOM、限价市场、真空、成功突破、第二腿陷阱和紧通道高潮寿命启发式 | Core Trading Ranges、LOM、Breakouts、Climax/Transition |
| [19A–E](lesson_index.md#course-19) | 建立支撑阻力和磁点体系 | 市场状态改变水平作用；多周期磁点、整数位、入场价和 50% 回调 | Core Context、Support/Resistance/Targets |
| [20A–B](lesson_index.md#course-20) | 定义测量移动 | Leg 1 = Leg 2、区间/突破高度、双向投射和目标选择 | Core Support/Resistance/Targets |
| [21A–D](lesson_index.md#course-21) | 建立反转总框架 | 次要/主要反转、逆势短线、早入/确认、压力、TBTL 和反转交易方程 | Core MTR、逆势修正 Scalp、Trader's Equation、Scalp/Swing |
| [22A–D](lesson_index.md#course-22) | 完整展开 MTR | 趋势线破坏、旧极值测试、HL/LH、重新入场和失败后重置 | Core Major Trend Reversal、Acceptance |
| [23A–B](lesson_index.md#course-23) | 定义 Final Flag | 候选与事后确认、趋势晚段、尺度、BOM 和低概率早入 | Core Final Flags、Climax、逆势修正 Scalp |
| [24A–E](lesson_index.md#course-24) | 系统解释 Wedge | 三推、坏楔形、抛物线楔形、75/25 先验和突破后更新 | Core Wedges、Climax、Breakouts、逆势修正 Scalp |
| [25A–B](lesson_index.md#course-25) | 解释广义双顶双底 | 双测试、旗形、颈线、支撑阻力复测和失败机制 | Core Double Tops/Bottoms、MTR |
| [26A–B](lesson_index.md#course-26) | 定义三角形与扩张三角形 | 五腿成熟度、压缩/扩张、旗形与反转职责 | Core Triangles、Breakout Mode |
| [27A–B](lesson_index.md#course-27) | 将头肩形还原为价格行为 | MTR 骨架、右肩、颈线失败及区间本质 | 不建独立 Core 形态；归 MTR、Double Tests、Trading Range |
| [28](lesson_index.md#course-28) | 将圆弧顶底还原为状态过程 | 圆弧常是交易区间或 endless pullback 的另一标签 | 不建独立 Core 形态；归 Trading Range、Pullback |
| [29A–E](lesson_index.md#course-29) | 系统解释 Climax | 事后命名、V 形过渡、TBTL、连续高潮、真空、gap 和周期重置 | Core Climax/Transition、Gaps、Scalp/Swing |
| [30A–E](lesson_index.md#course-30) | 深入 Trader's Equation | 微小优势、概率/RR 交换、40–60、等距目标和统计冲突 | Core Probability/Risk/Reward；冲突留 Reference |
| [31A–D](lesson_index.md#course-31) | 明确 Scalp 与 Swing | 目标尺度、持有方式、成本、2R、强突破和计划一致性 | Core Scalp/Swing、Trade Plan |
| [32A–C](lesson_index.md#course-32) | 系统解释订单 | Stop/limit 与市场状态、确认—价格交换；market 成交和 bracket/OCO 平台机制 | 前者进入 Core Order Logic；具体平台机制留在 Reference |
| [33A–G](lesson_index.md#course-33) | 系统解释 Stop | 保护止损、结构失效、追踪、宽/窄止损、保本和仓位反推 | Core Stop、Trade Plan、Risk |
| [34A–B](lesson_index.md#course-34) | 区分初始与实际风险 | Initial risk、事后 Actual Risk、目标替代和样本统计问题 | Core 定义风险四分法；统计冲突留 Reference |
| [35A–C](lesson_index.md#course-35) | 展开分批建仓数学 | 加权均价、层数、间距、共同止损、最坏总风险和高胜率代价 | Core Scaling In/Out、Trade Plan |
| [36A–B](lesson_index.md#course-36) | 解释成交后的计划更新 | 利润保护、目标变化、OPM 误区和默认管理 | Core Trade Plan、Acceptance、Risk Psychology |
| [37A–B](lesson_index.md#course-37) | 将前 36 讲重新整合 | 状态—交易构造—双周期—40/60—默认目标，以及浮盈/已实现利润不能替代新增风险预算 | Core 方法主线、Risk Psychology 和全局交叉检查 |
| [38A–D](lesson_index.md#course-38) | 顶部 MTR 完整案例 | 卖压、较低高点、确认、再次入场、止盈和止损 | Core MTR；具体案例留在 Reference |
| [39A–D](lesson_index.md#course-39) | 底部 MTR 镜像案例 | 买压、更高低点、概率交换、追踪止损和开盘案例 | Core MTR；具体案例留在 Reference |
| [40A–E](lesson_index.md#course-40) | 解释趋势末端追价和失望 | FOMO、Final Trend Bar、Give-up Bar、入场价测试、被套和风格切换 | Core Climax、Acceptance、Risk Psychology |
| [41A–D](lesson_index.md#course-41) | 展开强突破和 Buy/Sell the Close | 收盘入场、swing stop、突破—通道、陷阱与趋势退出 | Core Breakout/Trend Setup；具体案例留在 Reference |
| [42A–C](lesson_index.md#course-42) | 重新整理高潮和失败反转 | minor/major climax、测量/衰竭 gap、微型通道和区间第二腿 | Core Climax、Gaps、Second-leg Trap |
| [43A–D](lesson_index.md#course-43) | 紧密多头通道专题 | 首次反转、顺势买入、逆势分批困难、区间化 | Core Trends/Channels、Scaling；策略案例 |
| [44A–D](lesson_index.md#course-44) | 紧密空头通道镜像 | 首次反转、顺势卖出、逆势分批困难、区间化 | Core Trends/Channels、Scaling；策略案例 |
| [45A–E](lesson_index.md#course-45) | 宽幅多头通道专题 | 趋势/区间双重属性、周期嵌套、失败反转、50% 回调和买入区 | Core Trends/Channels、Context；策略案例 |
| [46A–E](lesson_index.md#course-46) | 宽幅空头通道镜像 | 主要高点、局部反转、逆势管理、50% 回调和卖出区 | Core Trends/Channels、Context；策略案例 |
| [47A–D](lesson_index.md#course-47) | 交易区间综合专题 | 困惑诊断、80% 规则、第二腿陷阱、限价交易、最终突破 | Core Trading Ranges、LOM、Second Entries |
| [48A–K](lesson_index.md#course-48) | 日内时段和开收盘专题 | first swing、Opening BOM、first-18 heuristic、Opening Reversal、日中转换、尾盘时间风险和磁点 | Core 定义对象与时间边界；固定窗口和具体参数留在 Reference |
| [49A–E](lesson_index.md#course-49) | 用整日案例验证状态重判 | 开盘反转、急速—通道、区间反复、高潮、第二腿陷阱和尾盘转换 | 用于验证全部 Core；不新增独立定义 |
| [50A–E](lesson_index.md#course-50) | 剥头皮专题 | 适用状态、交易者门槛、低周期陷阱、TICK 辅助和案例管理 | Core Scalp/Swing；TICK 与具体案例留在 Reference |
| [51A–D](lesson_index.md#course-51) | 解释因错误造成的亏损 | 错误信念、坏交易、心理止损、低风险误区、正确 stop、分批风险和周期一致性 | Core Trade Plan、Risk Psychology、Stop、Scaling |
| [52A–B](lesson_index.md#course-52) | 汇总防止大亏的管理规则 | 三层保护、趋势末端失望、前提改变、保本边界和 trapped traders | Core Acceptance、Trade Plan、Risk Psychology |

## 四、跨章节思想怎样落入七个 Core 专题

| Core 专题 | 课程连续链 | 应保留的统一思想 | 不能混入的内容 |
| --- | --- | --- | --- |
| `00_method` | 01–02 → 12–13 → 30 → 37 → 51–52 | 状态、背景、形态、Setup、方程、计划和更新是一条链 | 产品规格、固定胜率、Z-score 冲突 |
| `01_market_cycle` | 12 → 14–18 → 29 → 40–47 → 49 | Trend/TR 基础状态；breakout phase、tight/broad channel 连续谱；区间最终突破 | 把 breakout mode 当第三种基础状态；把 climax 当立即反转信号 |
| `02_context` | 02D、04、10、19–20 → 37 → 45–49 | 位置、压力、Always In、支阻、目标、周期和剩余时间共同改变交易方程 | 猜测真实订单身份；固定开盘/尾盘参数 |
| `03_acceptance_and_order_logic` | 08–10、15、18 → 32–33 → 40–42、47、52 | 触发后看跟进、收回、失望、失败；区分 stop entry/protective stop；识别二次尝试和陷阱 | 把第二次信号当独立优势；把限价入场当无限摊平 |
| `04_patterns` | 08–11 → 23–29 → 42 | 形态描述压力和结构，不脱离 Context；候选与事后结果分开 | 为头肩、圆弧等同义标签重复建立交易规则 |
| `05_setups` | 09、15、18、21–22 → 38–47 | 趋势延续、突破延续、区间 fade、MTR、逆势修正 scalp 是交易命题原型 | 具体价格、订单寿命、固定时间窗口和完整执行方案 |
| `06_trade_plan_and_management` | 30–36 → 50–52 | 同一版本的 entry/stop/target/size/management；scalp/swing；总风险；心理纪律 | 课程内部错误算术、业绩承诺和未经限制的加仓 |

## 五、Core 32 篇正文知识映射

### 00_method

| Core 页面 | 课程依据 | 权威职责 | 边界与旁路 |
| --- | --- | --- | --- |
| [00_al_brooks_thesis](../../core/00_method/00_al_brooks_thesis.md) | 01–02、06–08、12–13、30、37、49、51–52 | 定义 Price Action 的最低可观察证据边界，并连接状态、Context、Pattern、Setup、Trade Plan、方程和成交后更新 | Volume、DOM 和新闻不独立保证方向；交易判断仍看价格的突破、接受或失败，外部事实与机制留在 Reference |
| [01_probability_risk_reward](../../core/00_method/01_probability_risk_reward.md) | 13A、21B、30A–E、31、34A–B、37B、39C、51A–C | 定义 probability、risk、reward、cost 的同方案关系，以及 initial / Actual / account / personal risk 四分法 | Actual Risk 是事后统计量，不能由单笔赢家倒推事前正期望；Z-score、80%/3R 和十亿交易者算例留在 Reference |

### 01_market_cycle

| Core 页面 | 课程依据 | 权威职责 | 边界与旁路 |
| --- | --- | --- | --- |
| [00_market_cycle](../../core/01_market_cycle/00_market_cycle.md) | 12A–C、13A、14、16–18、21A、37、43–49 | 定义 Trend / TR 基础状态、breakout phase—channel 层级、模糊状态 fallback，以及周期绑定的 reversal / minor reversal | 所有状态标签必须绑定观察周期；breakout mode 不作为第三种基础状态 |
| [01_trends_and_channels](../../core/01_market_cycle/01_trends_and_channels.md) | 11D、14A–E、16A–F、17A–B、37B、41B、43–46、50A | 定义 tight / broad channel、局部与外层结构、首次 pullback 阶段切换、staircase、shrinking stairs、trending trading range 和宽通道参与区启发式 | 通道标签和参与区描述结构连续谱，不单独生成交易动作；75/25 只适用于清楚倾斜的通道 |
| [02_trading_ranges](../../core/01_market_cycle/02_trading_ranges.md) | 12–13、17–19、28、37、42C、47A–D、49 | 定义普通区间、TTR、宽区间、80% 经验、BOM 条件和区间第二腿陷阱 | 50/50 只作为中性或 BOM 条件先验，不是所有区间突破的固定概率 |
| [03_breakouts_and_breakout_mode](../../core/01_market_cycle/03_breakouts_and_breakout_mode.md) | 15A–G、18B/F、20B、24E、29E、40–42、47、50D | 区分 breakout event、接受、breakout phase、BOM 和 second-leg 倾向，并定义 Buy / Sell The Close 的早期与确认版本 | 首根强突破收盘可形成早期版本；持续收盘与 follow-through 形成确认版本，两者的风险时点不同 |
| [04_climax_and_transition](../../core/01_market_cycle/04_climax_and_transition.md) | 18C、23、24D、29A–E、40A–E、42A–C、48J、49、52 | 区分进行时与事后 climax，登记紧通道寿命启发式与 climax 语境中的 TBTL 倾向，并界定首次反转、Final Trend Bar 的事后角色和趋势末端失望 | Climax 和 Final Trend Bar 不直接预测顶部或底部；根数与概率是特定背景经验，交易结论仍由后续接受或失败决定 |

### 02_context

| Core 页面 | 课程依据 | 权威职责 | 边界与旁路 |
| --- | --- | --- | --- |
| [00_context_location_control](../../core/02_context/00_context_location_control.md) | 02D、08D、10、13、19、21A、37、40、43–49 | 定义 buying / selling pressure、位置、路径空间和 Always In 控制 | Always In 通常由强反转加跟进切换；强 Context 下单根足够强的反转 K 可立即切换；方向不等于持仓 |
| [01_support_resistance_targets](../../core/02_context/01_support_resistance_targets.md) | 11D、19A–E、20A–B、29、33F、34B、40、42、48、52B | 区分 support、resistance、magnet 与 target，并纳入 entry、关键收盘和日周月 OHLC 候选 | Magnet 不是必到结果；水平本身不直接生成 entry |
| [02_time_and_timeframes](../../core/02_context/02_time_and_timeframes.md) | 04、09C、12B、16C、19A/C、37A、40–41、45–46、48–49、51D、52A | 定义多周期、session 和剩余时间边界，并区分 first swing、Opening BOM、first-18 heuristic、内部固定 window 与 Opening Reversal | Opening BOM 可作宽泛课程用语；固定窗口和具体参数留在 Reference，不形成通用定义 |

### 03_acceptance_and_order_logic

| Core 页面 | 课程依据 | 权威职责 | 边界与旁路 |
| --- | --- | --- | --- |
| [00_stop_entry_vs_protective_stop](../../core/03_acceptance_and_order_logic/00_stop_entry_vs_protective_stop.md) | 08D–09、32A–C、33A–G、41B/D、51B–D、52A | 区分 stop entry 与 protective stop，并定义结构候选、实际在场保护和 mental stop 的边界 | Stop 不保证成交价格；滑点、跳空和平台安全进入真实账户风险 |
| [01_acceptance_and_failure](../../core/03_acceptance_and_order_logic/01_acceptance_and_failure.md) | 02C、10、15、18、19D、33D、36、40、42、52A–B | 定义 acceptance、disappointment、premise change、trade failure、三层保护和退出后再入 | Pain Trade 是由价格推断的行为与路径模型，不另建 Setup 或 failure 状态 |
| [02_limit_order_market](../../core/03_acceptance_and_order_logic/02_limit_order_market.md) | 18D–E、32B–C、35、43C–47D、50E、52B | 定义 limit-order logic 在区间与宽通道中的适用条件、成本、计划内分批和强突破失效 | 限价成交和“差一 tick”都不是保证；无限摊平不属于该模型 |
| [03_second_entries_and_traps](../../core/03_acceptance_and_order_logic/03_second_entries_and_traps.md) | 09、15D、18B、21D、24、42C、47C、49C、51B | 定义第二信号对上层命题的继承关系、区间第二腿陷阱，以及 chart entry bar 与账户 actual fill 的分层 | 图形名称只能说明图表触发，不能证明账户已经成交 |

### 04_patterns

| Core 页面 | 课程依据 | 权威职责 | 边界与旁路 |
| --- | --- | --- | --- |
| [00_patterns_are_language](../../core/04_patterns/00_patterns_are_language.md) | 02D、08D、21–29、42 | 定义 Pattern 作为结构语言，并与 Setup 分层 | 头肩形、圆弧顶底等替代标签不因课程有专讲就自动建立独立 Pattern Definition |
| [01_bar_types](../../core/04_patterns/01_bar_types.md) | 08A–D、09A、10、15D、40C、52 | 定义 trend / TR / reversal bar、shaved 几何、actual / implied pullback，并区分 signal bar、chart entry bar 和账户 actual fill bar | Shaved 只描述无影线边界，不独立生成 Setup；Signal Bar 保留计划层角色，强弱评价落在图表触发层，账户成交事实单独记录 |
| [02_h1_h2_l1_l2](../../core/04_patterns/02_h1_h2_l1_l2.md) | 09A–C、14、17、22、24、49B/D、50E | 定义 H1–H6 / L1–L6、局部与全局尺度，以及明确 breakout leg 后的计数重置 | 高阶编号描述尝试次序，不是胜率等级 |
| [03_wedges](../../core/04_patterns/03_wedges.md) | 24A–E、27、29、42、49 | 定义三推、抛物线楔形和 wedge 在延续、反转与高潮中的职责 | 较少预期方向突破后按突破质量重新评估，不继续机械沿用旧先验；75/25 不是任意 wedge 的固定胜率 |
| [04_double_tops_bottoms](../../core/04_patterns/04_double_tops_bottoms.md) | 09B、21D、22–25、27–28、38–39 | 定义广义双测试、neckline 确认、形态高度量度、失败反向分支、旗形和微型变体 | 双顶或双底只描述结构，交易命题仍取决于状态、位置和确认 |
| [05_final_flags](../../core/04_patterns/05_final_flags.md) | 23A–B、29、40E、43C、48J | 定义 Final Flag 候选、最小尺度、晚段语境和事后确认 | “Final” 是事后角色，不是实时确定标签 |
| [06_triangles_ii_ioi_oo](../../core/04_patterns/06_triangles_ii_ioi_oo.md) | 08C、18B、26A–B、29E、47 | 定义普通与扩张 triangle 的五腿成熟度、相对尺度，以及 expanding triangle 的 MTR 候选条件 | 尺度与末端反向压力建立候选；后续突破、跟进和接受负责确认升级 |
| [07_gaps](../../core/04_patterns/07_gaps.md) | 10–11、15E、29A–C、34B、42A–B、46A、48F | 区分 session gap、Gap Open Bar、完整 K 线 gap、body / negative-overlap / micro / measuring / exhaustion gap | Negative gap 不是反方向跳空；measuring 与 exhaustion 是候选解释，结果由后续价格行为确认 |

### 05_setups

| Core 页面 | 课程依据 | 权威职责 | 边界与旁路 |
| --- | --- | --- | --- |
| [00_what_is_a_setup](../../core/05_setups/00_what_is_a_setup.md) | 08D、13、21、30、37、49 | 定义 Setup 与 Pattern、Trade Plan 的边界，以及 Setup 分类的非穷尽性 | Setup 组织交易命题，不替代具体订单和账户执行方案 |
| [01_trend_continuation](../../core/05_setups/01_trend_continuation.md) | 09、13–14、17、22C、31、41、43–46 | 定义 H2 / L2、wedge flag、double test、MA gap bar、premise 和目标在趋势延续命题中的关系 | 具体字段须保持同一 Trade Plan 版本一致 |
| [02_breakout_continuation](../../core/05_setups/02_breakout_continuation.md) | 15、18、20、24E、29E、31D、40–42、48J、50D | 定义突破延续的预判与确认版本、接受、第二腿和 measured move 条件 | Buy / Sell The Close 可落在预测或确认版本，只表示风险承担时点，不另立 Setup |
| [03_trading_range_fade](../../core/05_setups/03_trading_range_fade.md) | 15G、18、19、28、37、47、50E | 定义成熟区间边缘、limit / stop 两类 entry、premise 失效和区间目标 | 第二腿陷阱由上游状态页定义 |
| [04_major_trend_reversal](../../core/05_setups/04_major_trend_reversal.md) | 21–22、27、29、38–39、40E、42 | 定义成熟趋势、结构破坏、旧极值测试、HL / LH、反方控制和 40/60 风险时点 | “约五根强，或约十根普通/较弱”是压力启发式；新结构出现时旧证据需要重置 |
| [05_minor_reversal_scalp](../../core/05_setups/05_minor_reversal_scalp.md) | 21A、21C、21D、23B、24D–24E | 定义第一次逆势反转的短线命题与升级 MTR 的边界，应用 TBTL 路径预期 | 逆势交易不是与趋势对抗；无结构破坏与失败证据时第一笔逆势交易经常失败 |

### 06_trade_plan_and_management

| Core 页面 | 课程依据 | 权威职责 | 边界与旁路 |
| --- | --- | --- | --- |
| [00_trade_plan](../../core/06_trade_plan_and_management/00_trade_plan.md) | 30–36、37、41、51–52 | 定义 entry、stop、target、size、management 的同版本一致性，以及 active stop、catastrophe backup、动态 premise 和三层保护 | 退出后的重新入场属于新计划版本；具体平台机制不属于 Core |
| [01_scalp_vs_swing](../../core/06_trade_plan_and_management/01_scalp_vs_swing.md) | 13B–C、21D、31A–D、36、50A–E、51C–D | 区分 scalp 与 swing 的概率/RR、成本、TBTL 和管理方式 | 两种交易构造不能成交后随意互换；少数专家的极高胜率描述不是通用准入标准 |
| [02_scaling_in_out](../../core/06_trade_plan_and_management/02_scaling_in_out.md) | 30B、35A–C、36、43C–44C、45D–46D、47C、51D、52A–B | 定义加权平均 entry、共同 stop 下的完整总风险，以及成本、止损距离与仓位的关系 | 加仓改变整仓价格和敞口，不凭空提高市场方向概率；无限摊平不属于计划内 scaling |
| [03_risk_psychology](../../core/06_trade_plan_and_management/03_risk_psychology.md) | 06–07、30C、33、36A–B、37B、40A、50B、51A–D、52A–B | 区分正常统计亏损与规则错误，并定义快速纠错、无关痛痒仓位、FOMO 小仓参与边界、OPM / 沉没结果、希望和保本边界 | 浮盈与已实现利润不能替代新增风险预算；遗传决定论和“所有导师无用”等绝对叙事不进入 Core |

## 六、完整课程中不应进入 Core 的内容

### 1. 产品和账户机制

03A–E 的外汇报价、pip、保证金、rollover、carry 和换算属于产品 Reference。它们会随产品、账户货币、经纪商和监管变化，不是通用价格行为定义。

### 2. 因果和参与者身份叙事

05 的算法/高频/操纵、29E 的期权对冲占比、34B 的机构算法止盈、51C 的遗传希望叙事，都只能作为可能解释或待核事实。Core 应只保留可观察的价格、跟进、回调、突破和失败。

### 3. 专用指标

50C 的 NYSE TICK 是辅助信息，不属于 Price Action 最低框架。若保留，应进入 Reference 或具体策略背景，并说明数据源、市场和阈值。

### 4. 固定策略参数

48–49 的开盘/尾盘案例可支持时段 Context，但固定分钟窗口、订单寿命、精确目标和记录字段只作为课程材料保留在 Reference。Core 只定义“时段会改变波动、剩余时间和目标可达性”。

### 5. 课程内部冲突

以下内容因课程内部存在数字、公式或解释冲突，不进入 Core；具体证据见[边界与冲突](boundaries_and_conflicts.md)：

- 30C 的 Z-score 公式与收益解释；
- p2362 的 80%/3R 结论；
- 34B 的十亿交易者连续 100 胜/负算例；
- 43C 的 60%/80%/90% 胜率冲突；
- 51B 无风险回报比的“60% 仍亏损”；
- 用单笔事后 Actual Risk 证明事前正期望。
