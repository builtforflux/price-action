# 价格行为交易系统总流程

> **状态：Trading System / Runtime Contract**

本页是唯一运行入口。系统处理持续变化和不确定性：稳定的是事实边界、更新规则、风险上限和行动纪律，不是某次市场判断。入场前判断是否值得承担风险，入场后判断是否仍值得承担当前风险。

```text
相关事件
→ Safety Gate：先核对订单、敞口、保护和数据
→ Event Gate：判断增量更新还是完整重构
→ Frame：固定交易周期、外层约束和剩余时间
→ Environment：判断交易周期的 Regime、Direction、Phase、Variant 和 Modifiers
→ Location Map：扫描相关来源，合并价格区域，按上下方向、距离和角色排列，并计算空间
→ Price Action Now：读取当前运动、gap / separation、重叠、跟随、买卖压力和控制
→ Active Test + Views：说明市场正在检验什么；按需附加次序、几何或角色视图
→ 建立向上 / 向下 Market Paths 与 Pending Outcome
→ Market Gate：路径、位置、空间、时间和当前价格行为是否允许交易
→ Risk Plan：Entry、Invalidation、Stop、Target、成本和方程怎样表达风险
→ Execution Gate：账户暴露、仓位、保护、数据和订单条件是否允许执行
→ Action：按当前账户状态选择唯一动作
→ 按 Execution State 执行允许的动作
→ 仅在决定、风险、执行或复盘边界改变时保存最小信息
→ 等待下一相关事件
```

**实盘从哪里开始**：

