# 价格行为术语表

> **状态：Reference / Non-normative**

本表用于检索来源中的术语，不建立独立交易规则。术语怎样进入实时判断，以 [`trading_system/`](../trading_system/README.md) 为准；页码、来源差异与重复证据见[课程概念索引](course/concept_index.md)和[边界与冲突台账](course/boundaries_and_conflicts.md)。

一个术语只回答“正在描述什么”。它不能凭名称提供交易许可。实时顺序始终是：

> 价格事实 → Market Read（继承 Context → 更新 Price Map / Price Process → 确认或重构 Context）→ Opportunity Set → Context Permission + Trade Candidates → Trade Plan → 执行 / 等待 / 不交易

## 一、判断对象

### Price Action

价格运动及其可观察表示。成交量、DOM、新闻和日程可以形成背景或尾部风险，但方向证据仍来自价格如何测试、突破、接受或拒绝相关区域。

### Context

当前交易周期中支配目标、正常回调和管理方式的价格组织，包括市场状态、控制、时间和相关外层约束。连续观察时先继承上次确认结果，再由当前 Price Process 保持、削弱、标记 Transition 或重构；首次看图无法确认时允许 `Unclear`。位置由 Price Map 保存，眼前运动由 Price Process 保存。

### Price Map

按当前价格上方、下方和距离组织相关价格区域、来源与汇合。Potential Entry Area、Target、Obstacle 或 Invalidation Reference 是区域相对某条 Opportunity 的角色，不是地图自身属性；Invalidation 本身是可观察的市场条件。

### Price Process

Price Process 用 `From → Now → Role → Change → Testing → Next` 保存价格怎样演化到当前区域，包括当前段、暂停或局部平衡，以及它承担 continuation、pullback、range leg 还是 reversal attempt 作用。`Change` 依次观察 K 线质量、连续性与 follow-through、gap / overlap、回调质量和反方尝试结果，再汇总 Buying / Selling Pressure 与 Control。它最终压缩成一句双向问题：此前运动怎样变化、哪个区域正在被测试，以及什么新事实表示接受、拒绝、Activation、失败或过期。

### Pattern

对几何或事件顺序的压缩命名。Pattern 是结构视图，不是交易类别；H2、Double Bottom、Wedge、Flag、Triangle 和 MTR 等名称必须还原为共同的价格事实与结果路径。

### Setup

来源材料常用的历史术语。本系统不维护 Setup 家族或 Setup 路由；来源中的 setup 必须被翻译为当前结构、目标事件、触发、失效、概率和方程，才能进入运行流程。

### Opportunity Set

当前现实 Long / Short 市场结果的集合。每条 Opportunity 都有 Direction、Role、Objective、Market Outcome Criterion、Horizon、去重后的理由链、Activation、Invalidation、价格区域角色、最强矛盾、Market Probability 和 Expiry；不同目标或 horizon 分开表达，机会也可以按“先修正、后延续”顺序成立。

### Trade Candidate

在 Context Permission 允许后，于当前判断时点表达某条已 Activation Opportunity 的风险交换，包括 Trigger、Entry、对 Opportunity Invalidation 的引用、Planned Protective Stop、Target、Candidate Outcome Probability、成本、仓位和管理。同一 Opportunity 在 close、follow-through 或回调时点可以生成不同 Candidate，每次都按当前价格重算。

### Trade Plan

被选 Trade Candidate 的冻结快照，明确 entry、Opportunity invalidation snapshot、protective stop、target、outcome criterion、两种概率、成本、仓位、订单与管理。未被选 Candidate 不保存为并行完整计划。

### Market Probability / Candidate Outcome Probability

Market Probability 描述 Opportunity objective 在当前条件与 horizon 内发生的概率；Candidate Outcome Probability 描述当前 Trigger、Entry、Stop、退出、数量和管理下各交易结果的概率。只有两者评价同一结果事件时才能直接共用。

### Evidence Convergence / Two Reasons

市场状态、位置、控制、结构与触发等相对独立证据共同支持一条 Opportunity。来源中的“two reasons”是最低提醒，不是固定打分；同一价格事实的多个同义标签、嵌套计数或重叠形态不得重复计票。

### Evidence Lifecycle

