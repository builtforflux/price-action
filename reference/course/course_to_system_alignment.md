# 01–52 课程与交易系统对齐

> 本页把 01–52 的课程证据映射到 `trading_system/` 的运行阶段。它用于覆盖核验和返回来源，不是另一套交易流程，也不直接许可交易。

## 一、权威边界

课程材料提供术语、价格关系、案例、条件概率和现实限制；[交易系统](../../trading_system/README.md)负责把这些证据融合为唯一运行语义。两者之间的关系是：

```text
正式来源与逐讲证据
→ 重复、递进、分母和冲突核验
→ 交易系统选择、归并、条件化
→ 市场结构、目标路径、计划、执行和复盘
```

本页不把课程中的每项说法自动升级为系统规则。产品规格、平台机制、因果叙事、固定参数和专用指标留在 Reference；数学冲突、分母不清和翻译不确定项进入隔离台账。

## 二、课程知识进入系统的判断

| 证据类型 | 系统处理 |
| --- | --- |
| 改变价格事实、活动结构、目标事件或结果路径 | 进入[市场结构与结果路径](../../trading_system/market_structure_and_paths.md) |
| 改变目标概率、Entry、Invalidation、Stop、Reward、仓位或方程 | 进入[交易决策与计划](../../trading_system/decision_and_plan.md) |
| 改变订单、实际保护、持仓、退出或复盘 | 进入[执行、持仓与复盘](../../trading_system/execution_and_review.md) |
| 条件、目标、周期、horizon 和判断时点完整的概率 | 进入[条件规则台账](../../trading_system/rules_and_conflicts.md) |
| 只提供来源、案例、产品或平台背景 | 留在 Reference |
| 数学、分母、翻译或来源口径不清 | 隔离，不进入运行 |

## 三、完整课程思想

01–52 反复应用的是同一个动态判断过程，而不是独立形态或策略集合：

```text
价格和账户事实
→ 分离、重叠、压力与接受
→ 活动结构、边界和位置
→ 结构生成候选目标事件
→ 建立到达目标与路径失效的结果路径
→ 匹配条件概率
→ 用 Entry / Invalidation / Stop 表达路径
→ 检查 Reward / Risk / Cost / Time
→ 执行、保护、管理和复盘
```

Pattern、Market Cycle、Context、H/L、Wedge、Double Test、Flag、MTR 等都在这条链中承担局部描述职责，不选择另一套运行逻辑。

## 四、01–52 覆盖映射