- 初次打开图表或主要结构已变：走[看图主链](#三看图主链从可见事实到当前判断)，最后得到一句当前市场读取；
- 普通新 K 线：只做[三个 Delta 检查](#普通新-k-线只问三个-delta)，都没变就结束；
- 准备下单、订单工作中、持仓或异常：再叠加[对应账户状态清单](#准备下单)。

## 一、运行对象与权威边界

| 对象 | 唯一职责 |
| --- | --- |
| Runtime Snapshot | 固定判断时点及当时可见的市场、时间、订单、账户、数据和适用规则 |
| Market Model | 保存 `Frame → Environment → Location → Price Action Now → Active Test + Views → Paths` 的 Market Read；各分支只拥有自己的字段 |
| Active Test | 表达价格正在从什么方向检验哪个对象，以及当前 Stage、Acceptance / Failure Criterion 和 Horizon |
| Opportunity Set | 保存同一 Primary Test 下的向上、向下与 Pending 结果 |
| Market Path | 描述从当前测试到一个明确市场目标事件的条件路径 |
| Decision Record | 固定重要决策及其最小依据，并关联当时路径、规则和账户事实 |
| Trade Plan | 把一条 Market Path 转成当前时点完整的风险表达 |
| Execution State | 保存实际订单、成交、敞口和 Active Protective Stop |

图表事实、订单事实和账户事实分别保存。图表 Trigger 不能证明账户成交，价格触及 Limit 不能证明实际 fill，计划中的 Stop 也不能证明仓位已经受到保护。

Pattern 只是同一底层事实的结构、位置、次序或角色视图。H2、Double Bottom、Wedge、Flag、MTR 等名称若来自同一次运动、同一位置或同一测试次序，只形成一份证据簇，不选择另一套运行逻辑。

执行决定形成时保留原始 Trade Plan；首次实际成交对应这份计划。Execution State 随账户事实更新，不能写回原计划。后续新增风险不属于原计划层时，必须形成新的 Decision Record 和 Trade Plan。

### 三层使用接口

完整语义不等于完整填表。系统明确分成三层：

| 层 | 用途 | 盘中义务 |
| --- | --- | --- |
| 系统知识与内部模型 | 定义事实、对象、状态、路径、计划、执行和结果边界 | 必须被正确理解和遵守；不要求交易者逐字输出内部对象 |
| 实盘检查清单 | 数秒内提醒当前必须看什么、是否遗漏或冲突 | 观察、心中确认或快速勾选；已确认项可跳过，不因“检查过”而产生书面记录 |
| 必要记录 | 固定会改变计划、风险、账户事实或后续复盘的信息 | 只在关键节点保存最小充分增量；完整叙事留到盘后 |

**负担上限**：空仓扫描和持仓更新以数秒完成为目标。普通新 K 线若没有改变结构、路径、风险或动作，只继续观察，不产生记录。只有新建或实质修改计划、改变风险、发生执行事件、出现安全异常或交易结束时，才进入记录流程。

## 二、Safety Gate 与 Event Gate

### Safety Gate

每次运行先处理实际暴露，再考虑市场机会：

```text
账户与订单对账
> 未保护或保护不足的敞口
> 过期、失效或状态不明的工作订单
> 已有持仓管理
> 新增风险
```

账户状态不明、关键数据不完整或实际保护不足时，不新增风险；按预写异常路径核对、恢复保护、撤单、减仓或退出。

### Event Gate

系统只处理能够改变风险、判断或下一观察条件的相关事件：

| 事件 | 处理 |
| --- | --- |
| Safety Event | 成交、拒单、撤单、部分成交、保护或基础设施异常；立即处理实际暴露 |
| Observation Event | 观察 K 线完成，重要区域被接近、触及、越过、重新进入，或 Entry、目标、时间条件发生；增量更新 |
| Reframe Event | 主要 Frame、Environment 或 Primary Test 被解决、失效或替代；完整重构 Market Model 与 Opportunity Set |

初始化和 Reframe Event 才要求完整重扫。普通 Observation Event 从上一次判断出发，快速检查新事实是否增强、保持、削弱、完成或否定已有路径。若对结构、路径、风险、动作和下一观察条件均无实质影响，无需记录；有影响时只保存最小增量。认知可以改变而不产生交易动作。

## 三、看图主链：从可见事实到当前判断

拿到一张图时从本节开始。不先猜 Pattern、方向或 Entry，而是依次回答“边界是什么—市场处于什么环境—价格在哪里—眼前怎样运动—正在测试什么—接下来可能怎样”。下列内容是观察顺序和遗漏检查，不是书面表单。完整定义见[市场结构与结果路径](market_structure_and_paths.md)。

### 完整扫描的运行主线

```text
Frame
→ Environment
→ Location Map
→ Price Action Now
→ Active Test
→ Up / Down / Pending Paths
→ Market Gate
→ Risk Plan
→ Execution Gate
→ 当前账户状态允许的唯一动作
```

### 各阶段怎样运行

初始化或 Reframe 时依次完成以下步骤。盘中只观察和判断；某一步已经足以排除交易时，直接得到 Wait / No Trade，仍可继续观察市场，但不构造后续计划。

#### 1. Frame｜先固定本次判断边界

1. 固定 Trading Timeframe；scalp 使用更小 Entry 图时，也要保留实际承担风险的管理周期。
2. 只读取会改变本次目标、正常回撤或 Stop 的 Relevant Outer Constraint。
3. 检查 Session、已知事件、剩余时间和最迟退出时点。

产出是一句固定边界，例如：`5m 管理；外层仍是多头运动；本次只评价收盘前 40 分钟内可完成的路径。`

#### 2. Environment｜判断交易周期怎样组织价格

按顺序判断：

1. `Regime`：Trend / Trading Range / Unclear；
2. `Direction`：Bull / Bear / Neutral；
3. `Phase`：Breakout Phase / Channel / Developing Range / Mature Range；
4. `Variant`：Tight / Broad / Micro / Small Pullback / Triangle / Expanding 等；
5. `Modifiers`：当前是否存在 Breakout Mode、Climax 或 Transition。

产出只需能够约束正常波动和路径预期，例如：`Broad Bull Channel，正在出现 Transition evidence`。无法区分 Trend / Range 时使用保守 fallback，不为得到完整标签而延迟后续观察。

#### 3. Location｜建立有角色区分的位置地图

按四步建立位置地图：

1. **确定当前所在区域**：价格处于哪个趋势腿、通道、区间、突破区或压缩区；位于其上缘、中部、下缘，还是已经在边界外。
2. **扫描参考来源**：只找当前 horizon 内可能改变测试、目标、空间或失效的区域：
   - 外层与 Session：前日 / 当日高低、开盘、opening range、session gap；
   - 当前结构：swing high / low、区间边界与中部、趋势线、通道线；
   - 当前运动：突破点、回调起点、未关闭 gap、可见入场区域；
   - 动态参照：EMA 等当前仍在组织价格的区域；
   - 投射区域：事前固定的 measured move、Leg 1 = Leg 2 等目标候选。
3. **合并并排序**：落在同一价格带的参照合并成一个区域；其余分别按当前价格上方、下方及距离排列。
4. **赋予当前角色并计算空间**：标出 Active Area；分别标出两侧 First Obstacle、Magnet、Target Candidate、Acceptance Reference 和 Re-entry Reference；再计算上下两侧到首个障碍和目标候选的空间。

最终位置地图为：

```text
Location Map
├─ Current Region：当前正在交易的区域
├─ Position in Region：上缘 / 中部 / 下缘；边界内 / 外；突破点上 / 下
├─ Active Area：价格正在接近、触及、越过或重新进入的区域
├─ Above Price（按距离排序）
│  ├─ First Obstacle：上行首先必须穿越的区域
│  ├─ Magnet：可能吸引价格、但未必适合作为计划目标的区域
│  ├─ Target Candidate：结构生成的上行目标候选
│  ├─ Acceptance Reference：评价上方接受所使用的价格区域
│  └─ Re-entry Reference：评价上破后是否回到旧区所使用的价格区域
├─ Below Price（按距离排序）
│  ├─ First Obstacle：下行首先必须穿越的区域
│  ├─ Magnet：可能吸引价格、但未必适合作为计划目标的区域
│  ├─ Target Candidate：结构生成的下行目标候选
│  ├─ Acceptance Reference：评价下方接受所使用的价格区域
│  └─ Re-entry Reference：评价下破后是否回到旧区所使用的价格区域
└─ Available Space
   ├─ Up：到上方首个障碍；到上方目标候选
   └─ Down：到下方首个障碍；到下方目标候选
```

旧高低、区间边界、突破点、gap 边界、EMA、趋势线或通道线都先作为价格区域进入这张地图，再根据当前运动承担具体角色。同一区域可以同时是旧高、区间边界和 Double Top 区域，但图上仍只有一个价格区域。产出应能直接回答：**现在位于哪里；正在与哪个区域互动；上方和下方首先会遇到什么；两侧分别还有多少空间。**

#### 4. Price Action Now｜读取价格怎样到达并怎样回应

1. `Current Move`：当前是向上 / 向下 Leg、Pullback 还是 Pause；
2. `Bar / Leg Quality`：实体、收盘、影线、连续性和回调深度；
3. `Separation`：相对哪个对象形成 gap，正在 Holding、Closing 还是 Closed；
4. `Overlap`：正在增加、稳定还是减少；
5. `Response`：触及或越过 Active Area 后是 Follow-through、Rejection、Re-entry 还是尚无反应；
6. `Pressure`：Buying、Selling 或 Mixed；
7. `Control`：Bull、Bear、Balanced 或 Unclear。

产出是一句当前事实，例如：`第三次上推到前高，重叠增加，上方没有保持 separation，卖压出现但控制尚未反转。` 普通新 K 线只检查这些事实是否相对上一判断发生实质变化。

#### 5. Active Test｜把当前位置与当前反应组成一个问题

1. 从 Location.Active Area 选择当前直接测试的 Object / Boundary；
2. 明确 Approach Direction；
3. 更新 Stage：Approaching / Testing / Pending / Accepted / Failed / Superseded；
4. 写清 Acceptance Criterion 和 Failure Criterion；
5. 固定 Horizon；
6. 若另一个测试可能取代当前问题，保留一个 Competing Test。

结构名称只在帮助回答下一步时调用：Sequence 判断这是第几次尝试；Geometry 判断是重复测试、收缩还是扩张；Role / Process 判断它在延续、区间或反转过程中承担什么作用。H2 / Double Bottom、三推 / Wedge 等若只是同一次测试的不同描述，只用于形成一个路径判断。

产出必须是一句可解决命题，例如：`价格正从下方测试前高；前高上方保持并有跟随才算 Accepted，跌回旧区域并保持接受则本次上破 Failed；收盘前 20 分钟内解决。`

#### 6. Paths｜分别展开上行、下行与继续未决

对三个结果分别展开：

```text
Up Path
├─ Target Event：向上要发生的可观察结果
├─ First Obstacle：到达目标前首先必须处理的上方区域
├─ Required Sequence：从当前测试到目标需要怎样发展
├─ Next Evidence：下一根或下一事件期待什么
├─ Invalidation：什么事实实质否定这条路径
├─ Horizon：最迟何时发生
└─ Probability Status：适用规则、近似语言或尚不可匹配

Down Path
├─ Target Event：向下要发生的可观察结果
├─ First Obstacle：到达目标前首先必须处理的下方区域
├─ Required Sequence：从当前测试到目标需要怎样发展
├─ Next Evidence：下一根或下一事件期待什么
├─ Invalidation：什么事实实质否定这条路径
├─ Horizon：最迟何时发生
└─ Probability Status：适用规则、近似语言或尚不可匹配

Pending Outcome
├─ Unresolved Form：测试继续重叠、压缩、回踩或反复越界的方式
├─ Re-evaluation Event：在哪个价格或事件重新判断
├─ Expiry：何时因 horizon 结束而过期
└─ Supersession：什么新测试会取代当前 Pending
```

只有目标、到达顺序、下一证据、失效和 horizon 对得上的路径，才匹配相应条件概率。缺少现实目标或可用空间的方向只保留排除原因，不构造 Trade Plan。

#### 7. Market Gate｜这条路径现在能否交易

- 选择哪条 Market Path；
- Entry 所在 Location 是否合理；
- 到首个障碍和目标的空间、剩余时间是否足够；
- Price Action Now 是否满足该路径所需的当前条件。

任一必要条件缺失时，结果是 Wait 或 No Trade，不进入 Risk Plan。

#### 8. Risk Plan｜怎样表达这条路径的风险

- Entry 条件；
- 订单类型；
- 订单有效期与取消条件；
- Structural Invalidation；
- Planned Stop；
- Planned Target；
- Outcome Criterion；
- Gross Reward；
- Initial Risk；
- 手续费、点差与预期滑点；
- 剩余时间和持仓时间风险；
- Trader's Equation 是否成立。

Entry、Invalidation、Stop、Target 或 Size 不能同时成立时，计划不完整，不提交订单。

#### 9. Execution Gate｜账户与执行条件是否允许

- Position Size 与最坏总风险；
- 已有仓位、工作订单和相关敞口；
- 成交后 Active Protective Stop 怎样覆盖实际数量；
- 关键行情与账户数据是否完整；
- 连接和订单通道是否正常；
- 当前流动性、点差和订单类型是否能可靠表达计划。

账户状态不明、保护无法建立或最坏风险超限时，不新增风险；先核对、恢复保护、撤单、减仓或退出。

#### 10. Action｜按当前账户状态选择唯一动作

- Flat：Execute / Wait / No Trade；
- Working Order：继续工作 / 修改或撤单 / 先对账；
- Open Position：持有 / 停止新增风险 / 减仓 / 移动保护 / 退出；
- Safety Exception：中断市场评价，先恢复保护或确认真实暴露。

产出是当前唯一动作及其下一触发条件。形成 Execute、需要持续跟踪的 Wait / No Trade，或风险实质改变时，按[必要记录与闭环](#七必要记录与闭环)保存最小计划或 Delta。

Gap 不是每次必须找到的 Setup；只在当前运动存在可见分离或闭合时更新 `Price Action Now.Separation`。同一根强突破 K 线的大实体、强收盘、gap、Pressure 和 Control 仍是一条价格事实链，不是五票。

Trend / Range 无法分时先按 Range；Broad Channel / Range 无法分时也先按 Range。Candidate measuring gap、potential exhaustion、final flag 和已确认 climax 不得用后续结果回填当前。

### 进入交易计划前的遗漏扫描

在寻找 Entry 之前只做一次快速反查：

- 我是否临时换了周期、目标或管理方式？
- 是否忽略了最近的重要区域、magnet、gap 关闭或前方障碍？
- 买卖 Pressure / Control 是否真的支持所选路径，还是我只看到了 Pattern？
- `Environment.Regime / Phase / Variant / Modifiers` 是否分类正确，`Active Test.Stage` 是否处于 Testing / Pending / Accepted / Failed / Superseded？
- H2 / Double Bottom / Flag，或三推 / Wedge / Broad Channel 是否只是同一价格链的多个名称？
- 反路径怎样才算获得接受？如果现在不能回答，不应承担风险。
- 目标空间、剩余时间、成本和执行可靠性是否允许这条路径被交易？

这七问是防遗漏的最后一眼，不是证据评分器。某项不相关时直接跳过；某项未知且会改变风险时，结果是等待或不交易，不是填写一个假答案。

## 四、建立并更新双向路径

每个 Primary Test 都从三个问题展开：

| 问题 | 证据范围 |
| --- | --- |
| 价格在哪里？ | Frame、Environment、Location、前方障碍和剩余时间 |
| 价格怎样到达？ | Push、Leg、Pullback、H/L、Gap、Overlap、Pressure 与 Control |
| 市场怎样回应？ | Touch、Reaction、Breakout、Follow-through、Acceptance 与 Failure |

然后建立：

```text
Opportunity Set
├─ 向上路径
├─ 向下路径
└─ Pending Outcome
```

双向考虑的最低要求是说明：双方为什么可能承担风险、各自期待什么市场目标、需要什么后续证据，以及在哪里被证明错误。Pending Outcome 描述当前测试继续未决的现实方式。明显缺少目标、空间、时间或必要条件的方向识别排除原因即可，不为形式完整制造伪路径，也不必为双方都构造 Trade Plan。

每条值得跟踪的 Market Path 绑定来源测试、目标事件与到达口径、周期、horizon、支持与最强反方事实、下一预期、增强和削弱条件、失效条件及适用概率。路径生命周期为：

```text
ACTIVE
├─ 目标事件发生             → ACHIEVED
├─ 市场事实实质否定         → INVALIDATED
├─ horizon 结束             → EXPIRED
├─ 新结构或测试取代         → SUPERSEDED
└─ 目标与失效顺序无法确认   → SEQUENCE_UNKNOWN
```

增强、保持和削弱是 `ACTIVE` 内一次事件的更新结果，不是生命周期状态。市场路径是否有效也不等于当前是否值得交易：账户预算、Entry、成本、时间或目标空间只能使 Trade Plan 不成立，不能改写市场目标本身。

## 五、比较风险表达并作出决定

概率只属于明确的条件、目标事件、周期、horizon 和判断时点。规则匹配与替代见[条件规则台账](conditional_rules_registry.md)。理由数量不生成概率；结构生命周期概率、市场目标概率和账户盈利概率不是同一对象。

规则台账保存的是可匹配模板、背景和隔离项，不是可以直接抄入计划的百分比。当前路径只有完成以下实例化后，才取得一条适用规则：

```text
候选规则模板
→ 固定当前已经成立的条件、目标事件、周期、horizon 与判断时点
→ 检查是否存在相同目标下更具体的新条件
→ 排除 Background、隔离或字段不完整的模板
→ 形成当前 Rule Match；否则使用诚实的近似语言或等待
```

系统先独立评价双向 Market Paths，再按照[交易决策与计划](decision_and_plan.md)为当前可交易路径构造：

```text
Market Path
+ Entry
+ Invalidation / Planned Stop
+ Target / Outcome Criterion
+ Cost / Time
+ Position Size / Management
+ Execution Reliability
= 当前风险交换
```

选择的不是理由最多、裸概率最高或最熟悉的一侧。即使一侧市场目标更可能发生，当前 Entry 太差、Stop 太远、成本太高或剩余空间不足时仍可等待或不交易。

决策只有三种：

| 决定 | 含义 | 后续 |
| --- | --- | --- |
| 执行 | 当前 Trade Plan 完整且方程成立 | 保留原始计划并提交计划规定的订单意图 |
| 等待 | 路径仍现实，但缺少已声明的必要事实或完整计划 | 明确所等事实和过期条件；只在形成需后续跟踪的正式等待决定时简记 |
| 不交易 | 已知条件使当前交换不值得承担 | 关闭本次评价；新结构、新 Entry 或新时点建立新判断 |

等待不保留隐藏的可执行计划。未来 Trigger、Follow-through 或更好价格出现时，使用当时事实重新构造；预先提交并等待触发的 Stop / Limit order 已属于执行状态。

## 六、按 Execution State 分派动作

执行生命周期由[执行、持仓与复盘](execution_management_and_review.md)负责。订单、敞口和保护是三个可以并存变化的状态面：

```text
Order State：Intent / Submitted Unknown / Working / Partial / Filled
             / Cancel Pending / Canceled / Rejected / Expired
Exposure：Flat / Open(quantity) / Exiting(quantity)
Protection：Not Required / Pending / Adequate / Deficient
```

共同顺序为：

```text
提交订单
→ 确认订单状态
→ 确认实际成交与数量
→ 确认 Active Protective Stop 覆盖实际仓位
→ 持仓中继续更新所选路径、对手路径与 Pending Outcome
→ 目标、Invalidation、Stop、时间或账户条件结束风险
→ 确认仓位归零和剩余订单清理完毕
```

撤单请求、退出请求或 Stop 触发都不等于风险已经结束。部分成交可以同时存在实际持仓、剩余工作订单和待确认保护；确认最终账户事实前按可能发生的最坏暴露管理。

持仓中的每个相关事件先更新认知，再按原计划与当前账户状态映射动作：

| 路径变化 | 动作边界 |
| --- | --- |
| 增强或保持 | 按计划持有；不自动增加风险 |
| 削弱但未失效 | 停止新增风险；按预写分支保持、减仓或收缩管理目标 |
| 对手获得接受或所选路径失效 | 取消剩余新增风险并主动退出；归零前保护继续有效 |
| 目标、Stop 或时间条件发生 | 按 Outcome Criterion 处理并核对实际剩余仓位 |

退出原方向不自动许可反向交易。反方向必须以当前事实重新经过目标、概率、Entry、Stop、仓位和方程检查。

计划内 Scale-in 可以来自预写的更好价格，或成交后出现的新确认；前者改善价格但不提高路径概率，后者提供新证据但仍增加账户暴露。所有层必须在第一笔新增风险前进入最坏总风险，执行时仍要求原路径有效、保护正常且总风险合规。计划外新增风险必须建立新计划。

## 七、必要记录与闭环

不要把“交易者必须检查的内容”都转化为“交易者必须书面记录的内容”。系统对信息的处理分为：

| 信息类型 | 实盘处理 |
| --- | --- |
| 当前 Environment、Location、Pressure、反方事实 | 观察或心中确认；无变化不记录 |
| 安全项、计划完整性、重复计数、状态冲突 | 快速勾选或扫描；通过即结束，不保存勾选记录 |
| 新结构实质改变路径、下一观察条件或当前动作 | 只记录变了什么及下一条件 |
| 形成 Execute / Wait / No Trade，或计划、目标、失效点、仓位、风险实质改变 | 保存最小 Decision Record |
| 成交、拒单、部分成交、撤单确认、保护异常、减仓或退出 | 保存账户和执行事实；能由经纪商或平台可靠留存时不重复抄写 |
| 交易或路径结束 | 实盘只先保存终结事实；盘后完成最小 Review Record，异常或校准样本再展开 |

最小决策记录只需固定：

```text
时点 + 品种/周期
决定：Execute / Wait / No Trade
依据：Environment / Location + 所选路径或排除原因（一短句）
边界：目标 + 最强反方/失效条件
计划（如执行）：Entry + Stop + Target + Size
下一条件：触发 / 过期 / 重构
```

只在实质修改时记录 Delta，不重抄未变字段。完整 Decision Record 是[交易决策与计划](decision_and_plan.md#decision-record)拥有的内部契约和复杂场景模板，不是每个事件的默认人工表单。等待与不交易若用于连续样本，只保留上述最小依据，不为空白 Trade Plan 填充不适用字段。

结果分别闭环：

- `Market result`：目标路径实际达成、失效、过期、替代或顺序不明；
- `Trade outcome`：实际 Entry 后各计划结果发生的顺序；
- `Account result`：实际成交、数量、费用、滑点、退出和 P&L；
- `Process result`：正常不确定结果，或违反系统契约。

没有实际成交的机会不能记为交易成功或失败，但其 Market Path 仍须在 horizon 结束时闭环。持仓归零后还要确认剩余订单已清理、保护已撤换，单次交易才真正结束。

规则校准是独立的离线闭环：使用条件、目标、周期、horizon 和判断时点一致的连续样本，区分市场、交易、账户和流程结果，再登记规则修订的生效时间与替代关系。单笔赢家、输家或错过不能直接修改概率，后来的规则不能回写历史判断。

## 八、实盘界面：看图主链与账户状态叠加

先按事件强度选择看图清单，再叠加当前的订单/持仓清单。这些问题用于观察和防遗漏，不是表单。

无论使用哪个清单，第一眼总是：**当前订单、实际仓位、保护和关键数据是否一致？** 不一致就直接进入异常状态，不继续市场分析。

### 初次看图或 Reframe：完整六问

1. **Frame｜判断边界**：交易周期、真正相关的外层约束和剩余时间是什么？
2. **Environment｜市场处境**：当前是 Trend、Trading Range 还是 Unclear？方向、阶段、变体和必要 Modifiers 是什么？
3. **Location｜价格在哪里**：当前区域及内部位置是什么？Session / 外层、结构、突破 / gap、动态参照和投射区域中，哪些与当前 horizon 有关？上方、下方按距离首先遇到什么，各有多少空间？
4. **Price Action Now｜眼前怎样运动**：腿、回调、gap / separation、重叠、跟随和买卖压力说明哪一方正在取得或失去控制？
5. **Active Test + Views｜正在测试什么**：Object、Approach Direction、Stage、Acceptance / Failure Criterion 和 Horizon 是什么？H2、Double Bottom、Wedge 等视图是否只是在解释同一测试？
6. **Paths｜接下来怎样**：向上、向下和 Pending 各自怎样发展；最强反方事实、反方接受和当前路径失效分别是什么？

六问的产出压缩为一句当前市场读取，例如：**5 分钟外层多头约束下的宽多头通道正在前高测试；第三推 / Wedge 是同一次测试，重叠增加且尚无上方接受，因此保留双向路径并等待。** 完整展开见[流程演练](worked_examples.md)。

### 普通新 K 线：只问三个 Delta

1. **Location / Price Action Now 变了吗**：价格是否接近、触及、越过或重新进入重要区域？新的 gap / 关闭、重叠、follow-through 或买卖 Pressure 是否改变 Control？
2. **Environment / Active Test 变了吗**：上述事实是否改变 Regime / Phase / Variant / Modifier，或使测试进入 Accepted / Failed / Superseded？
3. **Paths / Gates / Action 变了吗**：所选路径、反路径、Pending、市场资格、风险计划、执行条件或下一动作是否跨过原边界？

三问均为“没有”就结束：继续观察或持有，不重跑完整六问，不记录。任一答案为“有”，只回到受影响的步骤；主要 Frame、Environment 或 Primary Test 改变才触发完整 Reframe。

### 准备下单

- 我正在交易哪一条明确路径？目标、horizon 和所用条件规则是否对应同一事件？
- 位置、空间、时间、成本和盈亏比是否足够？
- Entry、Invalidation / Stop、Target 和 Position Size 是否明确？
- 订单类型、数量、有效期和成交后保护是否一致？
- 最强反方事实是什么？当它出现时做什么？

提交前保存最小执行计划；只有多层仓位、多目标、条件管理或异常路径复杂时，才展开完整 Trade Plan。

### 订单工作中

- 订单是 Working、Partial、Cancel Pending 还是状态不明？
- 路径、价格范围、有效期和总风险是否仍有效？
- 若现在成交，实际数量会否立即获得足量保护？
- 现在真正需要继续工作、撤单，还是先对账？

订单和回执由平台留存；只在状态异常、取消原因非显然或计划/风险改变时补充最小说明。

### 持仓管理（每个相关事件数秒扫描）

- 实际数量和 Active Protective Stop 是否一致？
- 所选路径是增强、保持、削弱还是已失效？
- 反路径只是增强，还是已经获得接受？
- 当前波动是原计划允许的正常发展，还是改变了前提？
- 现在真正需要持有、停止加风险、减仓、移动保护还是退出？

保持原动作且无实质变化时不记录。只在改变风险、保护、数量、目标、管理方式或退出时保存 Delta 和执行事实。

### 异常状态（中断市场评价）

- 账户真实净仓位和可能最坏暴露是什么？
- 是否有订单不明、部分成交、双向成交、保护缺失或数据中断？
- 应当核对、恢复保护、撤单、减仓还是退出？
- 在确认安全前，是否已阻止所有新增风险？

异常必须记录当时实际状态、采取动作和确认结果；处置完成前不返回新机会评价。

## 九、系统不变量

- 所有方向使用同一套 Frame、Environment、Location、Active Test 和证据更新；系统不按 Pattern 或 Setup 切换流程。
- 每个现实 Primary Test 都考虑向上、向下和 Pending 结果；双向考虑不要求双向同时交易。
- 没有明确市场目标事件，不匹配 Market Path 概率，也不建立 Trade Plan。
- 一个概率必须绑定条件、目标、周期、horizon 和判断时点；同源名称不重复计数。
- 规则模板和背景数字不能直接进入 Trader's Equation；只有当前字段完整且未被更具体条件替代的 Rule Match 可以使用。
- 一个 Trade Plan 只表达一个 Primary Test、一条 Market Path 和一个判断时点。
- 市场路径失效、交易计划失效和执行异常分别记录，并产生各自的动作。
- 每个相关事件可以改变认知而不改变动作；普通波动不自动触发加仓、减仓或退出。
- 没有实际成交就没有持仓，没有可确认的保护就不能假定风险受控。
- 实时候选、原始判断和后续更新分别保存，最终结果不能回填当时理由。
- 等待、不交易、未成交路径、实际交易和规则样本都有各自的闭环。
