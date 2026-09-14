# 仓位管理：来源与吸收映射

> 当前方法以 [price-action](../../price-action/README.md) 为准。本文涉及旧系统的职责、采用状态及章节对应仅保留为历史记录，不代表当前方法；来源证据仍可查阅。

## 整理范围

- 全量检索 reference/course 的 191 个分讲，189 个命中仓位、加减仓、止盈止损或退出词项；04、08B 未命中。本项是检索覆盖。
- 正文与参数表选用 47 个分讲，重点读取相关条件、动作、算例、边界及已有视觉核验记录；归并为 20 个管理条目、23 项参数记录。
- 同时检查概率清单、来源台账、术语与课程边界；当前系统仅用于判断已有覆盖及吸收位置。
- 本轮依据本地 reference 整理；PDF 页码沿用来源台账版本，英文与原图核验状态沿用既有记录。

文档分工：[管理正文](README.md)保存条件与动作；[参数与核算](parameters.md)保存数值、损益及冲突；本页保存归并与吸收去向。

## 主要来源

01–36 为 `SRC-COURSE-01-36`，37–52 为 `SRC-COURSE-37-52`。同页码须连同课号定位；来源身份见[正式来源台账](../../reference/official_sources.md)。

| 来源 | 提供的增量 | 归并位置 |
| --- | --- | --- |
| [30C](../../reference/course/30C.md)、[33A](../../reference/course/33A.md)、[51D](../../reference/course/51D.md) | 结构止损反推数量、分层总风险、执行承受能力 | PM01–PM02、PM20；N01–N04、N07 |
| [33B](../../reference/course/33B.md)、[33C](../../reference/course/33C.md)、[33E](../../reference/course/33E.md)、[33F](../../reference/course/33F.md) | 多种合理保护、主要回调点、正常回调与追踪 | 保护参照表、PM12、PM18 |
| [35A](../../reference/course/35A.md)、[35B](../../reference/course/35B.md)、[35C](../../reference/course/35C.md) | 盈利追加、回调追加、分笔/组合退出、数量和层距 | PM02–PM04、PM08、PM11；N02–N06、N13–N15 |
| [45D](../../reference/course/45D.md)、[46D](../../reference/course/46D.md)、[47C](../../reference/course/47C.md)、[47D](../../reference/course/47D.md) | 双边重叠资格、边缘分层、越界幅度、宽止损与回摆退出 | PM05、PM11；N18、N23；时序表 |
| [43C](../../reference/course/43C.md)、[44C](../../reference/course/44C.md) | 窄通道逆势分层的收益风险与退出困难 | 受限案例；N16–N17、N19 |
| [31A](../../reference/course/31A.md)、[31D](../../reference/course/31D.md)、[33D](../../reference/course/33D.md)、[40B](../../reference/course/40B.md) | 持有风格、趋势降级与目标缩短 | PM07、PM10、PM12、PM15 |
| [34A](../../reference/course/34A.md)、[34B](../../reference/course/34B.md) | Initial / Actual Risk、过小风险倍数目标 | 核算口径、PM07；N08 |
| [36A](../../reference/course/36A.md)、[36B](../../reference/course/36B.md) | 当前权益回撤、目标兑现、分批比例、原前提失效 | PM06–PM09、PM14–PM15；N07–N09 |
| [13B](../../reference/course/13B.md)、[21D](../../reference/course/21D.md)、[22B](../../reference/course/22B.md) | 退出与反手不同门槛、早期反转的余仓管理 | PM07、PM09；N10 |
| [38A](../../reference/course/38A.md)、[38B](../../reference/course/38B.md)、[38D](../../reference/course/38D.md)、[39C](../../reference/course/39C.md)、[39D](../../reference/course/39D.md)、[41A](../../reference/course/41A.md)、[41D](../../reference/course/41D.md) | 多空案例中的减仓、保护、追踪、再入及日内退出 | PM03、PM07、PM09、PM12–PM13、PM18–PM19；N11 |
| [33G](../../reference/course/33G.md) | 近似保本、首轮测试容忍、恢复后的再测试、临近目标反转 | PM13–PM14、PM20；N12 |
| [32A](../../reference/course/32A.md)、[40D](../../reference/course/40D.md)、[51B](../../reference/course/51B.md)、[51C](../../reference/course/51C.md) | 止损实际执行、未成交退出、残留订单、新交易 | PM16–PM18；时序表 |
| [52A](../../reference/course/52A.md)、[52B](../../reference/course/52B.md) | 结构/动量/止损三类退出、加仓未触发、失望测试 | PM04、PM11、PM15、PM17–PM18、PM20；N05、N20 |
| [48I](../../reference/course/48I.md) | 剩余时段对分层与回摆目标的约束 | PM19 |
| [15G](../../reference/course/15G.md)、[50A](../../reference/course/50A.md)、[50D](../../reference/course/50D.md) | 最小目标、价差与成交余量、高手概率、已成交层 | N19、N21；时序表 |
| [03E](../../reference/course/03E.md)、[07B](../../reference/course/07B.md) | 报价币损益换算、保证金、训练仓位 | 核算口径；N22 |

## 重复与保留的区别