证据会出现、增强、减弱、失效或在结构改变后重置。新主导突破、成熟区间、控制切换或更高周期结构接管后，旧计数和旧倾向不能自动继承。

### 执行 / 等待 / 不交易

- **执行**：选中 Candidate，Trade Plan、保护、目标和方程同时成立。
- **等待**：Market Read 尚未解决、Opportunity 尚未 Activation，或当前没有值得承担的 Candidate，但存在明确下一事实与 Expiry。
- **不交易**：机会已失效、风险无法定义、方程无优势或运行约束不允许。

这三个结果是当前决策，不是永久评价。详见[交易决策与计划](../trading_system/decision_and_plan.md#十四唯一决策)。

## 二、市场状态与运动

### Market Cycle

Trend 与 Trading Range 之间连续演化的观察模型。常见路径为 `breakout phase / spike → tight channel → broad channel → trading range`；Breakout Mode、Climax 与 Transition 是叠加状态，不是第三种基础市场。

### Trend / Channel

一侧持续控制并反复恢复原方向。Tight channel 回调浅、重叠少；broad channel 回调深、重叠多，行为逐渐接近倾斜区间。所有上涨宽通道同时可以从更高层看成对先前下跌的 bear flag；哪个视图有用，取决于当前测试与目标。

### Trading Range / TTR

双边交易反复成功、突破容易失败的区域。Broad range 的边缘可能提供空间，中部通常没有优势；tight trading range（TTR）重叠多、空间小、触发质量差，通常应等待价格建立分离。

### Breakout Attempt / Acceptance

越过重要边界先只是突破尝试。强收盘、follow-through、分离保持、回测守住与反方失败支持接受；快速回到原区域支持 failed breakout。突破事实、接受程度与方向控制必须分开记录。

### Breakout Mode

两个方向的突破都合理、尚不能预设结果的条件状态。它不保证第一次突破成功，也不是独立交易类型；突破后立即转入接受/失败证据链。

### Breakout Pullback / Test

突破后的回调称 breakout pullback；重新访问旧边界或原入场区域是更具体的 breakout test。测试可立即或延后发生，不是突破获得接受的必要条件。

### Buy / Sell the Close

在强突破阶段于顺势收盘附近承担风险的行为语言。它不是单根 K 线许可；每个决策时点仍须用实际 entry、结构 stop、剩余 target 和成本重新计算方程。

### Pullback / Leg / Swing

Pullback 是原运动内尚未否定恢复预期的暂停或反向运动；leg 是较大结构中的一段方向运动；swing 是相对更大的价格路径或持仓目标。第一段后的第二段是条件倾向，不保证长度、力度或完成方式。

### Reversal / Minor Reversal

Reversal 表示方向或状态开始改变，不表示相反趋势已经建立。第一次逆势尝试通常仍是原趋势的 pullback、flag 或 trading range；minor reversal 尚未形成反方持续控制。

### Climax / Transition

加速、大实体或极端微型通道可以是 climax-like 行为，但不保证反转。只有后续进入区间或反向趋势，才能确认原运动已经耗竭或转换。

### Staircase / Trending Trading Range

Staircase 是突破与后续回调持续重叠的阶梯式趋势；trending trading range 是局部区间经短突破迁移到新公平区域。两者都提示趋势强度衰减，但不直接确认反转。

## 三、位置、压力与目标

### Support / Resistance

价格可能停顿、测试或反转的区域，不是保证反转的精确线。突破后同一区域可以交换角色。

### Magnet / Target

Magnet 是可能吸引测试的区域；target 是当前活动结构生成、并由计划选定的结果事件。目标先于概率和 entry：没有明确目标，就无法定义成功事件、现实 reward 或持有时间。

### Measured Move

依据已形成结构投射的目标区域，如区间高度或 `Leg 1 ≈ Leg 2`。它是候选目标，不是价格承诺。

### Test / Reaction

Test 表示价格接近、触及或重新访问参照区域；reaction 是测试后的即时响应。是否获得 acceptance 仍需后续延伸、保持或失败证据。

### Confluence / Dueling Lines

相对独立的支撑阻力对象落在同一区域。汇合可以强化 location，但不能独立生成交易；由同一 swing 推出的多个名称只能算一组事实。

### Overshoot / Undershoot

Overshoot 是短暂越过候选线或边界，undershoot 是未到达便提前反转。轻微越线或未触线不自动使结构失效；持续不再响应旧线才支持重画。

### Pressure / Control / Always In

Pressure 由 K 线连续性、实体与收盘、影线拒绝、突破、gap、跟进和回调质量累积形成。Control 是一侧能否持续推动并阻止另一侧获利。Always In 是“若必须持仓，更可能选择哪一侧”的控制摘要，不表示必须持仓，也不替代目标和方程。

### Gap / Separation

两个相关价格对象之间缺少充分双边交易的空间。传统 gap、body gap、open gap、measuring gap 与 negative/overlap gap 使用不同参照对象；任何机械标注都必须写清参照。Measuring / exhaustion 等结果名称只有后续路径才能确认。

## 四、结构视图与计数

### H1 / H2 / L1 / L2

H1/H2 是回调中第一次/第二次向上恢复尝试；L1/L2 是第一次/第二次向下恢复尝试。它们描述事件次序，不是固定胜率。新的主导 breakout leg 建立后重置计数；高编号通常要求先重判区间或控制变化。

### Double Top / Double Bottom

对同一区域的两次测试。Double Bottom 与 H2 可以是同一底层事件的不同视图：前者强调位置复测，后者强调恢复尝试次序；不能把它们当作两个独立理由。

### Second Signal / Second Entry

Second signal 是第二次可观察触发机会；严格的 second entry 还要求第一次已形成 chart entry。账户是否真的成交是另一层事实，不能由图形名称推断。

### Wedge / Parabolic Wedge

Wedge 描述三次推动或三次尝试。它可属于顺势回调、反转过程或普通区间；parabolic wedge 强调 tight channel 中的高潮式多次 surge。三推只形成当前测试，不保证反转或两段修正。

### Flag / Final Flag

Flag 是对更大运动的逆向或横向修正；因此上涨宽通道在更高层可以是 bear flag，下跌宽通道可以是 bull flag。Final flag 只能实时标为候选，只有后续路径确实终结原趋势段才能确认。

### Triangle / ii / ioi / oo

这些结构都可以表达压缩与双向突破候选。来源对 triangle 的“反转次数”与“段数”口径不同，标注时应声明口径；近 50/50 的倾向只适用于相应成熟结构，不能外推给所有压缩。

### Major Trend Reversal / MTR

MTR 是过程而非形态许可：原趋势先减弱或发生结构破坏，价格测试旧极值，反方再尝试建立控制。双顶底、wedge、head-and-shoulders 等只是在不同阶段对同一过程的视图。

### Micro Double Top / Bottom

近邻 K 线对同一区域的微型复测。它可能是一根或数根的 flag，也可能参与反转过程；尺度本身不决定方向。

### Pattern Evolution

形态名称随新价格扩展、失败或被更大结构吸收。不得用最终形态回填当时不可见的信息；每次结构接管都应重新生成目标与路径。

## 五、K 线与触发

### Trend Bar / Trading-range Bar

由相对实体、影线、收盘位置和 Context 共同判断的连续谱，不是固定尺寸分类。Shaved top/bottom 只描述一端没有明显影线；机械标注须声明 tick 容差。

### Inside / Outside Bar

Inside bar 的高点不高于前高且低点不低于前低。Outside bar 在来源中存在严格越界与允许等高等低两种边界，数据标注必须声明所用定义。

### Reversal Bar

提供反向响应的 K 线。靠近新方向极值的收盘、测试影线与相对较强实体可以增强质量，但外观不能替代结构、位置和后续跟进。

### Signal Bar / Chart Entry Bar / Actual Fill Bar

Signal bar 提供计划触发所需的局部信息；chart entry bar 是声明条件第一次被满足的 K 线；actual fill bar 是账户真实成交所在 K 线。三者可能重合，也可能不同。

### Trigger

使预先声明的入场条件成立的价格事件。Trigger 不等于订单已被接受，也不等于账户已经成交。

### Follow-through / Surprise / Disappointment

Follow-through 是初始运动后的继续延伸；surprise 是明显超出原预期的强行为，常增加第二段可能；entry disappointment 只是入场后表现偏弱，不能单独确认路径或交易 failure。

## 六、订单、风险与结果

### Stop Entry / Limit Entry / Market Entry

- **Stop entry**：价格向交易方向越过触发价后入场。
- **Limit entry**：只在指定价格或更好价格成交，不保证成交或完整成交。
- **Market / close entry**：以当下可得价格承担风险，成交确定性较高但价格不确定。

订单类型只决定参与方式，不能修复一个没有优势的 Trade Candidate。

### Protective Stop / Invalidation

Protective stop 限制账户损失；Structural Invalidation 是证明原 Opportunity 不再成立的价格事实。两者可以接近但职责不同。计划中的 stop、经纪商已确认的 active stop 与灾难备份也必须分开记录。

### Trailing / Breakeven Stop

Trailing stop 随新确认结构向减少开放风险的方向移动。Breakeven stop 是把保护移到计划 entry 或加权平均 entry 附近；佣金、滑点、跳空和部分成交意味着实际结果未必为零。

### Trader's Equation / 40–60 Thinking

以同一组 entry、stop、target 和管理比较成功概率、失败概率、reward、risk、成本与时间占用。多数普通交易没有压倒性胜率；概率优势与回报优势可以互相补偿，但不能混用不同计划的数字。

### Likely / Probably / Risky

来源常把 likely/probably 用作约 60% 或更高的教学语言，而非精确校准模型。Risky 表示概率、合理 stop、现实 reward 或成本使方程不清楚；具体原因必须展开。

### Success / Failure / Scalper's Profit

Success 与 failure 必须绑定预先声明的 outcome criterion：目标先到、stop 先到或 premise 变化主动退出是不同事件。Scalper's profit 只表示价格曾提供合理短线利润机会，不证明账户兑现，也不等于更远 swing 目标成功。

### Active / Expired / Sequence Unknown

已经形成的 Opportunity 在目标、失效、过期或取代事件均未发生时保持 `ACTIVE`；horizon 结束而目标与失效均未发生时为 `EXPIRED`；目标与失效在同一可观察区间内发生且顺序无法确认时为 `SEQUENCE_UNKNOWN`。尚未形成 Opportunity 的未决 Market Read 不进入这组状态。三者描述不同结果。

### Scalp / Swing / TBTL

Scalp 追求较小目标，通常需要更高胜率；swing 接受正常 pullback 以换取更大目标。TBTL（Ten Bars, Two Legs）是常见时间与路径预期，不是硬性完成条件或价格目标。

### Trapped In / Trapped Out / Pain Trade

Trapped in 指已持有不利仓位的一方；trapped out 指错过行情、可能被迫追价的一方。Pain trade 是这些退出或追价压力可能延伸运动的行为路径推断，仍须由价格接受/失败证据确认。

### Fade / Countertrend / Limit Order Market

Fade 押注当前尝试不会获接受；countertrend 明确逆当前控制方向；Limit Order Market 表示双边逆向限价参与反复可获利。三者可以重叠但不是同义词。

## 常用缩写

| 缩写 | 含义 |
| --- | --- |
| `AIL` / `AIS` | Always In Long / Short |
| `BLSHS` | Buy Low, Sell High, Scalp |
| `BO` / `BOM` / `BP` / `BT` | Breakout / Breakout Mode / Breakout Pullback / Breakout Test |
| `BTC` / `STC` | Buy The Close / Sell The Close |
| `ET` / `MTR` | Expanding Triangle / Major Trend Reversal |
| `FBO` / `FF` / `FT` | Failed Breakout / Final Flag / Follow-through |
| `H1`–`H6` / `L1`–`L6` | High / Low counting |
| `LOM` | Limit Order Market |
| `MDB` / `MDT` | Micro Double Bottom / Top |
| `RR` / `TE` | Risk / Reward / Trader's Equation |
| `TBTL` / `TTR` | Ten Bars, Two Legs / Tight Trading Range |

## 运行入口

- 统一循环：[价格行为交易系统总流程](../trading_system/overall_flow.md)
- 概念关系：[Market Read 与 Opportunity](../trading_system/market_read_and_opportunities.md)
- 交易构造：[交易决策与计划](../trading_system/decision_and_plan.md)
- 持仓闭环：[执行、持仓与复盘](../trading_system/execution_management_and_review.md)
- 条件概率：[条件规则台账](../trading_system/conditional_rules_registry.md)
