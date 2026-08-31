# 价格行为来源术语与别名表

> **状态：Reference / Alias Index / Non-normative**

本表用于检索来源术语、仓库别名和必须保留的概念边界，不建立独立交易规则或处理顺序。当前看盘与交易方法由 [`trading_system/`](../trading_system/README.md) 定义；页码、来源差异与重复证据见[课程概念索引](course/concept_index.md)和[边界与冲突台账](course/boundaries_and_conflicts.md)。

一个名称只回答“正在描述哪类事实、视图、判断、结果路径或账户事件”。名称本身不提供交易许可；若同一底层事实同时符合 H2、Double Bottom、Wedge、Flag 或 MTR 等视图，应共享事实而保留各视图不同的解释职责，不能把标签数量当作独立证据数量。

本表偶尔列出当前仓库使用的英文别名，目的只是帮助证据找到可能的消费者。别名不证明该对象必须独立存在，也不要求未来系统继续采用相同名称或分层。

历史仓库名称只在本页用于检索，不是运行可写值：

| 历史名称 | 当前运行名称 |
| --- | --- |
| Market Read / Market Model / Market Note | 市场判断 |
| Price Process | 到达路径与当前测试 |
| Opportunity Set / Opportunity Book | 多方与空方方向机会（市场路径） |
| Path Effect / OpportunityImpact / Market Delta | 本次变化 |
| Context Permission | 无独立运行对象；还原为市场路径的支持、反证与参与前条件 |
| Candidate Outcome Probability | 交易结果概率 |
| Decision Ticket | 交易方案 |
| Account Card | 账户状态 |
| EXECUTE / COMMIT / TRADE | 交易 |
| WAIT | 等待 |
| NO_TRADE / STAND_DOWN | 放弃 |

## 一、来源术语与跨层消歧

### Price Action

价格运动及其可观察表示。成交量、DOM、新闻和日程可以形成背景或尾部风险，但方向证据仍来自价格如何测试、突破、接受或拒绝相关区域。

### Context

来源用 Context 表示某个交易周期中影响目标、正常回调和管理方式的价格组织，包括市场状态、控制、位置、时间和相关外层约束。它是条件集合而非单个标签；应绑定观察周期和判断时点。系统怎样保存、继承或重构 Context 由运行契约决定。

### Price Map

