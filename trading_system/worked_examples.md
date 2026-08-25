# 完整流程演练

> **状态：Trading System / Worked Examples**

本页只演示[总流程](overall_flow.md)怎样在 5 分钟图上运行，不新增 Pattern、Setup、概率或记录义务。示例中的字段通常在数秒内心中确认；只有决定、计划、风险、执行事实或复盘边界改变时才保存最小信息。

## 一、宽多头通道第三推测试前高

### 初始读取

| 步骤 | 当时判断 |
| --- | --- |
| Safety / Event | 空仓、无工作订单、保护不适用、数据正常；主要前高进入观察范围，执行一次 Reframe |
| Frame | 5m；外层约束仍偏多；Session 尚有足够时间 |
| Environment | Regime = Trend；Direction = Bull；Phase = Channel；Variant = Broad；Modifier = Transition candidate |
| Location | Current Region = 前高区域；Active Area = 前高 / 区间上沿；Above Magnet = 下一量度区域，Target Candidate = 同一区域；Below First Obstacle = 旧突破点；前高外是上行 Acceptance Reference，重新进入前高下方是 Re-entry Reference |
| Price Action Now | 第三次上推后重叠增加，上方 separation 尚未建立，Pressure = Mixed，Bull control 正在减弱 |
| Active Test + Views | 自下而上测试前高能否获得接受；Sequence = 第三推，若满足同一 pullback / test 的第三次向上尝试才同时记 H3；Geometry = Wedge top candidate，Role = reversal candidate；同一上行价格链只形成一次路径判断 |
| Paths | Up：强突破并 follow-through；Down：跌回前高下方并获得接受；Pending：围绕前高继续重叠 |
| Market Gate | 多头路径缺少接受；空头路径也还只有候选反转；不进入 Risk Plan |
| Action | Wait：等待前高外接受，或跌回旧区域后的持续接受 |

这里不能把 Broad Channel、第三推、H3、Wedge 和 reversal candidate 算成五个空头理由。Broad Channel 是当前 Environment.Variant；其他名称只是同一次前高测试的次序、几何和过程视图。第三推不无条件等于 H3；只有计数尺度与恢复尝试的重置条件一致时，二者才是同源视图。

### 下一根强空头 K 线

新 K 线跌回前高下方并强收盘，只做三个 Delta：

1. Location / Price Action Now：价格重新进入前高下方，新增 rejection，Bull separation 失败，Selling Pressure 增强。
2. Environment / Active Test：Environment 尚未必改变，但前高上方测试从 `TESTING` 转为上行接受失败候选；若旧区域随后保持接受，Down path 增强。
3. Paths / Gates / Action：先重新判断空头路径是否通过 Market Gate；通过后才构造 Risk Plan 并检查 Execution Gate，全部成立才 Execute，否则继续 Wait。

若先前确有突破买入和后续失望，trapped buyers / 预期退出压力可以解释为什么下跌可能加速；它是同一“突破失败—重新进入”价格链的行为推断，不是额外一票。真正新增的证据是后续 bear follow-through 或旧区域持续获得接受。

若随后执行空头计划，盘中只保存最小 Decision Record、实际 fill / protection 事实和发生变化的风险 Delta。每根未改变路径或动作的普通 K 线不记录；对手重新在前高上方获得接受时，按原失效条件退出，而不是因为已经做空就继续寻找空头名称。

## 二、成熟区间下沿的 H2 / Double Bottom Scalp