| 课程 | 主要证据增量 | 系统落点 |
| --- | --- | --- |
| 01 | 基础语言、Trend / Range、Scalp / Swing | 市场结构；决策与管理 |
| 02A–D | 图表、价格反应、Context、Momentum、Pain Trade | 外部信息边界；Pressure；行为路径 |
| 03A–E | 报价、pip、保证金、rollover、carry、损益换算 | Reference-only 产品事实；只通过成本和风险进入系统 |
| 04 | 周期、大周期位置、EMA 与观察设置 | 多周期、运行边界与参照区域 |
| 05 | 程序、高频和操纵叙事的证据边界 | 只保留可观察价格反应；机制叙事留 Reference |
| 06 | 纪律、耐心、客观和风险承受 | 执行纪律与仓位边界 |
| 07A–B | 市场/周期选择、选择性交易和情绪 | 运行边界、等待和行为纪律 |
| 08A–D | Trend/TR bar、反转、内外包、ii、Signal Bar | K 线事实、压缩视图和 Trigger |
| 09A–C | Pullback、H/L、高阶计数、重置、多周期 | 价格运动、同源视图和证据重置 |
| 10A–B | 实体、收盘、影线、突破和回调形成 Pressure | Pressure / Control / Always In |
| 11A–D | Session、open/close、完整、body、micro、MA、measuring/exhaustion gaps | Separation / Gap 与目标边界 |
| 12A–C | Trend / Trading Range、Breakout–Channel–Range | 活动结构连续谱与 fallback |
| 13A–C | Always In、Trader's Equation、Scalp / Swing | Control；条件概率；风险方程 |
| 14A–E | Trend、Spike–Channel、紧/宽通道、小回调 | 活动结构、Channel 角色和 Stop 空间 |
| 15A–G | Breakout attempt、follow-through、surprise、失败和第二腿 | 测试—接受链与结果路径 |
| 16A–F | 通道线、重画、边界测试、周期嵌套和区间化 | Channel 生命周期、多 horizon 路径 |
| 17A–B | Microchannel、小回调趋势、首次反转和 TTR | Tight Channel、minor path 与压缩 |
| 18A–F | Range、BLSHS、BOM、LOM、vacuum、成功突破和第二腿陷阱 | Range 目标、Breakout Mode、限价行为 |
| 19A–E | Support / Resistance、magnet、多周期位置和 entry test | 参照区域、目标事件与 confluence |
| 20A–B | Leg 1 = Leg 2、Range/Breakout height | 结构目标与投射端点 |
| 21A–D | Minor/Major reversal、压力、TBTL 和早晚风险时点 | Reversal 路径；条件概率与管理 |
| 22A–D | 趋势破坏、旧极值测试、HL/LH、再入和重置 | MTR 过程、Invalidation 与新路径 |
| 23A–B | Final Flag 候选、晚段和事后确认 | 候选/事后边界；Transition |
| 24A–E | Wedge、Parabolic Wedge、75/25 与突破后更新 | 三推视图和条件替代 |
| 25A–B | Double Test、Neckline、量度与失败链 | 第二次测试、目标和反路径 |
| 26A–B | Triangle / Expanding Triangle 的成熟度和尺度 | Range / Breakout Mode 视图 |
| 27A–B | Head and Shoulders 的价格行为还原 | MTR 组件，不建立独立分类 |
| 28 | 其他替代形态名称和区间本质 | 同源视图；低增量名称不新增系统对象 |
| 29A–E | Climax、Gap、Final Flag、量度、Wedge 和转折 | 实时/事后边界；目标和状态更新 |
| 30A–E | 方程、风险、仓位、心理和计划 | Trade Plan、风险类型和隔离数学问题 |
| 31A–D | Scalp / Swing、目标、概率与成本 | 管理选择和 Trader's Equation |
| 32A–C | Stop / Limit / Market 订单与成交现实 | Entry 表达和订单生命周期 |
| 33A–G | 结构 Stop、Mental Stop、提前退出和风险 | Invalidation、Planned / Active Stop |
| 34A–B | Initial / Actual / Account Risk 和统计问题 | 四种风险；Actual Risk 仅作事后样本 |
| 35A–C | Scale-in 数学、层数、间距、共同 Stop | 加权均价、最坏总风险和计划约束 |
| 36A–B | 成交后更新、部分退出和目标变化 | 冻结原计划、current state 和数量管理 |
| 37A–B | 前 36 讲的状态—方程—执行整合 | 总流程与跨阶段不变量 |
| 38A–D | 顶部反转的压力、结构、再入和管理案例 | MTR 路径实例；不新增分类 |
| 39A–D | 底部镜像、概率交换和 trailing | MTR 镜像；Stop 与管理 |
| 40A–E | 趋势末端、FOMO、Final Trend Bar、失望和 trapped | Transition、持仓更新和行为纪律 |
| 41A–D | 强突破、Buy/Sell The Close 和 Swing Stop | Breakout 路径的不同判断时点 |
| 42A–C | Minor/Major climax、Gap、microchannel 和区间第二腿 | 特定覆盖条件与结果路径 |
| 43A–D | Tight Bull Channel、首次反转和逆势加仓困难 | Channel 路径；数量风险；冲突数字隔离 |
| 44A–D | Tight Bear Channel 镜像 | 同一无方向系统关系，不重复规则 |
| 45A–E | Broad Bull Channel、周期嵌套、深回调和失败反转 | Broad Channel / TTR 双视图 |
| 46A–E | Broad Bear Channel 镜像 | 同一无方向系统关系，不重复规则 |
| 47A–D | Range、80% attempt、第二腿陷阱和限价交易 | Range 目标与突破条件更新 |
| 48A–K | First swing、Opening BOM、first-18、Opening Reversal 和尾盘 | Session 对象分层与时间风险 |
| 49A–E | 整日状态重判、H/L、高潮和第二腿 | 总流程动态更新案例 |
| 50A–E | Scalp、低周期、TICK 和管理 | Scalp 管理；TICK 只作辅助背景 |
| 51A–D | 错误、Mental Stop、周期一致和数量风险 | 系统违规、保护和行为纪律 |
| 52A–B | 三层保护、前提变化、再入和 trapped | 执行、持仓和复盘总结合同 |

## 五、跨讲重复怎样进入系统

| 重复簇 | 系统处理 |
| --- | --- |
| 趋势反转失败与区间突破失败的多种 80% | 保留不同目标和分母，禁止合成无条件 80% |
| H/L、Double Test、Wedge、Second Entry | 保存次序、空间和触发视图，只形成一份底层证据 |
| Tight/Broad Bull 与 Bear Channel | 运行知识使用无方向母版；Reference 保留镜像案例 |
| Pattern 名称最终回到 Pressure、Breakout 和 Failure | 不建立独立 Pattern 路由 |
| 结构 Stop、仓位、提前退出和重新入场 | 由一套 Trade Plan 与执行生命周期承载 |
| 状态转换在案例中反复出现 | 保留案例证据；系统只维护一个状态更新契约 |

完整重复判定见[跨讲重复矩阵](repetition_matrix.md)。

## 六、不进入运行系统的内容

- 外汇产品规格、账户货币和经纪商参数；
- 算法、机构、期权对冲或参与者身份的不可观察因果叙事；
- NYSE TICK 等专用辅助指标的固定阈值；
- 开盘/尾盘案例中的固定分钟、订单寿命和特定产品参数；
- Z-score 错配、80%/3R、十亿交易者百胜百负、43C 胜率冲突等数学问题；
- 用单笔事后 Actual Risk 证明事前交易方程；
- 没有样本定义的业绩承诺和能力上限修辞。

这些内容保留在逐讲材料和[边界与冲突](boundaries_and_conflicts.md)，不因课程出现就获得运行权限。

## 七、覆盖维护

新增课程证据时，先更新逐讲文件和必要的冲突/重复记录，再判断它是否改变现有系统字段。只有会改变结构、目标、路径、概率、计划、执行或复盘的内容才进入 `trading_system/`；否则保持 Reference-only。