历史仓库用它指代“按当前价格上方、下方和距离组织相关区域、来源与汇合”，它不是 Brooks 的固定对象。Potential Entry Area、Target、Obstacle 或 Invalidation Reference 是区域相对某条市场路径或交易方案的角色，不是区域的永久属性；当前方法把相关事实放在[重要区域、位置与目标](../trading_system/market.md#35-重要区域位置与目标)。

### Price Process

历史仓库用它汇集“价格怎样演化到当前区域”的关系，包括此前运动、当前段、暂停、局部平衡、所测试区域，以及 continuation、pullback、range leg 或 reversal attempt 等可能角色。K 线质量、连续性、follow-through、gap / overlap、回调质量和反方尝试是可复用证据；当前方法把它们放入[尝试、预期与实际表现](../trading_system/market.md#36-尝试预期与实际表现)。

### Pattern

对几何或事件顺序的压缩命名。Pattern 是结构视图，不是交易类别；H2、Double Bottom、Wedge、Flag、Triangle 和 MTR 等名称必须还原为共同的价格事实与结果路径。

### Setup

来源材料常用的历史术语，最低含义是带有 Context、可供考虑入场的 pattern。Setup 不等于完整风险计划；若要被系统消费，仍须能还原为可观察条件、目标事件、参与条件、失效、概率边界和风险交换。Reference 不要求系统维护 Setup 家族或独立路由。

### Opportunity Set

历史仓库用它指代“现实市场结果假说集合”，例如延续、先修正后延续、区间旋转、突破接受、突破失败或反转过程。不同 objective 或 horizon 不能因方向相同而混成一个概率事件；当前方法把每个方向当前唯一的市场路径显示为[双向路径](../trading_system/market.md#38-双向路径)，不另建 Opportunity 对象。

### Trade Expression / 历史 Trade Candidate

历史仓库用它指“在某个判断时点，怎样用 entry、protective stop、target、成本、数量、时间和管理参与一条市场路径”。同一市场路径在 close、follow-through 或回调时点可以形成不同方案。当前方法只使用[交易方案](../trading_system/trade.md)，不建立 Expression 或 Candidate 生命周期。

### Trade Plan

历史材料可把被“交易”选择、供执行和事后核对的参与方式称为 Trade Plan；当前方法直接称为交易方案。它应与未选择的市场路径或研究草案区分；Reference 不决定怎样交易。

### Market Probability / Trade Outcome Probability

Market Probability 描述某个市场 objective 在给定条件与 horizon 内发生的概率；Trade Outcome Probability 描述某组 entry、stop、退出、数量、成本和管理下各交易结果的概率。`Candidate Outcome Probability` 是历史别名。前者不能直接代入交易者方程。任何数值都必须先由[复盘与治理](../trading_system/governance.md#3-已校准的数值规则)发布且仍然有效，运行页再检查适用口径；当前没有生产级数值概率规则。

### Evidence Convergence / Two Reasons

市场状态、位置、控制、结构与触发等相对独立证据可以共同支持同一个结果路径。来源中的“two reasons”是最低提醒，不是固定打分；同一价格事实的多个同义标签、嵌套计数或重叠形态不得重复计票。

### Evidence Update

证据会出现、增强、减弱、失效或在结构改变后重置。新主导突破、成熟区间、控制切换或更高周期结构接管后，旧计数和旧倾向不能自动继承。

### 交易 / 等待 / 放弃

这些是当前方法最终的三种空仓决策结果，不是来源术语定义。Trade 质量接近平衡且存在明确改善事件和期限时等待，否则放弃；质量不值得时放弃。质量较有利时先提交 Account，只有 Account 允许后才成为“交易”。Account 禁止会终止当前表达的提交资格；Trade 只能结束该表达后构造另一份完整表达、等待期限内明确可恢复的条件，或放弃。Reference 只提供会改变行动资格、等待价值或风险边界的证据；各结果的条件和动作由[交易决策](../trading_system/trade.md)拥有。主动不承担风险不能反向改写市场事实、交易质量、概率或来源 Claim。

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

价格可能停顿、测试或反转的区域，不是保证反转的精确线。它们与 Magnet、结构目标等可以共享同一底层重要区域；支撑或阻力只是相对当前方向和路径的职责，突破并接受后同一区域可以交换角色。

### Magnet / Target

Magnet 是可能吸引测试的区域；来源中的 target 可以指结构生成的市场结果，也可以指交易者实际选择的兑现价格。两者可以引用同一重要区域，但不能因价格相同而合并职责：Market 负责结果事件，Trade 负责具体数量的兑现。任何概率或 reward Claim 都必须绑定明确的目标事件、horizon 和判断时点；这是一项证据完整性要求，不另建系统对象。

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

对同一区域的两次测试。Double Bottom 与 H2 在同一周期、Object、区域和恢复链上重合时，共享底层价格事实：前者强调结构复测、Neckline 与可能的高度投射，后者强调恢复尝试次序、Signal / Trigger 与 Chart Entry；条件不同则分别评价。

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

Inside bar 的高点不高于前高且低点不低于前低。来源之间对 Outside bar 的等高、等低边界并不一致，本页只保留这一来源差异。当前运行口径由[K 线与运动事实](../trading_system/market.md#e-k-线与运动事实)统一定义；数据标注必须声明所用口径。

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

订单类型只改变参与和成交方式，不能把缺少来源支持或风险优势的市场判断变成好交易。

### Protective Stop / Invalidation

Protective stop 用于限制账户损失；Structural Invalidation 指证明原市场结果假说不再成立的价格事实。两者可以接近但职责不同。来源还区分计划中的 stop、经纪商已确认的 active stop 与灾难备份；系统应保留这些职责差异，但具体对象和状态由运行契约拥有。

### Trailing / Breakeven Stop

Trailing stop 随新确认结构向减少开放风险的方向移动。Breakeven stop 是把保护移到计划 entry 或加权平均 entry 附近；佣金、滑点、跳空和部分成交意味着实际结果未必为零。

### Trader's Equation / 40–60 Thinking

以同一组 entry、stop、target 和管理比较成功概率、失败概率、reward、risk、成本与时间占用。多数普通交易没有压倒性胜率；概率优势与回报优势可以互相补偿，但不能混用不同计划的数字。

### Likely / Probably / Risky

来源常把 likely/probably 用作约 60% 或更高的教学语言，而非精确校准模型。Risky 表示概率、合理 stop、现实 reward 或成本使方程不清楚；具体原因必须展开。

### Success / Failure / Scalper's Profit

Success 与 failure 必须绑定预先声明的 outcome criterion：目标先到、stop 先到或 premise 变化主动退出是不同事件。Scalper's profit 只表示价格曾提供合理短线利润机会，不证明账户兑现，也不等于更远 swing 目标成功。

### Active / Expired / Sequence Unknown

这些是历史材料中的结果别名，不是 Brooks 的固定状态机。

**市场结果先后不明**

- 目标完成条件与失效条件在现有数据粒度内无法判断先后；
- 这是复盘需要保留的证据边界，不是新的运行状态。

**账户事实先后或归属不明**

- 这是订单、仓位或财务事实可能不可靠的证据边界，不由 Glossary 决定动作。

当前处置分别由[市场判断](../trading_system/market.md#39-首次建立与路径变化)、[账户执行](../trading_system/account.md)和[复盘与治理](../trading_system/governance.md)负责。

### Scalp / Swing / TBTL

Scalp 追求较小目标，通常需要更高胜率；swing 接受正常 pullback 以换取更大目标。TBTL（Ten Bars, Two Legs）是常见时间与路径预期，不是硬性完成条件或价格目标。

### Trapped In / Trapped Out / Pain Trade

Trapped in 推断一方在可见入场机会后没有先获得价格结果、随后可能处于不利路径；trapped out 推断错过行情的一方可能面对追价压力。Pain trade 是两类潜在反应可能延伸运动的行为路径推断，仍须由可见区域、failure、follow-through 与现实空间支持；这些名称不证明实际参与者身份、持仓或盈亏。

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

## 方法入口

以下 Owner 拥有当前运行语义；这些链接只帮助从来源术语定位方法，不表示 Reference 能证明现有对象拆分是唯一设计：

- 市场解释与结果路径：[市场判断](../trading_system/market.md)
- 风险表达与决策：[交易决策](../trading_system/trade.md)
- 订单、持仓、保护与结果：[账户执行](../trading_system/account.md)
- 概率与证据边界：[复盘与治理](../trading_system/governance.md)

市场判断另提供一个不拥有运行状态的派生查询视图：[常见市场场景](../trading_system/scenarios.md)。