| 资料中的重复表现 | 归并方式 | 仍需保留的区别 |
| --- | --- | --- |
| 多头更低加买 / 空头更高加卖 | 原前提有效的回调追加、边缘分层分别归并 | 持仓方向与当前趋势方向；浮盈与浮亏 |
| 首仓波段、后层短线；全部波段 | 同一强突破追加条目内保留两个用途 | 各部分持有条件与减仓顺序 |
| 深回调加仓、趋势末端被套后加仓 | 共用分层与退出核算 | 前提有效程度、触发信号、剩余时间 |
| 正常回调中持有、新强突破后移止损 | PM12 依新事实顺序连接 | 新主要回调点须由后续强突破确认 |
| 盈利减仓、高潮止盈、目标兑现 | 按当前回吐风险、反向证据、预定目标分别整理 | 相同减仓动作可以有不同触发依据 |
| 入场价保本、两价中点保本、整组均价退出 | 共用逐笔损益核算 | 等量 / 不等量、已实现结果、成本 |
| 早退、宽止损持有、止损后重新入场 | 备选管理方案分别留档 | 已成交时序、旧余仓、新交易 |
| 多讲反复出现约 80% / 90% | 沿用原概率编号及条件 | 市场路径概率、交易结果概率、毛保本算术 |

## 现有方法与吸收位置

| 内容 | 当前覆盖 | 建议吸收方式 |
| --- | --- | --- |
| 止损反推数量、初始风险、当前风险、整笔损益 | Trade 3.6–3.7（旧系统） 已有 | 沿用现有定义；以 PM01、PM06 和算例作来源支撑 |
| 最大层数、预留预算、共同止损、增量判断 | Trade 第四节（旧系统） 已有 | 沿用共用规则；补 PM03–PM05 的不同市场资格 |
| 首仓波段、后层短线；动能失败减仓 | Trade 4.1（旧系统） 已有用途分工 | 以 PM08 补充重叠、平缓通道及跟随转弱的触发 |
| 目标兑现、当前风险减仓、高潮减仓 | Trade 3.5–3.6（旧系统） 已有原则 | 按 PM06–PM10 补条件与余仓去向 |
| 首次突破测试与恢复后再次测试 | Trade 3.4（旧系统） 已有止损约束 | 以 PM13 补判断时点；近似保本价仍核对结构与成本 |
| 前提失效、止损成交、退出未成交 | Trade 第五节（旧系统）、Account（旧系统） 已有 | 用 PM15–PM17 对照场景与订单事实，统一余仓数量 |
| 原交易退出后再入、反向新交易 | Trade（旧系统） 已有新方案核算 | 保留旧结果，补 PM18 的原背景恢复 / 反向新依据分支 |
| 日内分层的时间资格 | Trade 3.5（旧系统） 已有期限对象 | 用 PM19 补“回摆所需时间与剩余时段”的具体关系 |
| 目标倍数、分批比例、层距 | 现有方法按方案确定参数 | N03–N12 作为有来源的候选模板，明确分母及条件 |
| 算术冲突、未校准胜率、窄通道逆势案例 | [Reference 边界与冲突](../../reference/course/boundaries_and_conflicts.md) 保存来源问题 | N01–N02、N13–N20 留在审计与研究层 |

宽止损的案例可用于比较首笔参与方式；当前 Trade 对已有仓位采用单向收紧、需要更远止损则结束原交易后重评。来源的备选宽止损、实际风险目标和加仓案例进入方法时，分别遵守这一已选约束及整笔预算。

## 延伸主题与来源缺项

| 主题 | 已有证据 | 本次处理 |
| --- | --- | --- |
| 长期分批投入 | [35A p2740–2741](../../reference/course/35A.md) 按月固定数量投入 | N22 保留时间分批；日内条目按价格与信号组织 |
| 持续盈利后扩大常态规模 | [51D p1343](../../reference/course/51D.md)、[来源台账 SRC-RISK-113](../../reference/official_sources.md) | 保留训练、盈利记录与执行稳定性条件；晋级比例、样本量与回撤降级阈值待定义 |
| 期权替代与尾部保护 | [32A p2507](../../reference/course/32A.md)、[33F p2668](../../reference/course/33F.md) | 保存保护性 put、call/put 或价差替代；合约、期限、权利金和组合损益模型缺失，独立研究 |
| 保证金、杠杆与账户币换算 | [03E p250–264](../../reference/course/03E.md) | 保留计量区别与换算关系；历史产品参数留在来源 |
| 组合相关性、连败与账户总风险 | [30C 边界](../../reference/course/30C.md)、[课程冲突](../../reference/course/boundaries_and_conflicts.md) | 本轮来源未形成完整配置、降仓与恢复算法，列为后续账户研究问题 |
| 官方补充材料 | [来源台账](../../reference/official_sources.md) 的 `SRC-SCALE-IN-TRENDS`、`SRC-SCALE-IN-REVERSALS`、`SRC-POSITION-SIZE`、`SRC-RISK-113`、`SRC-STOP-ORDERS` | 采用台账已有文本支撑：初仓小、计划分层、总风险、当前价至止损及部分止盈；本轮未复查远端页面 |

后续吸收以管理动作的条件、数量、保护和余仓处理为单位；现有共用核算继续复用，数值模板在明确适用范围后另行选择。
