# Market Read 与 Opportunity

> **状态：Trading System / Market Model**

本页定义 `Market Read = Context + Price Map + Price Process` 怎样从连续价格事实形成，以及它怎样生成可证伪的双向 `Opportunity Set`。Price Process 在实盘中按 `Current Move → Active Test` 读取；连续运行时先继承当前有效 Context，再以位置、运动和测试的新事实确认或重构它。首次看图或 Reframe 可从暂定分类或 `UNCLEAR` 开始。

本页是系统知识与内部模型，不是盘中标注任务。下文的区分首先是语义边界；交易者通常只需观察或心中确认，记录负担由[总流程](overall_flow.md#六必要记录)规定。

## 一、统一价格命题

市场不断在旧公平区域与可能的新公平区域之间测试：

```text
方向运动创造分离
→ 回调或反向尝试检验分离
→ 新区域获得接受：控制保持或建立，价格寻找下一目标
→ 分离被关闭：控制减弱，价格返回旧区域或进入双边状态
→ 反方在另一侧获得接受：旧路径失效，结构重新分类
```

Trend、Trading Range、Gap、Breakout、Failed Breakout、H2、Double Bottom、Wedge、Flag 和 MTR 都是这条测试链在不同周期、次序、空间或外层约束中的描述。

## 二、概念的形成契约

系统中的概念必须能够回答：

```text
来源事实是什么？
在什么周期与观察窗口形成？
它在当前流程中承担什么职责？
什么新事实会增强、削弱、失效或重置它？
它不能单独推出什么？
```

不能从价格事实给出形成条件、更新条件和流程职责的名称，不进入运行系统。包含最终结果的名称必须区分实时候选和事后确认。

概念之间只使用五种关系：

| 关系 | 含义 | 示例 |
| --- | --- | --- |
| 本质归属 | A 是 B 的一种 | Channel 是当前周期 Trend 的阶段 |
| 同源视图 | 同一事件从不同维度命名 | H2 与 Double Bottom 可以描述同一第二次测试 |
| 外层角色 | 局部结构在外层路径中的作用 | Rising Channel 同时保留长期 Bear Flag 视角 |
| 条件演化 | 新事实改变当前解释 | Breakout Attempt → Acceptance → Breakout Phase |
| 周期展开 | 同一价格在不同尺度呈现不同结构 | 高周期 Breakout Bar 在低周期展开为 Channel / Range |

同源视图只产生一份证据。外层角色可以同时成立，但内部模型必须分开它们的周期、目标事件与 horizon。

## 三、原始价格事实

### 外部信息的边界

价格运动的任何表示都属于价格行为。Volume、DOM、新闻、NYSE TICK 等辅助指标和日程事件可以作为背景、流动性、时机或尾部风险输入，却不能独立保证方向；运行证据仍是这些信息怎样反映在突破、跟随、回调、接受或失败上。产品报价、pip、tick、保证金、rollover 和平台机制属于外部产品事实，只通过成本、仓位、订单和风险边界进入系统。数据中断、基础设施异常和已知事件风险进入运行边界与 Trade Plan，不因系统以价格反应为主而被忽略。

### K 线几何

设本根最高、最低、开盘、收盘为 `H`、`L`、`O`、`C`：

```text
总范围   = H - L
实体     = abs(C - O)
实体占比 = abs(C - O) / (H - L)
收盘位置 = (C - L) / (H - L)
上影占比 = [H - max(O, C)] / (H - L)
下影占比 = [min(O, C) - L] / (H - L)
```

`H = L` 时按零波幅 K 线处理，不计算比例。观察还包括：

- 方向、开高低收和相对附近 K 线的范围与实体大小；
- 与前一根、突破区域和局部结构的共享价格范围；
- 高低点相对前高前低的变化；
- 实体、影线和收盘变化是否具有连续性。

Trend bar 与 trading-range bar 是连续谱。实体相对大、影线较小、收盘靠近方向端点时更像 trend bar；小实体、大影线和重叠增加时更像 trading-range bar。单根 K 线不能建立趋势。

其他几何只承担局部描述：

- `Inside bar`：`high ≤ 前高` 且 `low ≥ 前低`；一端相等仍可成立；
- `Outside bar`：来源对相等边界存在不同口径，运行或标注必须预先声明使用严格越过还是允许两端相等；
- `Doji`：实体相对周围很小或为零；
- `Shaved`：实体一端与本根极值严格相等；若允许一跳容差必须另行声明；
- `Reversal bar`：相对当前 trend / leg 承担反向趋势或拒绝角色，必须结合方向、收盘、相对实体、位置和后续反应；
- `Two-bar / multi-bar reversal`：由两根或多根共同完成反向压力，不能用单一吞没几何覆盖全部课程用法。

几何名称不生成方向优势。强趋势中的顺势弱 bar 仍可能表达有效路径，错误位置的漂亮 reversal bar 也不能修复目标和交易方程。

### 价格运动

- `Push / Leg`：较大结构中一段具有方向的运动，不自动构成独立 Trend。
- `Pullback`：当前方向运动中的暂停或暂时反向运动；反向运动获得足够接受并改变结构后，不能继续只称旧趋势回调。
- `Pause`：停止扩展趋势方向极值或形成横向停顿。
- `Actual pullback`：当前周期已满足高低点反向运动的几何事实。
- `Implied pullback`：当前周期的停顿角色；在较低周期常已展开成实际回调，不能改写当前周期几何。

第二腿是条件路径倾向：第一腿足够强并使参与者期待延续时，市场常再尝试一次。第二腿可以很短、横向、未创新极值或很快失败；它不保证 `Leg 1 = Leg 2`，也不同于 second signal、second entry 或第二次实际成交。

### 参照区域

系统把以下对象视为区域而非精确屏障：

- 前高低、swing high / low、日周月已经形成的 OHLC；
- 区间边界、中部和内部公平区域；
- 突破点、旧结构起点和可见入场区域；
- 趋势线、通道线、EMA、大整数位；
- gap 边界和已固定结构生成的 measured-move 区域。

Support 位于当前价格下方，Resistance 位于当前价格上方；穿越后可以交换角色。位置本身不保证反转或突破。

多个来源相对独立的区域在相近价格与时间汇合，可以称为 confluence / Dueling Lines。若两条线由同一组 swing 推导，或旧高、区间上沿和 double-top 只是同一位置的不同名称，它们仍是一份位置证据。

汇合的运行作用取决于当前 Opportunity：当前价格处的多项支撑/阻力汇合可以增强停顿或反应倾向；前方多个事前固定投射汇合，可以增强目标区的 magnet 与到达后反应意义。它们都不单独生成 Entry，也不替代实际 rejection、breakout、follow-through、目标空间和当前 Market Probability。

### Price Map

相关区域进入同一张位置地图；同一价格带先合并，再按当前价格上方、下方和距离排序。当前运动正在到达、穿越或离开的区域优先进入 Active Area：

```text
Price Map
├─ Current / Active Area
├─ Above Price
│  └─ Region + Sources + Distance + Confluence
├─ Below Price
│  └─ Region + Sources + Distance + Confluence
└─ Nearest Relevant Area / Available Space：Up / Down
```

地图只唯一登记价格带、来源、汇合与距离。Active Area 是当前正在互动的区域；Potential Entry Area、Support / Resistance、Obstacle、Magnet、Target 和 Invalidation Reference 是相对某条 Opportunity 的运行角色。因此同一 `50%`、EMA 或旧高可以是一条机会的 Target，同时是另一条机会的 Potential Entry Area 或 Invalidation Reference；底层仍只保留一个价格带。Acceptance 与 Re-entry 属于 Price Process 事件，不是区域属性。

区域在以下任一条件成立时进入当前地图：价格正在互动；它是当前 horizon 的现实目标或障碍；它会改变正常 Stop、Invalidation、空间或动作；它是当前 Context 必须保留的外层约束。其他历史高低保持休眠，接近或获得新职责时再激活。

## 四、Price Process｜先读当前运动，再读活动测试

Price Process 保存前后关系，不把当前 K 线、位置反应或形态从其来源运动中截断。实盘分两步读取，内部仍属于同一连续过程。

### Current Move

```text
From：此前的方向运动、回调或区域反应
Now：UP_LEG / DOWN_LEG / PAUSE / LOCAL_BALANCE
Role：CONTINUATION / PULLBACK / RANGE_LEG / REVERSAL_ATTEMPT / UNRESOLVED
Bars：实体、收盘、影线与相对大小
Continuity：同向连续性与 follow-through
Separation：gap / breakout separation 与 overlap
Pullback：深度、持续时间、gap 与恢复速度
Opponent：反方 K 线质量、跟随与失败尝试
Result：Bull Pressure 变化；Bear Pressure 变化；Control 含义
```

Now 与 Role 分开：同一段 Down Leg 在多头方向状态中可能承担 Pullback 角色，在 Trading Range 中可能只是 Range Leg。`PAUSE` 尚未形成清楚方向腿；`LOCAL_BALANCE` 表示局部小区间已经比单腿或暂停更能组织价格。反向运动获得持续接受并改变外层正常回撤、目标或管理方式后，Role 才升级为新的 Context。

### Active Test

Current Move 与 Price Map 的互动形成当前要解决的问题：

```text
Object：正在测试哪个区域、边界或旧 Control
Stage：APPROACH / TOUCH / REACTION / BREAKOUT_ATTEMPT /
       FOLLOW_THROUGH / ACCEPTANCE / FAILURE / PENDING
Attempt：当前逻辑中的第一次、第二次或第三次尝试
Scale：外层位置测试与局部触发测试
Response：分离、拒绝、突破、重叠或重新进入旧区域
Next：什么事实表示接受、拒绝、Activation、失败或重构
Expiry：最迟何时当前问题仍有意义
```

外层位置决定这次测试可能承担的市场作用，局部测试次序和反应决定是否形成当前 Trigger。默认只展开当前 horizon 的这两个尺度；新增尺度必须改变目标、正常波动、失效或动作。

所有边界互动按同一顺序更新 Stage：

```text
Approach
→ Touch / Overshoot
→ Reaction 或 Breakout Attempt
→ Follow-through / No Follow-through
→ Acceptance / Failure / Still Pending
```

- `Approach`：正在接近区域，尚未触及。
- `Touch / Overshoot`：触及或短暂越过，只确认测试事件发生。
- `Reaction`：停顿、拒绝、反向或加速，结果仍可能缺少延续。
- `Breakout event / attempt`：高低点越过重要边界；此时新区域是否被接受仍未知。
- `Follow-through`：初始运动后，后续一根或多根继续延伸。
- `Acceptance`：边界外收盘、跟随、保持在外或回踩守住等证据支持新价格；它是证据状态，不直接许可交易。
- `Failure`：原目标路径未获得接受并被新价格实质否定；必须明确失败的是哪个 move 或 objective。

没有立即 follow-through 会削弱路径，但普通回调不自动确认失败。Failed breakout 要求旧区域被重新接受；若反向尝试随后失败、原突破方向重新获得接受，则形成 failed failure / breakout-pullback 路径。

### Process Question

Price Process 最后把 Current Move 与 Active Test 压缩成一句双向问题：

```text
当前运动从哪里来，质量怎样？
正在测试哪个区域，是第几次、哪个尺度的尝试？
怎样算在外侧获得接受？
怎样算拒绝、失败或重新接受旧区域？
下一事实和 Expiry 是什么？
```

例如：`强空头腿第三推延伸缩小，反弹后第二次下探卖压更弱；旧低下方会获得接受，还是多头先建立修正？`

H2、Double Bottom、Wedge、Flag 或 MTR 只在它们帮助说明 Attempt、Scale、几何、外层作用、目标或失效时附在这个过程上。价格进入新区域或 Context 重新分类时，新的 Current Move / Active Test 取代旧问题；旧结构只保留对新目标或正常回调仍有作用的部分。

发生关键变化时，用[市场决策事件导航](market_decision_events.md)确定只需重开哪些步骤。事件卡压缩常见过程，不拥有独立状态、概率或入场许可。

## 五、压力与状态更新

每个相关事件先更新 Price Map、Current Move 或 Active Test，再汇总 Pressure / Control：

```text
新的区域、运动或测试事实
→ Bars：实体、收盘、影线与相对强度
→ Continuity：同向连续性与 Follow-through
→ Separation：Gap 保持/关闭与 Overlap
→ Pullback：深度、持续时间、Gap 与恢复速度
→ Opponent Response：反方 K 线质量、跟随与失败尝试
→ Bull Pressure 变化 + Bear Pressure 变化
→ Bull / Bear / Balanced / Unclear Control
→ 确认原 Context、标记 Transition 或 Reframe
→ Long / Short Opportunity 或 Likely Sequence 是否改变
```

使用能回答当前过程的最小时间窗口：当前腿、当前区域测试，或上次 Reframe 以来。更早或更高周期事实留在 Context，不混入眼前 Pressure。

事实按来源价格链合并。一个强突破产生的大实体、强收盘、gap、Pressure、Control 和 Acceptance 可以影响机会的多个环节，但仍只是一条价格链。新的二次测试、后续 follow-through、反方尝试失败或独立价格区域才可能提供增量。

### Separation / Gap

Gap 的最低职责是描述两个价格对象之间是否保持分离。识别 Gap 时必须明确比较对象和边界：

- 完整范围 gap；
- body gap；
- micro gap；
- breakout point 与回调之间的开放、negative 或 overlap gap；
- 整根 K 线未触及 EMA 的 moving-average gap bar；
- session opening gap 或单根 `open` 相对前 `close` 的 Gap Open Bar。

这些名称不能互换。完整、实体、微型和 EMA 分离若来自同一次运动，只属于一个 Separation 证据组。运行更新使用：

- `NOT_RELEVANT`：当前窗口没有需要评价的分离关系；
- `NOT_PRESENT`：比较对象明确，但当前没有开放分离；
- `EXPANDING / HOLDING / CLOSING / CLOSED`：已经存在或刚刚关闭的分离怎样变化。

`CLOSED` 保留“先前存在、现在关闭”的事件语义；初始化时本来就没有 gap 使用 `NOT_PRESENT`。两者都要结合旧区域是否重新获得接受解释。

```text
Gap 保持且跟随良好
→ 原方向分离与控制增强

完整 gap 关闭但 body gap 保持
→ 原方向减弱但未失败

所有分离快速关闭并重新进入旧区域
→ 延续路径削弱，通道化或区间化增加

关闭后反方获得跟随
→ 原突破路径失效或重新分类
```

Measuring gap 与 exhaustion gap 含有事后结果。实时只能记录 candidate measuring gap 或 potential exhaustion；前者需要后续 measured move，后者需要后续停止延续、区间化或反转结果。Gap 不因“迟早回补”自动成为目标。

Moving-average gap bar 的两个常见语境不能混用：整根 K 线位于 EMA 反侧是严格几何；长期约 20 根未触 EMA 后的首次测试则是时间与趋势背景。前者可以增加反方压力，后者常仍保留原趋势测试旧极值的路径；两者都不机械生成 Entry。

### Pressure / Control / Always In

Bull / Bear Pressure 分别汇总同一段窗口中的可观察事实：

- 顺势 K 线、实体和强收盘的数量与连续性；
- 反向影线和失败尝试；
- breakout、gap、follow-through 与是否快速收回；
- pullback 深度、持续时间和恢复速度；
- 反方能否获得 scalp 或持续路径。

同一根 K 线的“大实体、强收盘、顺势 K 线”不能算成三个独立理由。每次更新分别回答两侧是增强、保持、减弱还是尚未建立；一侧减弱不自动等于另一侧建立。Pressure 是事实簇的方向汇总；一侧明显占优才支持 Control，控制足够强时才支持 Always In。Always In 不是必须持仓，也不能替代位置、目标和交易方程。这是观察输出，只有它改变 Opportunity、计划或动作时才记录。

通常需要足够强的反向运动和跟进改变 Always In。单根异常强反转只有在方向、相对强度、重要位置和对旧控制的否定同时清楚时，才可能直接完成切换；普通反色 K 线不够。

### 从事件到状态转换

证据增强或削弱不一定立即改变外层状态。只有新事实开始改变正常回撤、目标、两侧获利能力或管理方式时才重分类：

| 当前外层状态 | 累积的新事实 | 状态更新 |
| --- | --- | --- |
| Breakout / Spike | 出现第一次可识别回调，分离仍较好 | Tight Channel |
| Breakout / Spike | gap 缩小或关闭、Overlap 增加，但尚无完整回调 | 原状态减弱；标记 Transition，不抢先改名 |
| Tight Channel | 回调反复加深、穿回突破点，双边开始获利 | Broad Channel |
| Broad Channel | 相邻突破与回调重叠、延伸缩小 | Staircase / shrinking-stairs 视图；区间化增强 |
| Broad Channel | 局部区间经短突破迁移到新区间 | TTR 可以成为主导状态；若仍由方向 swing 支配，只作同源视图 |
| 任一方向状态 | 双方持续在同一公平区域获得接受，单边控制无法保持 | Trading Range |
| Trading Range / Breakout Mode | 强突破、跟随并守住区间外 | Breakout / Spike |
| Trading Range | 突破尝试后重新接受旧区域 | 保持 Trading Range，测试记为 FAILED |

这张表规定转换条件，不规定机械根数，也不是不可逆的单向周期。

## 六、Context｜继承后由当前过程确认

Context 只保存当前交易周期真正支配目标、正常回撤和管理方式的价格组织：

```text
Context
├─ Operating State
│  ├─ BREAKOUT_SPIKE
│  ├─ TIGHT_CHANNEL
│  ├─ BROAD_CHANNEL
│  ├─ TRENDING_TRADING_RANGE
│  ├─ TRADING_RANGE
│  └─ UNCLEAR
├─ Direction：BULL / BEAR / BALANCED / UNCLEAR
├─ Range Condition（仅 TRADING_RANGE）
│  ├─ Width：TIGHT / BROAD / UNCLEAR
│  └─ Maturity：DEVELOPING / MATURE / UNCLEAR
└─ Overlays：BREAKOUT_MODE / CLIMACTIC_MOVE_CANDIDATE / CONFIRMED_CLIMAX / TRANSITION
```

Operating State 在当前 horizon 内只选择一个主导值。Range Condition 只在 `TRADING_RANGE` 下启用，不恢复跨状态的通用 Variant。Broad Channel 与 Trending Trading Range 同时可见时，选择真正决定正常回撤、目标与管理的一项，另一项只作同源视图。只解释某段过程的第三推、Wedge 或局部 Triangle 留在 Price Process；Session 属于 Context。

连续观察中的 Context 是上一次确认结果，也是本次 Price Process 的比较基线；它不是无需复核的先验结论。普通新事实没有跨过正常回调、目标、Control 或双边获利能力边界时保持原值；跨过边界才按上节转换表更新。首次看图没有可继承状态时，先用相关窗口作暂定分类，无法确认就保留 `UNCLEAR`。

分类依据是回调深度和持续时间、Overlap、Separation 是否保持、双边获利能力，以及新旧公平区域是否仍在方向迁移。`UNCLEAR` 是允许结果；Overlay 只描述当前附加条件，不与 Operating State 并列计数。

### 方向状态

方向状态表示市场持续寻找更高或更低价格，一侧控制明显、反方尝试经常失败。Breakout / Spike 是接受证据已经建立方向控制且几乎没有回调的阶段；第一次可识别回调使当前状态进入 Channel，但不结束整个方向运动。

Channel 是 Trend 的方向结构：

- Tight Channel 回调浅、重叠少、分离保持，第一次逆势尝试通常先按 minor 处理；
- Microchannel 是没有明显回调、每根顺势极值持续推进的局部 tight-channel 表现；Small Pullback Trend 则持续以浅回调、保留 gap 或反方难以获利维持控制。两者只增强当前延续路径，不保证任意位置都值得入场；
- Broad Channel 回调更深、更久、常穿回突破点，双边逐渐都能获利；
- Staircase 表示相邻突破与回调开始重叠；shrinking stairs 表示连续延伸缩小，区间化证据增加；
- Trending Trading Range 强调“局部区间—短突破—新区间”的公平区域迁移。

Broad Channel 与 Trending Trading Range 可以是同一行情的两个观察视图：前者强调方向 swing 和深回调，后者强调局部平衡区迁移，只形成一份结构证据。

回调接近先前 leg 的一半可作为几何参照，但 `50%` 不是独立支撑或固定反转阈值。回调持续扩大为 endless pullback、反向 channel 或双边都能获利的区域时，应更新活动结构，而不是继续沿用“浅回调”名称。

Rising Channel 在当前周期属于多头趋势；同时保留其完整生命周期中向下突破趋势线并通常区间化的 Bear Flag 视角。若它位于外层空头趋势，本身直接承担外层 Bear Flag 角色。短期恢复旧高与长期向下突破属于不同 horizon，不能放进同一交易方程；Falling Channel 完全镜像。

趋势线或通道线只是候选区域。轻微 overshoot / undershoot 不使结构自动失效；强越界、边界外收盘、follow-through 或旧线长期不再组织价格，才支持重画或重新分类。

### 平衡状态

Trading Range 表示市场围绕公平区域反复双向测试，双方都能获利而没有一侧持续控制。Range Condition 只保存会改变当前动作的两个维度：

- `Width = TIGHT`：barbwire 或压缩重叠多，通常缺少扣除成本后的目标空间；
- `Width = BROAD`：边缘可能生成路径，中部通常缺少优势；
- `Maturity = DEVELOPING`：前序方向和初始腿仍可能明显约束测试与目标；
- `Maturity = MATURE`：价格已经反复双向测试公平区域，前序方向影响减弱，任一方向突破获得跟随的可能性上升；
- 强区间腿可能只是 vacuum test 或边缘第二腿陷阱，不因运动强就取得趋势突破后的延续概率；
- 边界越过先记 breakout attempt，只有外部接受和控制形成后才更新为 Trend。

Width 与 Maturity 都是连续判断，`UNCLEAR` 是合法值；系统不使用固定根数或绝对点数强制分类。Breakout Mode 仍需双向突破可能性等当前事实，不能只由 `MATURE` 自动推出。

Limit Order Market 是从重叠、影线、反转尝试和双边获利等事件事实归纳出的行为条件，常见于区间、宽通道和弱趋势，不是新的 Context 状态。价格 touch / cross limit price 也不证明账户成交。

### Overlays：Breakout Mode、Climax 与 Transition

Breakout Mode 表示任一方向突破都有可能获得跟进；它常叠加在成熟 Trading Range、Triangle、ii、ioi、oo 或压缩上，不是 Trading Range 的同义词。由这些 Geometry Views 归纳出 Breakout Mode 不构成第二份证据。Breakout Mode 不预测方向，也不保证首次突破成功。

`CLIMACTIC_MOVE_CANDIDATE` 表示进行时的过快过远或异常强运动；`CONFIRMED_CLIMAX` 只在后续已经停止延续并进入区间或反向结构后成立。前者用于实时路径更新，后者用于已经发生的状态转换和复盘。Final Trend Bar、Final Flag、Give-up Bar 同样包含事后角色，实时只保存候选并观察 follow-through、剩余空间和反向接受。

回调加深、双边交易增加、趋势线突破、旧极值测试失败和顺势突破缺少跟随构成 transition evidence；单项线索通常不足以确认 opposite trend。

### 分类不清时的运行 fallback

- 方向状态与 Trading Range 分不清：按 Trading Range 管理；
- Breakout / Spike 与 Channel 分不清：按 Breakout / Spike 管理，只沿控制方向；
- Tight 与 Broad Channel 分不清：按 Tight Channel 管理；
- Broad Channel 与 Trading Range 分不清：先按 Trading Range 处理。

Fallback 只决定当前允许动作，不把未决事实写成永久标签。

## 七、结构视图，而不是交易分类

### H/L、Double Test 与 Wedge

H1 / H2 / H3 表示同一牛向恢复逻辑中的第一、第二、第三次向上尝试；L1 / L2 / L3 镜像表示熊向恢复。计数必须绑定周期、当前 pullback / test 和重置条件。

```text
第二次向上恢复尝试
├─ 次序视图：H2
├─ 若两次下探测试近似区域：Double Bottom
├─ 若外层多头趋势仍有效：Bull Flag 角色
└─ 若旧空头结构已受破坏：MTR 测试组件
```

Double Bottom 只要求两次测试近似低位；成为 H2 还要求同一逻辑中的第二次向上尝试。严格 second entry 还要求第一次 chart entry opportunity 已经触发。三者可以描述同一事件，却不是无条件同义词。

Wedge 描述三次可区分的推动或测试；H3/L3 是尝试计数视图。Wedge 可以是趋势回调中的 Flag、成熟通道末端的 reversal candidate，或 Trading Range 中没有优势的局部结构。编号增加不等于概率增加；H4/H6 等高阶计数首先提示检查结构是否已经变成区间、endless pullback 或新趋势。

宽泛的三推只建立 Wedge 功能视图。只有观察尺度、倾斜方向、三推、当前 Context / Price Map 位置和适用目标满足具体规则时，才能匹配倾斜 Wedge 的方向先验；推动间反应、重叠和压力继续更新其质量，接近水平的成熟结构仍按 Triangle / Range 条件处理。三推也不单独确认 Broad Channel：Broad Channel 仍要求深而反复的回调、重叠增加和双边逐渐能够获利。三推、H3/L3、Wedge 或 Broad Channel 等名称若来自同一运动不各自增加证据；其中可区分的回调深度、重叠和后续反应仍是新增事实。

Parabolic Wedge 是 Tight Channel 中至少三次 surge 构成的高潮式三推。它描述推进紧迫性，不要求每一推机械变陡；没有反向接受时仍可能继续原趋势，第一笔反向运动通常先按 minor correction 或 Range 路径处理。

新的强 breakout 获得接受、成熟区间切断旧运动、主要结构被替换或观察周期改变时，旧 H/L 与腿数重置。局部重计和全局累计都必须绑定明确尺度，不能在结果出现后选择更漂亮的计数。

### Flag

Flag 只说明 pullback、channel、局部 range 或其他暂停在外层趋势路径中的角色。它没有统一概率，不产生 Entry、Stop 或 Target：

- Double Bottom 可以是 Bull Flag，也可以是区间底部测试或 MTR 组件；
- Rising Channel 可以是当前多头趋势，并同时是外层或长期 Bear Flag 视角；
- 普通 pullback 可以拖长成 endless pullback、反向 channel 或 Trading Range。

Final Flag 只能在顺势恢复失败和后续结果出现后得到更多确认；实时仍同时保留普通 continuation flag 路径。

### Triangle、ii、ioi 与 oo

Triangle 是成熟 Trading Range 与 Breakout Mode 的结构视图。来源对“五次反转”和“一侧三推且总体至少五腿”存在不同计数口径；运行中必须声明采用的观察尺度，不能建立机械换算。

- `ii / iii`：连续 inside bars，表示压缩；
- `ioi`：inside–outside–inside；
- `oo`：连续 outside bars，表示双边扩张；
- Expanding Triangle：两侧极值逐步扩张且多次反转，没有建立持续控制。

统一处理都是：压缩或双边状态 → 实际突破 → follow-through → 守住或重新进入。形态名称不提供方向。

这些几何可以与其他过程角色组合：例如 ii / ioi 同时可能处于 H/L 恢复尝试、普通 Flag 或 Final Flag candidate 中；高周期少量 K 线也可在低周期展开为 Triangle / Range。只有新增周期事实、外层约束或后续反应才可能增加信息；把同一压缩重新命名为 Triangle、H2/L2 或 Flag 不增加概率。

### Reversal 与 MTR 过程

第一次逆势尝试默认是 Minor Reversal，常见目标是两腿修正或 Trading Range，不自动形成 opposite trend。

MTR 描述一条过程，而不是另一套交易方法：

```text
成熟趋势
→ 趋势线或主要结构被破坏
→ 原趋势测试旧极值
→ 测试失败或形成 HL / LH
→ 反方触发并尝试建立 swing
→ 强反向 breakout 与 follow-through 进一步确认控制转移
```

约五根强反向 K 线，或约十根普通 / 较弱反向 K 线，是课程用于比较反向压力强度与持续时间的启发式，不是达到根数就确认 MTR；一两根足够强的 surprise 也可能更快改变控制。

Wedge、Double Top/Bottom、Head and Shoulders、rounding top/bottom、Final Flag 或 Climax 可以描述其中组件，不能替代完整过程。Head and Shoulders 通常可拆回结构破坏、旧极值测试和反向路径；rounding top/bottom 常可拆回 Broad Channel、Endless Pullback 或 Trading Range。强反向 breakout 获得接受后，它同时是旧趋势失控和新方向 breakout continuation 的事实链，不需要在两种“策略”间选择。

旧趋势以新的强 breakout 和紧密趋势腿重新建立控制时，旧趋势线破坏、旧极值测试和 H/L 证据重置，不能永久借给后来的反转候选。

## 八、多周期与时间范围

每个 Context、当前问题、Opportunity、目标和概率都绑定周期与观察窗口。同一价格在高周期可能是一根 breakout bar，在交易周期是 Tight Channel，在更低周期又展开成 Broad Channel 或 Range。

内部模型至少分开：

```text
Context
- Trading Timeframe、Relevant Outer Constraint、Session / Remaining Horizon

Market Read
- Context、Price Map、Current Move、Active Test

Opportunity
- Direction、Role、Objective、Horizon、价格区域角色与结构失效

Trade Candidate
- 当前 Entry、Planned Stop、Target、Size 与管理
```

较小周期可以提前触发，但必须在承担风险前定义；成交后不能因盈亏情绪临时切换到更小噪声周期。小周期 Entry 若追求大周期目标，Stop、仓位和持有时间必须容纳大周期正常波动。

Session 只通过剩余时间、波动、流动性、目标可达性和是否允许跨 Session 进入路径。盘中只能描述实时 session state，最终 day type 不能回填当时判断。Opening、first swing、Opening Breakout Mode、first-18 heuristic 和内部固定 opening window 不是同一对象，使用时必须声明边界来源。

## 九、目标怎样生成

目标来自已经固定的结构、可见参照区域和当前正在解决的价格问题。它先是市场结果，不是交易者为了修复 reward/risk 而事后选择的退出价。

| 来源结构 | 候选目标事件 |
| --- | --- |
| Trend / Channel 内恢复 | 测试旧极值、通道边界或下一现实 magnet |
| Trading Range 边缘反应 | 返回内部公平区域、中部或另一侧 |
| Range / Pattern 突破并接受 | 测试按固定高度投射的 measured-move 区域 |
| 强 Breakout 与回调 | 尝试第二腿、旧极值或 Leg 1 = Leg 2 |
| Failed Breakout | 返回旧结构、内部目标、中部或另一侧 |
| 通道反向突破并接受 | 通道起点或更大 Trading Range |
| MTR 路径 | 反向两腿、旧公平区域或其他实际 swing magnet |

常见投射：

```text
Leg 1 = Leg 2：第一腿 A → B，第二腿起点 C，目标 = C + (B - A)
Range height：H = upper boundary - lower boundary
  向上目标 = upper boundary + H
  向下目标 = lower boundary - H
Double-bottom height = neckline - bottom area
Double-top height    = top area - neckline
```

所有端点必须来自当时可见的结构并冻结。Measured move 是目标候选，不提供入场许可；更近障碍、成本和剩余时间会改变现实 Reward。多个来源相对独立的投射落在相近区域，可以增强 target cluster 的 magnet 和到达后反应意义；同一结构的不同量法仍只属于一个来源族。

目标事件只定义市场结果：价格触及、进入区域、越过并获得接受，或在 horizon 内未发生。账户是否实际成交退出属于 Trade Outcome 与 Account Result，不能写入 Opportunity 的市场目标。

## 十、从 Market Read 到 Opportunity Set

结构、位置与当前价格问题明确后，分别扫描现实 Long / Short 路径，不用一个“偏多/偏空”标签代替双方论证。双向扫描完成前不进入 Trade Construction：

```text
Opportunity
- Direction + Role + Horizon
- Objective + Market Outcome Criterion
- Market Targets
- Why：去重后的价格事实链
- Already → Next
- Activation：什么过程事实使机会具备交易表达资格
- Invalidation：引用哪个 Region，什么市场事实真正否定机会
- Price Region Roles：Support / Resistance / Potential Entry Area / Obstacles /
  Magnets / Targets / Invalidation Reference
- Against：最强矛盾或对手 Opportunity
- Market Probability / Rule Match
- Expiry
```

每一侧都必须得到运行结论：构造现实 Opportunity、等待 Next，或以没有现实 objective、空间、时间为由排除。排除结果只保留原因，不展开伪 Opportunity。Context Control 提供 Permission 和先验，不替代另一方向的扫描。

事实不必平均分布。一条机会可以由一条强而连贯的突破链主导，也可以由独立位置、对手失败和新跟随补全。关键是它们分别支持机会的背景、Activation、接受、持续或目标，而不是理由数量。

`Role` 只用来防止混合 objective 和 horizon：continuation、correction、reversal、range return 或 breakout。例如强空头趋势中，`Up / Correction` 可先到 EMA 或 50%，随后 `Down / Continuation` 再测试旧低；两者可顺序成立。只有该顺序会改变当前选择或管理时才保存一句 `Likely Sequence`。`Up / Reversal` 则要求破坏空头控制并获得新方向接受，不能从短期修正目标直接推出。

明显缺少现实目标、时间或空间的方向只保留排除原因，不为形式对称制造伪机会。Market Read 尚未解决、Activation 尚未满足且不能由许可的条件 Trigger 完整执行，或当前没有值得承担的表达，都可以产生 Wait；Wait 只保存下一事件与 Expiry，不需要独立 Pending 对象。

常见双向问题可以生成：

| 当前问题 | 一条现实 Opportunity | 对手 Opportunity |
| --- | --- | --- |
| 趋势回调 | 原方向恢复并测试旧极值 | 回调扩大、结构破坏或进入 Range |
| 区间边缘 | 拒绝边缘并返回公平区域 | 外部获得接受并启动突破目标 |
| Breakout pullback | 突破点守住并恢复 | gap 关闭、旧区域重新接受 |
| 通道边界 | 内部反应并继续通道运动 | 外部突破获得接受并重分类 |
| 旧极值、EMA 或量度区域 | 穿越并获得接受 | 拒绝并启动返回路径 |

机会随来源事实改变，不随名称数量改变。新的 Context、价格区域、Current Move 或 Active Test 可以替代旧机会；历史结构只在仍能改变目标、正常回调或管理时留在 Context。不同 objective 或 horizon 分别表达，不用一个方向概率覆盖全部结果。

## 十一、证据生命周期

```text
出现
→ 在当前周期、窗口和状态内有效
→ 因缺少跟随、重叠增加或关键区域被收回而削弱
→ 因目标路径被新事实否定而失效
→ 因新主导 breakout、成熟 Range、控制切换或周期变化而重置
```

削弱不等于立即失效；重置不否认历史发生，只说明旧事实不再支持当前 Opportunity。Pattern 演化、事后名称和旧概率都不能越过重置继续提供交易许可。

Opportunity 的生命周期与证据强弱分开：

```text
ACTIVE
├─ 目标事件发生             → ACHIEVED
├─ 市场事实实质否定         → INVALIDATED
├─ horizon 结束             → EXPIRED
├─ 新 Context、价格问题或机会取代 → SUPERSEDED
└─ 目标与失效顺序无法确认   → SEQUENCE_UNKNOWN
```

增强、保持和削弱是 `ACTIVE` 内一次事件的更新结果；Activation 只表示该机会可以进入 Context Permission 与 Candidate 检查，不等于交易许可，也不改变生命周期。是否可交易由当前 Trigger、Entry、Stop、交易结果概率、Reward、成本、时间和账户条件决定。

## 十二、证据追溯

本页的运行关系由以下 Reference 范围支持并接受其冲突边界：

- [课程概念索引](../reference/course/concept_index.md)：课程思想骨架和概念族覆盖；
- [跨讲重复矩阵](../reference/course/repetition_matrix.md)：同源视图、镜像、递进和低增量重复；
- [边界与冲突](../reference/course/boundaries_and_conflicts.md)：概率分母、术语口径、数学和翻译限制；
- [正式来源台账](../reference/official_sources.md)：正式资料身份与来源锚点；
- [逐讲课程材料](../reference/course/README.md)：具体条件、页码和案例证据。

Reference 只提供核验依据；本页负责系统中的形成条件、更新语义和运行职责。