| 步骤 | 当时判断 |
| --- | --- |
| Safety / Event | 空仓、账户状态一致；价格再次进入区间下沿，Observation Event |
| Frame | 5m；外层没有足以推翻本区间管理方式的约束；剩余时间允许一次 scalp |
| Environment | Regime = Trading Range；Phase = Mature Range；Direction = Neutral |
| Location | Current Region = 成熟区间；Active Area = 下沿；Above Magnet = 区间中部，Target Candidate = 同一区域；Below Acceptance Reference = 下沿外区域；到中部有足够净空间 |
| Price Action Now | 第二次下探力度减弱，出现下沿 rejection；重叠仍多，Control = Balanced |
| Active Test + Views | 自上而下测试区间下沿能否守住；Sequence = 第二次向上恢复尝试 / H2，Geometry = Double Bottom；若外层多头约束仍有效，可引用 Bull Flag 角色；同属一次下沿二次测试 |
| Paths | Up：返回区间内部或中部；Down：下沿突破并在外部获得接受；Pending：继续贴着下沿重叠 |
| Market Gate | 下沿位置合理，到中部的净空间足够，bull Entry 条件出现后通过 |
| Risk Plan | Entry 可观察；Invalidation 在下沿外接受；Stop 位于实际失效外；Target = 中部；扣除成本后方程成立 |
| Execution Gate | Size 合规、成交后保护可覆盖实际数量、订单条件可靠 |
| Action | 三个门全部通过才 Execute scalp；否则 Wait / No Trade |

成交后，普通小回调若仍属于计划允许的区间波动，只是 `保持`，不产生记录。新的 bear breakout attempt 先更新 Price Action Now；只有下沿外获得接受、计划失效或实际保护改变时才触发退出和记录。到达事前固定的中部目标后核对实际退出、仓位归零和剩余订单，再于盘后记录 Market result、Trade outcome、Account result 与 Process result。

这个例子保留了 H2、Double Bottom 和 Bull Flag 的不同含义，却只运行一条下沿测试路径。名称没有丢失，也没有建立三个 Setup。

## 三、区间中部的 ii / ioi 压缩

| 步骤 | 当时判断 |
| --- | --- |
| Safety / Event | 空仓、无异常；普通 Observation Event |
| Frame | 5m；临近日内低流动时段，剩余 horizon 受限 |
| Environment | Regime = Trading Range；Modifier = Breakout Mode |
| Location | Current Region = 区间中部；Above First Obstacle = 上沿；Below First Obstacle = 下沿；两侧首个障碍前的净空间均不足 |
| Price Action Now | 连续重叠、Pressure = Mixed、Control = Balanced；尚无方向 separation |
| Active Test + Views | 测试压缩边界哪一侧能获得接受；Geometry = ii / ioi；若同一压缩也可称局部 Triangle，仍只形成一次路径判断 |
| Paths | Up：上破并获得 follow-through；Down：下破并获得 follow-through；Pending：继续压缩或首次突破失败 |
| Market Gate | 两侧路径都存在，但区间中部位置和首个障碍前空间不足；不进入 Risk Plan |
| Action | No Trade：等待新的位置或外部接受事件 |

`ii`、`ioi`、Triangle 和 Breakout Mode 不是四份方向证据。前三者描述压缩几何，Breakout Mode 是由双向突破可能性归纳出的 Environment.Modifier；它们都不预测突破方向。

若随后首次上破但立即跌回压缩区，只更新失败链，不因出现“trapped breakout buyers”再加一票。若之后下破且 follow-through 建立外部接受，则旧 Test 关闭，Market Read 重新定位到新的 Environment / Location / Active Test；此时才以新价格和剩余时间重新经过 Market Gate、Risk Plan 与 Execution Gate，不能沿用压缩前的隐藏计划。

## 四、三个例子的共同闭环

无论最终是 Execute、Wait 还是 No Trade，运行闭环都相同：

```text
Safety / Event
→ Frame → Environment → Location → Price Action Now
→ Active Test + Views → Paths
→ Market Gate → Risk Plan → Execution Gate → Action
→ 允许的执行动作
→ 只记录关键决定、风险和账户事实
→ 路径与交易分别闭环
→ 盘后复盘；普通未变化 K 线不补写叙事
```

示例的目的不是让交易者盘中填写表格，而是验证每一步都有明确输入、输出和下一条件：看不清可以保留 `Unclear`，没有空间可以直接 No Trade，缺少接受可以 Wait，账户状态不一致则在 Safety Gate 中断市场评价。
