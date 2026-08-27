# 市场决策事件导航

> **状态：Trading System / Runtime Navigation**

本页回答一个盘中问题：`当前边界或价格变化是否值得重新展开判断，若值得，应重开哪几步？` 它是[总流程增量更新](overall_flow.md#四增量更新只沿变化传播)与 [Market Read](market_read_and_opportunities.md) 的事件索引，不是形态、Setup、信号或概率目录。

事件不建立新的持久对象。识别后只更新既有的 `Price Map → Current Move → Active Test → Context → Long / Short Opportunity`；只有机会、计划、风险或动作改变时才记录最小增量。订单、成交、保护和账户异常由[执行生命周期](execution_management_and_review.md)处理。

## 一、盘中用法

普通新 K 线仍只运行增量问题：

```text
Frame / Safety 是否发生边界变化？
区域、运动或测试出现新事实了吗？
多空路径、顺序或 Context 因此变了吗？
Candidate、计划、风险或动作因而需要改变吗？
```

全为否：`NO_CHANGE`。出现关键事件时，在本页找到最接近的路由或复合卡，只重开所列步骤。事件名称只是导航标签；同一价格链触发多个名称时，合并为一次更新。

一次事件更新的最小输出是：

```text
What changed：Frame 边界，或新区域、运动、测试、期限事实
Bull Pressure：增强 / 保持 / 减弱 / 未建立
Bear Pressure：增强 / 保持 / 减弱 / 未建立
Control：Bull / Bear / Balanced / Unclear
Context Change：INITIALIZED / UNCHANGED / UPDATED / REFRAMED
Current Context：Operating State / Direction / Conditions
Long / Short：各自的 Side Scan、Support / Activation 是否改变
Route：No Change / Update Opportunity / Rebuild Candidate / Submit Decision / Update Position
```

这是快速判断格式，不是逐项书面记录要求。

Bull 与 Bear Pressure 使用同一个能回答当前过程的最小窗口，默认是当前段、当前测试或上次 Reframe 以来；只有窗口发生切换或可能产生歧义时才另行说明。纯 Frame 事件没有产生新价格事实时，两侧 Pressure 与 Control 继承原结论。

## 二、边界与通用价格事件路由

### Frame / Session Boundary

新 Session、Opening、Trade Plan.Time Exit、已知事件窗口，或波动与流动性条件实质变化时，从 `Frame` 重开。先更新 Session、Remaining Time、目标可达性和相关外层约束；Opening Gap 同时进入 Price Map，开盘后的第一段运动再进入 Current Move / Active Test。只有这些变化继续改变 Context、Opportunity、Candidate 或 Position 时才向后传播。

Frame 事件不建立 Day Type、Opening Setup 或新的交易状态。盘中只能使用当时已知的 opening state；Opening、first swing、Opening Breakout Mode、内部 opening window 和最终 day type 的边界不能互换。

### 通用价格事件路由

所有价格事件都先更新 `Current Move`，再更新它与区域互动形成的 `Active Test`。Price Map、Context、Opportunity、Candidate 或 Position 只在上游结论改变时继续展开。下表的“必重开”是起点，不表示跳过共同传播顺序。

| 事件族 | 识别 | 必重开 | 必须解决的问题 |
| --- | --- | --- | --- |
| 参照形成 / 角色变化 | 新 swing high / low、突破点、运动起点、固定投射、major HL / LH 或保护锚点开始影响目标、空间、失效或动作 | Price Map；若改变当前问题则继续 Active Test | 新 Region 是否获得运行职责；它改变哪条路径、目标、保护或下一动作？ |
| 区域互动 | Approach、Touch、Overshoot、离开或重返相关 Region | Price Map → Current Move → Active Test | 哪个区域正在承担作用；接近与反应质量怎样；拒绝、接受或仍 Pending？ |
| 主动运动 | surprise、强 breakout、连续 trend bars 或明显分离 | Current Move → Active Test | 是一次尝试，还是已有 follow-through 与新区域接受？ |
| 后续反应 | follow-through、停顿、回调、反向 K 线或恢复 | Current Move → Active Test | 原方向保持连续性，还是仅减弱；反方是否真正建立压力？ |
| 尝试递进 | 同一逻辑的第二、第三次测试或恢复尝试 | Current Move → Active Test.Attempt | 延伸和压力在增强还是减弱；失败的是哪一方的哪项目标？ |
| 接受与失败 | 边界外保持、回踩守住、快速收回或旧区域重新接受 | Current Move → Active Test.Resolution | 哪个价格区被接受；原路径只是削弱还是已经失效？ |
| 压缩与释放 | ii、ioi、triangle、tight range 后离开平衡 | Price Map → Current Move → Active Test | 外层 Context 给哪侧先验；突破能否跟随并守住？ |
| 控制转换 | 正常回调、目标、双边获利能力或 Always In 边界改变 | Current Move → Active Test → Context | 原 Context 仍可沿用、增加 `TRANSITION` Condition，还是已经 Reframed；修正与反转是否仍分开？ |
| 目标与期限 | 到达 magnet / target cluster，空间耗尽、时间到期 | Current Move（价格到达时）→ Active Test → Opportunity / Position | 目标已完成、需要新目标，还是路径/计划到期？ |

无法归入复合卡的新价格场景，仍可由这些通用事件族完整路由；Frame、账户和执行变化分别使用本节边界路由或[执行生命周期](execution_management_and_review.md)，不需要把它们伪装成价格形态。

## 三、高价值复合事件卡

### 1. Session Open / Opening Gap / First Swing

```text
识别：新 Session 开始；opening gap 或开盘后的第一段方向运动开始形成
重开：Frame → Price Map(open / prior close / session levels) → Current Move → Active Test
双向：外部价格能否获得接受并延续；还是 gap 关闭、旧区域重新接受并形成 range / reversal path？
Next Observation：开盘运动的 follow-through、回踩守住；或 gap close 后旧区域接受、反向跟随
Event Expiry：开盘问题已被接受/失败解决，第一 swing 被新 Context 取代，或内部 opening window 到期
```

Opening Gap、first swing、Opening Breakout Mode 和 opening reversal 可以描述同一早期 Session 的不同事实，但不是同一对象，也不共享机械 Entry。当前 Context、位置、两侧压力、接受和剩余空间仍决定 Opportunity 与 Candidate。

### 2. 长期分离后的首次 EMA 测试

```text
识别：强趋势在当前周期约 20 根或足够长时间未触 EMA，首次回到 EMA 区域
重开：Price Map(EMA) → Current Move(回调质量) → Active Test → 双向 Opportunity
双向：顺势方能否在 EMA 附近恢复；反方只有修正压力，还是已经破坏旧 Control？
Next Observation：顺势 signal / breakout + follow-through；或穿越 EMA、反向跟随并获得接受
Event Expiry：首次测试完成、区域被反复穿越，或 Context 已重构
```

它首先是趋势背景下的区域测试。长期分离提高首次测试的意义，但不提供机械 EMA entry；顺势继续测试旧极值与反向演化为更深修正或反转必须分别表达。

### 3. Surprise / 强主动突破

```text
识别：相对背景异常大的趋势 K、连续强 K 或快速形成分离
重开：Current Move → Active Test → Context
双向：主动方能否获得跟随与新区域接受；对手是立即失败、形成反应，还是只暂时退让？
Next Observation：follow-through、回踩守住；或分离关闭并重新接受旧区域
Event Expiry：初始运动已被后续过程确认、否定或吸收到新 Context
```

### 4. 突破后的第一反应

```text
识别：初始突破后的下一段延伸、停顿或反向反应
重开：Current Move.Continuity / Separation / Opponent → Active Test.Phase / Resolution
双向：原方向是否新增独立跟随；反方是否关闭分离并建立自己的连续性？
Next Observation：接受、breakout pullback 守住；或 failed breakout 所需的旧区域重新接受
Event Expiry：突破被确认、失败，或演化为通道 / 区间
```

### 5. Breakout Pullback / 首次回踩突破区域

```text
识别：突破已发生，价格首次回到突破点、gap 或新区域边界
重开：Price Map → Current Move.Pullback → Active Test
双向：突破方能否守住并恢复；对手能否穿回旧区域且获得跟随？
Next Observation：顺势恢复 / H1-H2 trigger；或回踩失败与旧区域接受
Event Expiry：测试完成、边界反复穿越，或突破路径失效
```

### 6. 第二或第三次区域测试

```text
识别：同一 Region / objective 的独立再次尝试，中间存在可辨识反应
重开：Current Move(本次相对上次的质量) → Active Test.Attempt / Response → 双向 Opportunity
双向：本次延伸、K 线质量、连续性与对手反应相对上次怎样变化？
Next Observation：区域外接受；或拒绝、反向 breakout 与 follow-through
Event Expiry：测试逻辑被接受/失败解决，或新 Context 取代原测试
```

H2、Double Bottom、L2、Double Top、三推或 Wedge 可描述次序和几何。它们只在新增测试链确实形成时提供增量，名称本身不增加票数。

### 7. 三推 / Climax 候选后的对手反应

```text
识别：第三次推进、延伸衰减或潜在高潮，来到相关区域或目标
重开：Current Move → Active Test.Attempt → Context → 双向 Opportunity
双向：原方向 Pressure 是否仍强；对手是否已有强 K、连续性、分离和 follow-through？
Next Observation：原方向恢复并再创新极值；或反方 breakout、跟随并破坏旧结构
Event Expiry：第四次有效推进、原趋势恢复，或反方获得接受并重构 Context
```

三推在强原方向 Pressure、弱对手反应下通常只支持回调或暂停；它不能单独把 reversal attempt 升级为 reversal。

### 8. Trading Range 边缘测试

```text
识别：价格 Approach / Touch / Overshoot 成熟区间边缘
重开：Price Map → Current Move(接近与反应质量) → Active Test → Long / Short Opportunity
双向：边缘拒绝支持 range return，还是边界外出现突破、跟随与接受？
Next Observation：反向 signal / 跟随；或边界外保持、回踩守住
Event Expiry：回到内部目标、区间外接受，或测试时间失去意义
```

### 9. ii / ioi / Triangle / Local Balance 释放

```text
识别：局部重叠和波幅收缩后突破压缩边界
重开：Current Move → Active Test → Context
双向：外层趋势 continuation、区间 breakout mode 或失败突破，哪条路径获得后续事实？
Next Observation：突破 follow-through / hold；或快速收回并向另一侧测试
Event Expiry：某侧获得接受，或压缩继续扩展而需重画边界
```

### 10. 趋势结构破坏后的旧极值测试

```text
识别：反向 breakout 破坏通道 / 主要摆动结构，随后测试旧 extreme
重开：Price Map → Current Move → Active Test → Context → 双向 Opportunity
双向：原趋势能否恢复并重建 Control；反方能否形成第二段、HL/LH 与新方向接受？
Next Observation：旧极值突破并恢复原趋势；或测试失败、反向跟随并完成 MTR 路径
Event Expiry：旧趋势重建，或新方向结构获得接受
```

MTR、Head and Shoulders、Double Top / Bottom 是对这段过程的视图；运行结论来自结构破坏、旧极值测试和后续接受。

### 11. 目标簇 / Measured Move 到达

```text
识别：价格进入旧高低、区间投射、Leg 1 = Leg 2、通道边界等目标汇合区
重开：Price Map → Current Move(到达与反应质量) → Active Test → Opportunity / Position
双向：原路径继续穿越并接受，还是目标完成后出现足以激活反向路径的反应？
Next Observation：目标外 follow-through / hold；或拒绝、反向 trigger 与跟随
Event Expiry：目标事件按既定口径完成，或原 Outcome Horizon 到期
```

目标到达首先处理原 Opportunity 与持仓；反向交易仍需独立的 objective、Activation、Invalidation 和 Candidate。

## 四、视图与事件的合并

同一事件可有多个有用视图：

```text
H2 / Double Bottom       → 第二次向下测试
L2 / Double Top          → 第二次向上测试
H3 / L3 / Wedge          → 第三次尝试及推进质量
ii / ioi / Triangle      → 压缩与释放
Flag                     → 局部结构在外层 continuation / reversal 路径中的作用
MTR / Head and Shoulders → 结构破坏、旧极值测试与反向接受
```

合并标准是来源价格链与运行问题：若视图引用同一运动、区域、尝试和后续事实，只更新一份 Pressure、Active Test 与 Opportunity；若中间出现独立反应、第二次测试、follow-through 或另一价格区域，才形成新的增量事件。

## 五、维护边界

新增复合卡需同时满足：高频或高影响；容易漏掉；能明确指出应重开哪几步；能给出双向问题、Next Observation 与 Event Expiry。只提供新名称、固定 Entry 或与现有卡相同路由的场景，归入已有卡的 Views。

目录的完整性来自通用事件路由，复合卡只缩短常见判断。概率条件仍由[条件规则台账](conditional_rules_registry.md)负责，Entry / Stop / Target 与仓位仍由[交易决策与计划](decision_and_plan.md)负责。
