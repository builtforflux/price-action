# Reference 与 Trading System 完整差异清单

当前版本尚未吸收 Reference 的全部思想。全范围核对形成 166 个主题条目，其中包含未具体表达、部分吸收、方法/定义取舍、范围未纳入和已隔离来源；不是 166 个都应补入的缺陷。

范围为本地 191 分讲全文及各自英文逐页核验记录、Reference 其余已入库材料、7 个系统文件及明确委托的 Practice。逐讲共 808 个思想组，全部完成对照；同义和多空镜像归并，条件与例外留在来源分项。外部网页/书籍仅审计本地台账已记录命题，未声称穷尽其未入库全文。

系统在审计期间更新，最终判定按 [final_snapshot.json](final_snapshot.json)；起始内容保留在 [baseline.json](baseline.json)。当前系统和 Practice 已全文反查，[反查说明](other_materials.md)列出容易误报的已覆盖内容。早期逐讲表是来源证据与路由，最终分类以下文为准。

## 分类统计

| 分类 | 主题数 | 含义 |
| --- | ---: | --- |
| 定义/口径差异 | 23 | 同名概念的边界、评价对象或最低要求不同；有些是明确消歧。 |
| 方法取舍 | 15 | 系统有自己的参与、风险、风格或观察规则，与来源默认不同。 |
| 已覆盖（消歧） | 1 | 功能已覆盖，仅保留术语拆分供追溯，不计未吸收。 |
| 部分吸收 | 76 | 已有共同原则，但具体关系、条件、例外或管理模板未完整表达。 |
| 研究/隔离 | 4 | 来源数字、解释、错误或证据处理不进入当前生产规则；隔离原则本身已吸收。 |
| 未具体吸收 | 37 | 未在运行规则中找到该具体思想或启发式；不表示已验证值得采用。 |
| 范围未纳入 | 9 | 其他产品、策略或专用指标未纳入；不推定是核心运行缺陷。 |
| 仅别名或资料 | 1 | 名称未收录，未发现独立运行思想差异。 |

统计按主题归类，一个主题可以包含多条相关条件；166 项中含 164 个差异主题及 2 个已覆盖/纯别名追溯项。主题可能交叉（如 D007 收集其他条目的数值部分），不可相加成独立原子思想总数；分类不是严重程度或交易效果评价。D006/D007/D027 分别展开全部已核来源思想组，不以大标题掩盖其子项。其余条目的所有来源定位也逐一保留。

## 主要结论

- 主干已经覆盖：背景优先、市场连续变化、多尺度、强弱比较、第二腿及陷阱、主要结构、通用测量、结构止损、小仓位、成本与全层风险、早退重入、真实成交核对和分轨复盘。
- 较集中的未吸收增量：具体 K 线/形态条件、缺口和通道的定义边界、特定目标/止损/补仓配方、开盘/日中/尾盘模型、人工负荷和即时情绪条件，以及 NYSE TICK。
- 明确取舍包括固定目标/失效/期限、参与质量优先、净回报筛选、数值概率校准要求等。宽止损候选与持仓后放宽止损不同：课程多张图给不同方案，不能据此证明同仓移动；当前不放宽原则不能一概列为违背课程。
- 已隔离的百分比、历史参数、数学冲突与参与者叙事是完整差异的一部分，但不应直接迁入系统。

## 全部主题索引

| 编号 | 分类 | 差异主题 |
| --- | --- | --- |
| [D001](#d001) | 定义/口径差异 | outside bar 相等边界口径 |
| [D002](#d002) | 方法取舍 | 固定目标/失效/期限与趋势存续式持有 |
| [D003](#d003) | 已覆盖（消歧） | Chart Entry Bar 与实际成交 entry bar |
| [D004](#d004) | 部分吸收 | 量价背离的条件及两种后续 |
| [D005](#d005) | 部分吸收 | 经纪商破产、信誉与结算不交付风险 |
| [D006](#d006) | 研究/隔离 | 参与者动机、市场机制与理论解释 |
| [D007](#d007) | 研究/隔离 | 经验数字、历史参数、无样本断言和源内数学冲突 |
| [D008](#d008) | 部分吸收 | trapped in 与 trapped out 的角色和行为链 |
| [D009](#d009) | 部分吸收 | 流动性、时段重叠/清淡与参与选择 |
| [D010](#d010) | 部分吸收 | 外汇币种、pip/tick、名义额和点值换算 |
| [D011](#d011) | 未具体吸收 | 基准定价窗口的事件风险 |
| [D012](#d012) | 部分吸收 | Bid/Ask 点差的成本口径 |
| [D013](#d013) | 部分吸收 | Bid/Ask 构图、订单触发与成交侧对应 |
| [D014](#d014) | 部分吸收 | 日切、换汇、利息收付与多日计息 |
| [D015](#d015) | 范围未纳入 | Carry 长期利差策略 |
| [D016](#d016) | 部分吸收 | Session 模板与合约序列的数据口径 |
| [D017](#d017) | 未具体吸收 | 跨周期 EMA 近似、真实值与临时值 |
| [D018](#d018) | 范围未纳入 | 套利与跨市场配对策略 |
| [D019](#d019) | 部分吸收 | 专注和情绪干扰下的个人运行条件 |
| [D020](#d020) | 方法取舍 | 强突破阶段只顺势的参与限制 |
| [D021](#d021) | 方法取舍 | 参与质量优先与管理优先的教学重心 |
| [D022](#d022) | 方法取舍 | 多数人优先 swing 与潜在至少 2R 的教学默认 |
| [D023](#d023) | 部分吸收 | 周期、市场和复杂度须匹配人工负荷 |
| [D024](#d024) | 未具体吸收 | 本人感受作为观察 radar |
| [D025](#d025) | 范围未纳入 | 期权替代持股的承担方式 |
| [D026](#d026) | 方法取舍 | 强趋势中必须/尽快加入与当前可放弃的门槛 |
| [D027](#d027) | 部分吸收 | 信号质量相对开收、影线、前序与顺逆背景 |
| [D028](#d028) | 部分吸收 | 影线与低周期失败突破的解释桥梁 |
| [D029](#d029) | 部分吸收 | buy/sell reversal 与 bull/bear body、中点条件 |
| [D030](#d030) | 部分吸收 | 两根反转的非连续多棒用法与聚合边界 |
| [D031](#d031) | 部分吸收 | Outside bar 按背景选择限价反做或顺向突破 |
| [D032](#d032) | 部分吸收 | 小 TTR/ii/ioi 末棒方向、EMA位置及跟随质量 |
| [D033](#d033) | 定义/口径差异 | BOM 的宽泛小 TTR 与当前结构用法 |
| [D034](#d034) | 部分吸收 | 复杂分批及专家方法的个人能力准入 |
| [D035](#d035) | 部分吸收 | Actual/Implied Pullback 的相邻极值最低判据 |
| [D036](#d036) | 定义/口径差异 | 严格 H/L 触发计数与来源结构/段数映射 |
| [D037](#d037) | 未具体吸收 | 连续反转尝试增加相对概率的启发式 |
| [D038](#d038) | 未具体吸收 | 逆势持仓在原趋势 H2/L2 触发退出 |
| [D039](#d039) | 部分吸收 | Measuring gap 中点相对运动起点的对称投射 |
| [D040](#d040) | 定义/口径差异 | 岛形反转的几何变体和非独立预测力 |
| [D041](#d041) | 部分吸收 | Gap Open Bar 的趋势组合及市场适用权重 |
| [D042](#d042) | 部分吸收 | Stairs 的缺口重叠定义及逆势可获利诊断 |
| [D043](#d043) | 部分吸收 | 短区间继承方向、长区间逐渐中性的时间关系 |
| [D044](#d044) | 定义/口径差异 | 广义回调可始于最终极值之前及破坏趋势后的相对命名 |
| [D045](#d045) | 方法取舍 | 弱通道至少部分 scalp 与状态限定的管理默认 |
| [D046](#d046) | 部分吸收 | 能否可靠重入决定穿越回调持有或止盈重入 |
| [D047](#d047) | 部分吸收 | Always In 不清时回看最近未被反转的主导突破 |
| [D048](#d048) | 部分吸收 | 从通道外侧两点反向平移构造趋势线的取点约束 |
| [D049](#d049) | 部分吸收 | TFO 的开局极值含义、连续市场命名与后续分支 |
| [D050](#d050) | 部分吸收 | Trending TR 的新区间序列、重叠和回上一区间预期 |
| [D051](#d051) | 部分吸收 | 宽通道前段中间三分之一入场及加仓后的退出关系 |
| [D052](#d052) | 部分吸收 | 小回调趋势时段末较大回调、通常恢复及少见反转 |
| [D053](#d053) | 定义/口径差异 | 无需说清突破对象的微观教学用法与系统明确锚点要求 |
| [D054](#d054) | 部分吸收 | 强区间突破确认后停止逆向交易多棒的等待要求 |
| [D055](#d055) | 部分吸收 | Surprise 的事前低概率与确认后重新定价关系 |
| [D056](#d056) | 未具体吸收 | 形成中突破棒的停留位置与单次/重复回撤轨迹 |
| [D057](#d057) | 部分吸收 | 极端相对成交量强化跟随与测量预期 |
| [D058](#d058) | 部分吸收 | 首次回调时点、入场保本价测试与突破强弱 |
| [D059](#d059) | 定义/口径差异 | Micro gap 可接触不重叠与正宽度 gap 的边界 |
| [D060](#d060) | 部分吸收 | 末段衰竭高潮后通常先双顶/微双顶再反转 |
| [D061](#d061) | 部分吸收 | 固定 scalp 目标陷阱、提前一跳退出及弱 setup 反做分批方案 |
| [D062](#d062) | 部分吸收 | 趋势线三点的时间对称、独立性与超时失去相关性 |
| [D063](#d063) | 部分吸收 | Nested wedge 的大第三段内小楔形与衰减证据 |
| [D064](#d064) | 定义/口径差异 | 通道对侧最低目标需越线一 tick/pip 的设定 |
| [D065](#d065) | 部分吸收 | Micro Channel 相邻极值、起始基点与结束棒的严格定义 |
| [D066](#d066) | 未具体吸收 | 紧通道与 TTR 相对平均棒、最小 scalp 的两种空间门槛 |
| [D067](#d067) | 未具体吸收 | Micro trend line 有用而对侧微通道线可省略 |
| [D068](#d068) | 部分吸收 | 晚期高潮微通道首次反破后暂停原方向并观察 |
| [D069](#d069) | 未具体吸收 | 长紧通道高潮后至少二十棒两段修正的特定预期 |
| [D070](#d070) | 部分吸收 | LOM 的限价可行而突破单无空间及普通人避开的默认 |
| [D071](#d071) | 未具体吸收 | 紧区间大部分位于 EMA 一侧的轻微突破方向偏向 |
| [D072](#d072) | 部分吸收 | 早盘区间日的组合线索、各自观察窗口及延续时长 |
| [D073](#d073) | 未具体吸收 | 区间日末三分之一回测中部及两种收盘分支 |
| [D074](#d074) | 部分吸收 | 支撑阻力候选清单中的信号/入场棒、收盘极值、scalp目标及Daily pivots |
| [D075](#d075) | 部分吸收 | 月末年末对高周期开收及上期极值的特别关注 |
| [D076](#d076) | 部分吸收 | 收盘追随失望后分批回原价退出及最高最低收盘的角色切换 |
| [D077](#d077) | 定义/口径差异 | 越过晚期高潮棒边界即趋势结束与系统主要结构接受判据 |
| [D078](#d078) | 未具体吸收 | 深回调后等距最低目标及弱通道第二段结束倾向 |
| [D079](#d079) | 部分吸收 | 突破起点优先与区间起止分隔趋势两段的具体选点 |
| [D080](#d080) | 未具体吸收 | 以区间中点为对称中心的测量及较低权重 |
| [D081](#d081) | 定义/口径差异 | 反转/MTR 的广义状态命名及先按次要、反向破线持续十棒的默认 |
| [D082](#d082) | 仅别名或资料 | 杯柄、圆弧顶底等别名与已有反转/旗形过程的映射 |
| [D083](#d083) | 未具体吸收 | 主要反转压力所需极大棒、较小棒与普通棒的经验尺度 |
| [D084](#d084) | 定义/口径差异 | TBTL 作为最低目标与系统非最低等待的条件尺度 |
| [D085](#d085) | 未具体吸收 | 反转第一目标至少减半及TBTL/2R后最终获利的管理模板 |
| [D086](#d086) | 定义/口径差异 | 所有顶底可视为DT/DB的广义测试分类与系统同区测试判据 |
| [D087](#d087) | 未具体吸收 | 底部MTR向旧低方向至少三分之一回撤的要求 |
| [D088](#d088) | 部分吸收 | 按首次反向段强弱选择HH/LL提前反转或等待LH/HL |
| [D089](#d089) | 部分吸收 | 趋势中反侧MAG的最后一段预警与系统长期未触均线的限定 |
| [D090](#d090) | 部分吸收 | 头肩的HH到LH、LL到HL及肩头内部嵌套结构映射 |
| [D091](#d091) | 部分吸收 | MTR结构失败后须重新破线和测试的重置条件 |
| [D092](#d092) | 定义/口径差异 | 最终旗形不先顺原趋势突破的广义用法 |
| [D093](#d093) | 部分吸收 | 楔形三推动各有反转、同向倾斜通道与收敛可选的最低定义 |
| [D094](#d094) | 定义/口径差异 | 当前图无回调时推断低周期三推与可见事实要求 |
| [D095](#d095) | 部分吸收 | 抛物线楔形的连续高潮三推、加速不重叠与普通衰减楔形区别 |
| [D096](#d096) | 部分吸收 | 楔形反转先形态对端、再局部测量的目标层级 |
| [D097](#d097) | 部分吸收 | 楔形意外突破后预留反向测量目标外宽止损并分批反做 |
| [D098](#d098) | 定义/口径差异 | Micro DT/DB 的二至四或五棒尺度与外部波段背景确认作用 |
| [D099](#d099) | 部分吸收 | 三角形至少单侧三推五交替段、各边斜率与微型变体的定义 |
| [D100](#d100) | 未具体吸收 | 从横向三角形到倾斜楔形的方向先验连续变化 |
| [D101](#d101) | 未具体吸收 | 头肩颈线两水平与两点斜线三种画法及逐层测试 |
| [D102](#d102) | 定义/口径差异 | 每根趋势棒皆有高潮性质与停止后才命名高潮的宽窄定义 |
| [D103](#d103) | 部分吸收 | 单次高潮偏真空、连续高潮偏衰竭及真空全程/末段两种范围 |
| [D104](#d104) | 未具体吸收 | 普通高潮后先三至十棒区间及恢复/反转各半的默认 |
| [D105](#d105) | 定义/口径差异 | 高潮收盘到前棒极值及更早突破点的Gap距离定义 |
| [D106](#d106) | 未具体吸收 | 买入高潮后LH至少收复前下跌三分之一与底部源内方向疑点 |
| [D107](#d107) | 未具体吸收 | 高潮后最低修正棒数约原趋势一半的比例时间预期 |
| [D108](#d108) | 部分吸收 | 最后趋势段回撤深度与半程/三分之一内的方向概率和RR交换 |
| [D109](#d109) | 方法取舍 | 每笔凭经验估计数值概率与系统仅经校准才用于决策 |
| [D110](#d110) | 范围未纳入 | 十棒高低突破机械反向策略（大赢家分布意识已覆盖） |
| [D111](#d111) | 部分吸收 | Always In 以当前价上下等距离先到概率定义 |
| [D112](#d112) | 方法取舍 | 正期望但回报低于风险的交易与净回报硬筛选 |
| [D113](#d113) | 定义/口径差异 | Scalp 小于二倍风险与 Swing 至少二倍的教学定义 |
| [D114](#d114) | 部分吸收 | 连续突破按最新收盘至原共同止损距离延伸目标 |
| [D115](#d115) | 部分吸收 | 突破入场价只容忍一次回测、二次偏区间的状态启发式 |
| [D116](#d116) | 未具体吸收 | 最小scalp目标取近期平均棒高与日均波幅比例较大值及品种例外 |
| [D117](#d117) | 方法取舍 | 新手优先Stop入场、顺强趋势例外及暂避Stop-limit/marketable-limit的教学默认 |
| [D118](#d118) | 部分吸收 | 本应成交而未成交时联系经纪商及责任合同的处理范围 |
| [D119](#d119) | 部分吸收 | 五分钟形成中突破切一分钟连续棒提前入场及局部保护配方 |
| [D120](#d120) | 方法取舍 | 固定金额或信号外固定距离止损与优先结构保护的选择 |
| [D121](#d121) | 未具体吸收 | 宽止损按最小scalp倍数、平均棒高及日均波幅比例定距 |
| [D122](#d122) | 部分吸收 | 信号棒、区间或测量缺口投射外保护以容忍明显止损位假突破 |
| [D123](#d123) | 未具体吸收 | 强趋势追入以指定涨段半程外保护并止损后重入 |
| [D124](#d124) | 部分吸收 | 完美突破测试距突破点或保本位一二跳的定义与失守转换 |
| [D125](#d125) | 未具体吸收 | Scalp完成目标八九成后反转时近似保本的管理条件 |
| [D126](#d126) | 定义/口径差异 | Actual Risk/Perfect Stop事后存活距离与系统初始风险不改、仅作未来目标参考 |
| [D127](#d127) | 研究/隔离 | 亏损后排除异常值及假定极端盈亏抵消与连续全样本评价 |
| [D128](#d128) | 未具体吸收 | 加仓间距至少scalp尺度及原止损距离三分之一、首层预留比例 |
| [D129](#d129) | 部分吸收 | 盈利加仓动能转弱后快速降回常态数量及核心/后层分工 |
| [D130](#d130) | 范围未纳入 | 按月固定数量长期分时买入与短线战术加仓 |
| [D131](#d131) | 未具体吸收 | 不会加仓者等待专家追加位置作首次入场 |
| [D132](#d132) | 方法取舍 | 管理必须忽略入场价的绝对主张与当前全仓核算 |
| [D133](#d133) | 部分吸收 | 尾盘反转必须迅速推进及前棒反向四tick退出条件 |
| [D134](#d134) | 方法取舍 | 平仓后多数人先空仓一至三棒再评估反手 |
| [D135](#d135) | 研究/隔离 | Noise作为相对目标尺度的反转及不存在随机噪音的强断言 |
| [D136](#d136) | 部分吸收 | BTC/STC首次动能减弱后缩目标、积极管理及转Limit的阶段配方 |
| [D137](#d137) | 定义/口径差异 | Final Trend Bar事后定义与其后Give-up反转棒的区分 |
| [D138](#d138) | 未具体吸收 | 末端收盘两次方向测试失败后转试另一方向的预期 |
| [D139](#d139) | 方法取舍 | 收盘价为最重要单一价格及折线图的教学优先级 |
| [D140](#d140) | 定义/口径差异 | 第一次任何回调即结束突破阶段与系统首次有意义回调的门槛 |
| [D141](#d141) | 部分吸收 | 强反向旗形信号未触发即被顺向突破的陷阱确认序列 |
| [D142](#d142) | 未具体吸收 | 剩余趋势仓至少两个重要阻力或支撑理由重合再退出的默认 |
| [D143](#d143) | 未具体吸收 | 宽通道五棒以上段、三倍最小scalp、二至三均棒及三上三下/百棒确认的尺度簇 |
| [D144](#d144) | 方法取舍 | 屏幕约百棒与五分钟仅当日或前日形态、跨三日改高周期的观察范围默认 |
| [D145](#d145) | 部分吸收 | 此前失败突破幅度用于入场加仓止盈及旧极值外两倍最大突破的灾难止损 |
| [D146](#d146) | 部分吸收 | 宽通道开始形成LL/LH即停止原趋势交易的简化终止门槛 |
| [D147](#d147) | 未具体吸收 | 成熟区间至少两上两下且双向各10–20棒Always In swing的典型结构 |
| [D148](#d148) | 未具体吸收 | 区间突破只差一根跟进成为Always In时反向交易当前收盘 |
| [D149](#d149) | 方法取舍 | 新手区间止损后最多第二次反转重入、第三次不再进的默认 |
| [D150](#d150) | 部分吸收 | 开盘与尾盘偏突破Swing、中段偏通道区间的日内三阶段框架 |
| [D151](#d151) | 未具体吸收 | 初始摆动占平均日振幅25–50%或50–100%用于反转后趋势与区间预期 |
| [D152](#d152) | 部分吸收 | 日线方向与早晚影线由日内反转形成的对应及早期逆向测试偏置 |
| [D153](#d153) | 未具体吸收 | 昨日高潮后可先延续1–2小时再两小时横盘反向的次日路径 |
| [D154](#d154) | 部分吸收 | 开盘BOM首根两侧测试、初始不超过一棒及5–10棒/30–50%日振幅成熟度 |
| [D155](#d155) | 未具体吸收 | 前18棒范围突破独立于BOM，15–25棒关注窗及反侧日极值保持预期 |
| [D156](#d156) | 未具体吸收 | 窄昨日范围更易外包日、反转日不远过开盘另一端并收近开盘的预期 |
| [D157](#d157) | 部分吸收 | 跳空相对昨收/收盘区间/昨日极值及近端改为当日极值的动态边界 |
| [D158](#d158) | 部分吸收 | 最后一小时新反转通道弱于较早通道、末30分钟横盘延续及避免逆向分层的默认 |
| [D159](#d159) | 范围未纳入 | NYSE TICK逐股最新成交方向求和与价格tick区分、对齐价格周期 |
| [D160](#d160) | 范围未纳入 | TICK首次±700/1000极值顺势、后期重复极值高潮的阶段规则 |
| [D161](#d161) | 范围未纳入 | TICK新价格极值背离结合支阻的专家逆势与先顺势重测流程 |
| [D162](#d162) | 范围未纳入 | TICK自身前高前低支阻及持续零轴一侧的广度偏置 |
| [D163](#d163) | 定义/口径差异 | Body gap 的非相邻实体参照与系统相邻限定 |
| [D164](#d164) | 未具体吸收 | Gap reversal 越前棒一跳但不必到真正缺口边界 |
| [D165](#d165) | 部分吸收 | Exhaustion gap 的停止或小反转定义不要求缺口关闭 |
| [D166](#d166) | 定义/口径差异 | 来源 failure/success 的止损与目标先后及系统市场/交易结果分离 |

<a id="d001"></a>

## D001 outside bar 相等边界口径

**定义/口径差异。** 课程允许 outside 两端均相等，当前至少一端严格越界，采用的是另一公开来源口径；相同范围的 K 会被不同标注。

系统定位：[market E. K 线与运动事实](../../trading_system/market.md#e-k-线与运动事实)（L598）。

来源（链接中保留物理页码和条件）：[01·7](lessons/01.md#r7)、[08B·4](lessons/08B.md#r4)、[来源台账：inside bar / outside bar](../../reference/official_sources.md#来源锚点定位)。

<a id="d002"></a>

## D002 固定目标/失效/期限与趋势存续式持有

**方法取舍。** 来源允许随趋势存续持有、动态寻找兑现机会；当前授权必须有目标、失效和期限。未来方案可以更新，但不能改写旧预测；替代方法已列研究。

系统定位：[market 3.7 条件路径与目标](../../trading_system/market.md#37-条件路径与目标)（L357）；[trade 3.1 从条件路径开始](../../trading_system/trade.md#31-从条件路径开始)（L33）；[governance 待验证的交易与使用效果](../../trading_system/governance.md#待验证的交易与使用效果)（L256）。

来源（链接中保留物理页码和条件）：[01·8](lessons/01.md#r8)、[03D·3](lessons/03D.md#r3)、[13A·4](lessons/13A.md#r4)、[13B·2](lessons/13B.md#r2)、[13C·4](lessons/13C.md#r4)、[19D·1](lessons/19D.md#r1)、[20A·2](lessons/20A.md#r2)、[24E·3](lessons/24E.md#r3)、[31D·4](lessons/31D.md#r4)、[33B·1](lessons/33B.md#r1)、[33D·4](lessons/33D.md#r4)、[40C·3](lessons/40C.md#r3)、[45A·3](lessons/45A.md#r3)、[45D·1](lessons/45D.md#r1)、[46A·2](lessons/46A.md#r2)、[46C·3](lessons/46C.md#r3)。

<a id="d003"></a>

## D003 Chart Entry Bar 与实际成交 entry bar

**已覆盖（消歧）。** 来源 entry bar 有实际进入和图表触发两种用法；当前拆成 Chart Entry Bar 与真实成交。所需功能已经覆盖，本项不计作未吸收。

系统定位：[market E. K 线与运动事实](../../trading_system/market.md#e-k-线与运动事实)（L598）；[account 三、提交与平台记录](../../trading_system/account.md#三提交与平台记录)（L42）。

来源（链接中保留物理页码和条件）：[01·10](lessons/01.md#r10)、[08A·3](lessons/08A.md#r3)、[08B·4](lessons/08B.md#r4)、[09A·5](lessons/09A.md#r5)、[19D·4](lessons/19D.md#r4)、[来源台账：signal bar / entry bar](../../reference/official_sources.md#来源锚点定位)。

<a id="d004"></a>

## D004 量价背离的条件及两种后续

**部分吸收。** 来源给出新低成交量下降时反弹或横盘两种后续；当前只说 volume 可辅助、须连到价格，没有保留这一具体条件经验。

系统定位：[market 3.1 事实、关系与判断](../../trading_system/market.md#31-事实关系与判断)（L47）。

来源（链接中保留物理页码和条件）：[02B·1](lessons/02B.md#r1)、[18A·1](lessons/18A.md#r1)。

<a id="d005"></a>

## D005 经纪商破产、信誉与结算不交付风险

**部分吸收。** 当前平台检查涵盖执行能力、保证金及清算，不包含来源的经纪商信誉、破产和结算不交付风险；历史公司案例本身不成为参数。

系统定位：[account 五、低频平台检查](../../trading_system/account.md#五低频平台检查)（L112）。

来源（链接中保留物理页码和条件）：[02B·4](lessons/02B.md#r4)、[03A·6](lessons/03A.md#r6)。

<a id="d006"></a>

## D006 参与者动机、市场机制与理论解释

**研究/隔离。** 系统明确把身份、持仓、动机视为推断；没有把来源机构、算法、供需及心理因果叙事作为已证实机制。各个叙事和对应来源在 D006 细目中分别保留。

系统定位：[market 3.1 事实、关系与判断](../../trading_system/market.md#31-事实关系与判断)（L47）；[governance 四、知识进入方法前先拆清楚](../../trading_system/governance.md#四知识进入方法前先拆清楚)（L139）。

来源：[183 个来源思想组的完整分项](details/D006.md)。

<a id="d007"></a>

## D007 经验数字、历史参数、无样本断言和源内数学冲突

**研究/隔离。** 来源经验百分比、时间/根数/点数、历史参数、绩效断言和内部错误未成为生产数值规则。系统已有隔离原则；每个来源条件在 D007 细目中列出，不将所有数字合成一个胜率。

系统定位：[governance 3. 已校准的数值规则](../../trading_system/governance.md#3-已校准的数值规则)（L191）；[governance 四、知识进入方法前先拆清楚](../../trading_system/governance.md#四知识进入方法前先拆清楚)（L139）。

来源：[434 个课程思想组及其他入库命题的完整分项](details/D007.md)。

<a id="d008"></a>

## D008 trapped in 与 trapped out 的角色和行为链

**部分吸收。** 当前会使用 trapped/pain 但未完整定义 trapped in、从未进入/等待/过早退出的 trapped out 及已平仓者；真实持仓仍不可从 K 线确认。

系统定位：[market 3.1 事实、关系与判断](../../trading_system/market.md#31-事实关系与判断)（L47）。

来源（链接中保留物理页码和条件）：[02C·5](lessons/02C.md#r5)、[08C·5](lessons/08C.md#r5)、[14C·4](lessons/14C.md#r4)、[15A·5](lessons/15A.md#r5)、[15C·1](lessons/15C.md#r1)、[16E·5](lessons/16E.md#r5)、[17A·5](lessons/17A.md#r5)、[18E·4](lessons/18E.md#r4)、[22A·4](lessons/22A.md#r4)、[25A·2](lessons/25A.md#r2)、[30E·5](lessons/30E.md#r5)、[40A·2](lessons/40A.md#r2)、[40C·2](lessons/40C.md#r2)。

<a id="d009"></a>

## D009 流动性、时段重叠/清淡与参与选择

**部分吸收。** 已有 Session 和流动性条件；没有具体保留活跃市场重叠、清淡时段与不同产品参与难度的对照。

系统定位：[market 3.2 观察边界与多周期](../../trading_system/market.md#32-观察边界与多周期)（L80）；[account 五、低频平台检查](../../trading_system/account.md#五低频平台检查)（L112）。

来源（链接中保留物理页码和条件）：[03A·3](lessons/03A.md#r3)、[03C·6](lessons/03C.md#r6)、[07A·6](lessons/07A.md#r6)。

<a id="d010"></a>

## D010 外汇币种、pip/tick、名义额和点值换算

**部分吸收。** 已有 tick、每点价值和净损失公式；未完整说明 base/quote/账户币种、pip 与 fractional pip、名义额及换汇换算链。历史点值不能复制。

系统定位：[account 五、低频平台检查](../../trading_system/account.md#五低频平台检查)（L112）；[trade 3.7 判断是否值得](../../trading_system/trade.md#37-判断是否值得)（L166）。

来源（链接中保留物理页码和条件）：[03A·1](lessons/03A.md#r1)、[03B·2](lessons/03B.md#r2)、[03B·4](lessons/03B.md#r4)、[03C·1](lessons/03C.md#r1)、[03C·5](lessons/03C.md#r5)、[03C·6](lessons/03C.md#r6)、[03E·2](lessons/03E.md#r2)、[15D·10](lessons/15D.md#r10)、[15G·3](lessons/15G.md#r3)、[16F·4](lessons/16F.md#r4)、[18D·4](lessons/18D.md#r4)、[19B·2](lessons/19B.md#r2)、[19C·3](lessons/19C.md#r3)、[21A·1](lessons/21A.md#r1)、[21D·1](lessons/21D.md#r1)、[22B·1](lessons/22B.md#r1)、[30A·3](lessons/30A.md#r3)、[30B·1](lessons/30B.md#r1)、[30C·3](lessons/30C.md#r3)、[30C·7](lessons/30C.md#r7)、[30D·4](lessons/30D.md#r4)、[31A·5](lessons/31A.md#r5)、[31B·1](lessons/31B.md#r1)、[36B·4](lessons/36B.md#r4)。

<a id="d011"></a>

## D011 基准定价窗口的事件风险

**未具体吸收。** 来源的基准汇率定价窗口及相关集中交易风险没有专门表达；通用新闻/尾部风险不足以说明该事件机制。

系统定位：[market 3.1 事实、关系与判断](../../trading_system/market.md#31-事实关系与判断)（L47）；[account 五、低频平台检查](../../trading_system/account.md#五低频平台检查)（L112）。

来源（链接中保留物理页码和条件）：[03B·3](lessons/03B.md#r3)、[05·4](lessons/05.md#r4)。

<a id="d012"></a>

## D012 Bid/Ask 点差的成本口径

**部分吸收。** 成本后判断已有，但 Bid/Ask 点差及其与手续费、滑点的具体区别未列明，不能只用旧案例点差代替现行成本。

系统定位：[trade 3.7 判断是否值得](../../trading_system/trade.md#37-判断是否值得)（L166）；[account 五、低频平台检查](../../trading_system/account.md#五低频平台检查)（L112）。

来源（链接中保留物理页码和条件）：[03A·6](lessons/03A.md#r6)、[03B·1](lessons/03B.md#r1)、[03C·4](lessons/03C.md#r4)、[03C·6](lessons/03C.md#r6)、[31C·6](lessons/31C.md#r6)。

<a id="d013"></a>

## D013 Bid/Ask 构图、订单触发与成交侧对应

**部分吸收。** 触价不等于成交已覆盖；未定义 Bid/Ask 图与买卖触发、平仓侧的对应。偏移和报价源差异仍可能改变图表价与订单判断。

系统定位：[account 三、提交与平台记录](../../trading_system/account.md#三提交与平台记录)（L42）；[account 五、低频平台检查](../../trading_system/account.md#五低频平台检查)（L112）。

来源（链接中保留物理页码和条件）：[03D·1](lessons/03D.md#r1)、[03D·2](lessons/03D.md#r2)、[15G·3](lessons/15G.md#r3)、[19B·2](lessons/19B.md#r2)、[19D·2](lessons/19D.md#r2)、[19E·4](lessons/19E.md#r4)、[30E·1](lessons/30E.md#r1)、[31B·3](lessons/31B.md#r3)、[31C·6](lessons/31C.md#r6)、[31D·2](lessons/31D.md#r2)、[32A·3](lessons/32A.md#r3)、[32A·5](lessons/32A.md#r5)、[32A·6](lessons/32A.md#r6)、[32B·4](lessons/32B.md#r4)、[32C·3](lessons/32C.md#r3)、[40D·1](lessons/40D.md#r1)、[41A·3](lessons/41A.md#r3)、[43C·2](lessons/43C.md#r2)、[44C·2](lessons/44C.md#r2)、[48H·1](lessons/48H.md#r1)。

<a id="d014"></a>

## D014 日切、换汇、利息收付与多日计息

**部分吸收。** 已计持有成本，但未保留隔夜日切、利息收付、币种换算、多日计息等产品知识及条件。

系统定位：[trade 3.7 判断是否值得](../../trading_system/trade.md#37-判断是否值得)（L166）；[account 五、低频平台检查](../../trading_system/account.md#五低频平台检查)（L112）。

来源（链接中保留物理页码和条件）：[03A·6](lessons/03A.md#r6)、[03C·2](lessons/03C.md#r2)、[03E·3](lessons/03E.md#r3)、[03E·4](lessons/03E.md#r4)。

<a id="d015"></a>

## D015 Carry 长期利差策略

**范围未纳入。** 长期赚取币种利差的 Carry 策略未纳入当前价格运动交易流程；利息成本已覆盖，利差策略不等于成本字段。

系统定位：[trade 3.1 从条件路径开始](../../trading_system/trade.md#31-从条件路径开始)（L33）；[account 五、低频平台检查](../../trading_system/account.md#五低频平台检查)（L112）。

来源（链接中保留物理页码和条件）：[03E·4](lessons/03E.md#r4)。

<a id="d016"></a>

## D016 Session 模板与合约序列的数据口径

**部分吸收。** 已要求固定 Session、数据源与 K 构造，未完整列出 RTH/ETH、连续合约/换月等对图形和 SR 的具体影响。

系统定位：[market 3.2 观察边界与多周期](../../trading_system/market.md#32-观察边界与多周期)（L80）。

来源（链接中保留物理页码和条件）：[04·3](lessons/04.md#r3)、[38C·1](lessons/38C.md#r1)。

<a id="d017"></a>

## D017 跨周期 EMA 近似、真实值与临时值

**未具体吸收。** 引用高周期 EMA 已有，但没有保留低周期近似高周期均线与真实高周期 EMA 的数值差异；未完成值也需与最终值分开。

系统定位：[market 3.2 观察边界与多周期](../../trading_system/market.md#32-观察边界与多周期)（L80）；[market 3.5 重要区域图与路径作用](../../trading_system/market.md#35-重要区域图与路径作用)（L178）。

来源（链接中保留物理页码和条件）：[04·4](lessons/04.md#r4)、[48C·1](lessons/48C.md#r1)。

<a id="d018"></a>

## D018 套利与跨市场配对策略

**范围未纳入。** 配对、套利、跨市场同时持仓是来源中的其他策略；当前单向单笔框架没有这些组合规则。

系统定位：[trade 3.1 从条件路径开始](../../trading_system/trade.md#31-从条件路径开始)（L33）；[account 五、低频平台检查](../../trading_system/account.md#五低频平台检查)（L112）。

来源（链接中保留物理页码和条件）：[05·2](lessons/05.md#r2)、[31D·5](lessons/31D.md#r5)。

<a id="d019"></a>

## D019 专注和情绪干扰下的个人运行条件

**部分吸收。** 小仓位、行为复盘、学习损失和退回条件已有；疲劳、健康、家庭干扰、无法专注等即时不交易/暂停/减量条件未完整进入盘中规则。

系统定位：[Practice 晋级与退回](../../practice/README.md#晋级与退回)（L245）；[trade 3.1 从条件路径开始](../../trading_system/trade.md#31-从条件路径开始)（L33）。

来源（链接中保留物理页码和条件）：[04·1](lessons/04.md#r1)、[06·1](lessons/06.md#r1)、[07B·3](lessons/07B.md#r3)、[08A·4](lessons/08A.md#r4)、[14B·3](lessons/14B.md#r3)、[15B·6](lessons/15B.md#r6)、[30C·4](lessons/30C.md#r4)、[31A·1](lessons/31A.md#r1)、[31C·4](lessons/31C.md#r4)、[33A·3](lessons/33A.md#r3)、[33A·4](lessons/33A.md#r4)、[33F·6](lessons/33F.md#r6)、[33G·1](lessons/33G.md#r1)、[35A·1](lessons/35A.md#r1)、[35C·3](lessons/35C.md#r3)、[36A·3](lessons/36A.md#r3)、[37B·2](lessons/37B.md#r2)、[39C·2](lessons/39C.md#r2)、[40A·2](lessons/40A.md#r2)、[47C·3](lessons/47C.md#r3)、[48I·1](lessons/48I.md#r1)、[50A·3](lessons/50A.md#r3)、[50B·2](lessons/50B.md#r2)、[51A·2](lessons/51A.md#r2)、[51D·2](lessons/51D.md#r2)。

<a id="d020"></a>

## D020 强突破阶段只顺势的参与限制

**方法取舍。** 来源多次对强 BO/紧通道规定只顺势，当前在方向已清楚时容许有依据的有限逆向目标；只有分类仍不清时才严格限制。来源自己也有专家、高潮及局部反向例外，不能概括成绝对冲突。

系统定位：[market 3.4 市场结构与持续能力](../../trading_system/market.md#34-市场结构与持续能力)（L111）；[scenarios 八、趋势受损后尝试反转](../../trading_system/scenarios.md#八趋势受损后尝试反转)（L157）；[trade 3.1 从条件路径开始](../../trading_system/trade.md#31-从条件路径开始)（L33）。

来源（链接中保留物理页码和条件）：[06·6](lessons/06.md#r6)、[08D·1](lessons/08D.md#r1)、[09B·6](lessons/09B.md#r6)、[11D·2](lessons/11D.md#r2)、[12A·2](lessons/12A.md#r2)、[12C·3](lessons/12C.md#r3)、[13C·2](lessons/13C.md#r2)、[14B·2](lessons/14B.md#r2)、[14E·1](lessons/14E.md#r1)、[14E·3](lessons/14E.md#r3)、[16B·5](lessons/16B.md#r5)、[16C·4](lessons/16C.md#r4)、[16D·2](lessons/16D.md#r2)、[16E·3](lessons/16E.md#r3)、[17A·1](lessons/17A.md#r1)、[19A·1](lessons/19A.md#r1)、[21C·1](lessons/21C.md#r1)、[22D·1](lessons/22D.md#r1)、[24C·1](lessons/24C.md#r1)、[24D·3](lessons/24D.md#r3)、[24D·5](lessons/24D.md#r5)、[28·2](lessons/28.md#r2)、[30A·1](lessons/30A.md#r1)、[30C·4](lessons/30C.md#r4)、[31A·1](lessons/31A.md#r1)、[31C·1](lessons/31C.md#r1)、[32B·3](lessons/32B.md#r3)、[35A·4](lessons/35A.md#r4)、[37A·1](lessons/37A.md#r1)、[37A·2](lessons/37A.md#r2)、[37B·1](lessons/37B.md#r1)、[40A·2](lessons/40A.md#r2)、[40A·4](lessons/40A.md#r4)、[40C·3](lessons/40C.md#r3)、[40D·3](lessons/40D.md#r3)、[40E·1](lessons/40E.md#r1)、[41A·1](lessons/41A.md#r1)、[41C·3](lessons/41C.md#r3)、[42A·2](lessons/42A.md#r2)、[42B·2](lessons/42B.md#r2)、[43A·1](lessons/43A.md#r1)、[43A·2](lessons/43A.md#r2)、[43C·1](lessons/43C.md#r1)、[43C·3](lessons/43C.md#r3)、[44A·1](lessons/44A.md#r1)、[44B·2](lessons/44B.md#r2)、[44C·1](lessons/44C.md#r1)、[45C·2](lessons/45C.md#r2)、[45D·3](lessons/45D.md#r3)、[46A·1](lessons/46A.md#r1)、[46B·3](lessons/46B.md#r3)、[46D·3](lessons/46D.md#r3)、[47B·2](lessons/47B.md#r2)、[47C·2](lessons/47C.md#r2)、[48E·2](lessons/48E.md#r2)、[48H·3](lessons/48H.md#r3)、[49A·2](lessons/49A.md#r2)、[51A·3](lessons/51A.md#r3)。

<a id="d021"></a>

## D021 参与质量优先与管理优先的教学重心

**方法取舍。** 来源强调管理能挽救大量入场、正方程交易可同样好；系统明确优先改善参与质量。两者共享方程，重心和优先级不同，尚无比较效果结论。

系统定位：[README 判断与行动的主线](../../trading_system/README.md#判断与行动的主线)（L7）；[governance 四、知识进入方法前先拆清楚](../../trading_system/governance.md#四知识进入方法前先拆清楚)（L139）。

来源（链接中保留物理页码和条件）：[06·5](lessons/06.md#r5)、[37A·2](lessons/37A.md#r2)、[41A·2](lessons/41A.md#r2)、[41A·4](lessons/41A.md#r4)、[41C·3](lessons/41C.md#r3)、[48G·3](lessons/48G.md#r3)、[51A·1](lessons/51A.md#r1)、[51B·1](lessons/51B.md#r1)。

<a id="d022"></a>

## D022 多数人优先 swing 与潜在至少 2R 的教学默认

**方法取舍。** 来源建议多数人尤其初学者以 Swing、通常至少 2R 为默认；当前可选机会族和管理基准，并无该风格默认，净回报硬门槛为整笔至少 1 倍净风险。

系统定位：[trade 3.1 从条件路径开始](../../trading_system/trade.md#31-从条件路径开始)（L33）；[Practice 晋级与退回](../../practice/README.md#晋级与退回)（L245）。

来源（链接中保留物理页码和条件）：[06·4](lessons/06.md#r4)、[07B·1](lessons/07B.md#r1)、[12A·2](lessons/12A.md#r2)、[13A·4](lessons/13A.md#r4)、[13C·3](lessons/13C.md#r3)、[14C·3](lessons/14C.md#r3)、[15E·3](lessons/15E.md#r3)、[21B·1](lessons/21B.md#r1)、[21C·1](lessons/21C.md#r1)、[21D·1](lessons/21D.md#r1)、[21D·4](lessons/21D.md#r4)、[22B·2](lessons/22B.md#r2)、[23B·1](lessons/23B.md#r1)、[27A·1](lessons/27A.md#r1)、[30A·2](lessons/30A.md#r2)、[30D·2](lessons/30D.md#r2)、[30E·2](lessons/30E.md#r2)、[30E·3](lessons/30E.md#r3)、[31A·4](lessons/31A.md#r4)、[31C·5](lessons/31C.md#r5)、[31D·3](lessons/31D.md#r3)、[32B·1](lessons/32B.md#r1)、[33G·4](lessons/33G.md#r4)、[34A·1](lessons/34A.md#r1)、[37B·3](lessons/37B.md#r3)、[来源台账：SRC-RISK-113 Trading goals](../../reference/official_sources.md#来源锚点定位)。

<a id="d023"></a>

## D023 周期、市场和复杂度须匹配人工负荷

**部分吸收。** 运行负荷和适用产品检查已有；课程的人工周期/屏幕复杂度选择、极端波动暂停、1 分钟难度及每小时至多约 20 棒建议未完整列出。

系统定位：[market 3.2 观察边界与多周期](../../trading_system/market.md#32-观察边界与多周期)（L80）；[Practice 晋级与退回](../../practice/README.md#晋级与退回)（L245）。

来源（链接中保留物理页码和条件）：[06·3](lessons/06.md#r3)、[07A·4](lessons/07A.md#r4)、[07A·6](lessons/07A.md#r6)、[08B·6](lessons/08B.md#r6)、[13C·2](lessons/13C.md#r2)、[13C·3](lessons/13C.md#r3)、[15B·6](lessons/15B.md#r6)、[16F·1](lessons/16F.md#r1)、[18D·1](lessons/18D.md#r1)、[18D·3](lessons/18D.md#r3)、[22B·2](lessons/22B.md#r2)、[24D·1](lessons/24D.md#r1)、[30B·1](lessons/30B.md#r1)、[31A·1](lessons/31A.md#r1)、[31C·4](lessons/31C.md#r4)、[31D·3](lessons/31D.md#r3)、[33F·3](lessons/33F.md#r3)、[37A·3](lessons/37A.md#r3)、[40A·2](lessons/40A.md#r2)、[41B·4](lessons/41B.md#r4)、[41B·5](lessons/41B.md#r5)、[43A·2](lessons/43A.md#r2)、[44A·2](lessons/44A.md#r2)、[50A·3](lessons/50A.md#r3)、[50B·1](lessons/50B.md#r1)、[50B·2](lessons/50B.md#r2)。

<a id="d024"></a>

## D024 本人感受作为观察 radar

**未具体吸收。** 来源将困惑、恐惧、希望等本人感觉用作重新检查背景的 radar；系统主要处理客观事实与盘后偏差，未保留这一观察提示机制，感觉也不能替代证据。

系统定位：[market 3.1 事实、关系与判断](../../trading_system/market.md#31-事实关系与判断)（L47）；[Practice 晋级与退回](../../practice/README.md#晋级与退回)（L245）。

来源（链接中保留物理页码和条件）：[07B·6](lessons/07B.md#r6)、[15D·8](lessons/15D.md#r8)、[18A·3](lessons/18A.md#r3)、[18F·3](lessons/18F.md#r3)、[21C·1](lessons/21C.md#r1)、[22B·3](lessons/22B.md#r3)、[30C·4](lessons/30C.md#r4)、[30E·5](lessons/30E.md#r5)、[33A·3](lessons/33A.md#r3)、[43A·3](lessons/43A.md#r3)、[43C·3](lessons/43C.md#r3)、[44A·3](lessons/44A.md#r3)、[47C·1](lessons/47C.md#r1)、[51A·2](lessons/51A.md#r2)。

<a id="d025"></a>

## D025 期权替代持股的承担方式

**范围未纳入。** 来源的期权替代股票、保护性 put/call 与价差等承担方式未在系统实现；一般仓位预算并不包含期权非线性风险建模。

系统定位：[trade 3.1 从条件路径开始](../../trading_system/trade.md#31-从条件路径开始)（L33）；[account 五、低频平台检查](../../trading_system/account.md#五低频平台检查)（L112）。

来源（链接中保留物理页码和条件）：[07A·2](lessons/07A.md#r2)、[29E·1](lessons/29E.md#r1)、[32A·2](lessons/32A.md#r2)、[33F·5](lessons/33F.md#r5)、[41B·4](lessons/41B.md#r4)。

<a id="d026"></a>

## D026 强趋势中必须/尽快加入与当前可放弃的门槛

**方法取舍。** 来源有强趋势必须立即/尽快小仓进入的强措辞；当前没有合算价格、保护、目标或时间就等待/放弃。来源后期高潮与远目标障碍的反例同时保留。

系统定位：[trade 3.1 从条件路径开始](../../trading_system/trade.md#31-从条件路径开始)（L33）；[trade 3.7 判断是否值得](../../trading_system/trade.md#37-判断是否值得)（L166）。

来源（链接中保留物理页码和条件）：[07A·1](lessons/07A.md#r1)、[07B·7](lessons/07B.md#r7)、[08D·3](lessons/08D.md#r3)、[09A·3](lessons/09A.md#r3)、[09B·7](lessons/09B.md#r7)、[10B·3](lessons/10B.md#r3)、[12C·5](lessons/12C.md#r5)、[13A·2](lessons/13A.md#r2)、[13B·1](lessons/13B.md#r1)、[13B·5](lessons/13B.md#r5)、[13C·1](lessons/13C.md#r1)、[14C·4](lessons/14C.md#r4)、[14E·5](lessons/14E.md#r5)、[15D·10](lessons/15D.md#r10)、[16F·2](lessons/16F.md#r2)、[17A·5](lessons/17A.md#r5)、[17B·6](lessons/17B.md#r6)、[21A·2](lessons/21A.md#r2)、[31A·4](lessons/31A.md#r4)、[32B·4](lessons/32B.md#r4)、[32C·3](lessons/32C.md#r3)、[33B·3](lessons/33B.md#r3)、[35B·4](lessons/35B.md#r4)、[37B·1](lessons/37B.md#r1)、[37B·4](lessons/37B.md#r4)、[38C·1](lessons/38C.md#r1)、[39B·2](lessons/39B.md#r2)、[40A·2](lessons/40A.md#r2)、[40A·4](lessons/40A.md#r4)、[40C·3](lessons/40C.md#r3)、[41A·2](lessons/41A.md#r2)、[41C·3](lessons/41C.md#r3)、[41D·1](lessons/41D.md#r1)、[41D·2](lessons/41D.md#r2)、[42B·3](lessons/42B.md#r3)、[43A·3](lessons/43A.md#r3)、[43B·2](lessons/43B.md#r2)、[43D·1](lessons/43D.md#r1)、[44A·3](lessons/44A.md#r3)、[44B·2](lessons/44B.md#r2)、[44C·3](lessons/44C.md#r3)、[44D·1](lessons/44D.md#r1)、[45E·1](lessons/45E.md#r1)、[46E·1](lessons/46E.md#r1)、[48C·3](lessons/48C.md#r3)、[48F·2](lessons/48F.md#r2)、[48H·3](lessons/48H.md#r3)、[48K·2](lessons/48K.md#r2)、[49A·1](lessons/49A.md#r1)、[49A·4](lessons/49A.md#r4)、[49C·2](lessons/49C.md#r2)、[49D·3](lessons/49D.md#r3)、[49E·2](lessons/49E.md#r2)、[52A·1](lessons/52A.md#r1)。

<a id="d027"></a>

## D027 信号质量相对开收、影线、前序与顺逆背景

**部分吸收。** 当前已有大小、收盘、影线、重叠和背景比较，但没有完整保留逐棒相对开收/前高低、连续数、无反色、on 与 near、失败跟随和具体早退配方；各条件见 D027 细目。

系统定位：[market 当前运动的强弱](../../trading_system/market.md#当前运动的强弱)（L227）；[market E. K 线与运动事实](../../trading_system/market.md#e-k-线与运动事实)（L598）。

来源：[129 个来源思想组的完整分项](details/D027.md)。

<a id="d028"></a>

## D028 影线与低周期失败突破的解释桥梁

**部分吸收。** 当前有多周期共享事实；未明示长影线如何对应低周期失败突破/反向运动，不能仅由影线推断未观察的低周期实际结构。

系统定位：[market E. K 线与运动事实](../../trading_system/market.md#e-k-线与运动事实)（L598）；[market 3.2 观察边界与多周期](../../trading_system/market.md#32-观察边界与多周期)（L80）。

来源（链接中保留物理页码和条件）：[08A·2](lessons/08A.md#r2)、[15A·4](lessons/15A.md#r4)、[15D·9](lessons/15D.md#r9)、[21A·1](lessons/21A.md#r1)。

<a id="d029"></a>

## D029 buy/sell reversal 与 bull/bear body、中点条件

**部分吸收。** 来源 buy/sell reversal 按价格反转方向定义，可为反色实体，并有中点等条件；当前把 Reversal 作为作用，但没有完整列出该操作方向与实体颜色的区别。

系统定位：[market E. K 线与运动事实](../../trading_system/market.md#e-k-线与运动事实)（L598）。

来源（链接中保留物理页码和条件）：[08B·1](lessons/08B.md#r1)。

<a id="d030"></a>

## D030 两根反转的非连续多棒用法与聚合边界

**部分吸收。** 当前允许 multi-bar reversal；未完整说明课程中非相邻两根的功能性反转与严格相邻双棒、合成高周期单棒的关系。

系统定位：[market E. K 线与运动事实](../../trading_system/market.md#e-k-线与运动事实)（L598）；[market 3.2 观察边界与多周期](../../trading_system/market.md#32-观察边界与多周期)（L80）。

来源（链接中保留物理页码和条件）：[08B·3](lessons/08B.md#r3)、[21A·1](lessons/21A.md#r1)。

<a id="d031"></a>

## D031 Outside bar 按背景选择限价反做或顺向突破

**部分吸收。** 一般 Limit/Stop 选择已具备；弱 Outside 或弱信号在 TR/顺势背景下反做信号高低点，与强突破顺向触发的具体条件未完整表达。

系统定位：[trade 3.2 确认程度与订单条件](../../trading_system/trade.md#32-确认程度与订单条件)（L58）；[scenarios 八、趋势受损后尝试反转](../../trading_system/scenarios.md#八趋势受损后尝试反转)（L157）。

来源（链接中保留物理页码和条件）：[08C·3](lessons/08C.md#r3)、[32B·2](lessons/32B.md#r2)、[32C·2](lessons/32C.md#r2)、[50D·2](lessons/50D.md#r2)、[50E·1](lessons/50E.md#r1)、[51B·3](lessons/51B.md#r3)。

<a id="d032"></a>

## D032 小 TTR/ii/ioi 末棒方向、EMA位置及跟随质量

**部分吸收。** 当前保留 ii/ioi 压缩几何；末根颜色、EMA 相对位置、失望跟随怎样改变小 TTR 选择，没有逐项列出。

系统定位：[market A. 结构视图怎样共享事实](../../trading_system/market.md#a-结构视图怎样共享事实)（L481）；[market 当前运动的强弱](../../trading_system/market.md#当前运动的强弱)（L227）。

来源（链接中保留物理页码和条件）：[08C·4](lessons/08C.md#r4)、[08C·5](lessons/08C.md#r5)、[08C·6](lessons/08C.md#r6)、[31D·1](lessons/31D.md#r1)、[42C·3](lessons/42C.md#r3)。

<a id="d033"></a>

## D033 BOM 的宽泛小 TTR 与当前结构用法

**定义/口径差异。** 来源 BOM 可宽泛用于 2–5 棒 TTR，也有成熟中性区间与早期旗形区别；系统共用压缩/双向结构，未列专门 BOM 子型，不能由小 ii 推断中性。

系统定位：[market A. 结构视图怎样共享事实](../../trading_system/market.md#a-结构视图怎样共享事实)（L481）；[scenarios 五、价格到达区间或宽通道边缘](../../trading_system/scenarios.md#五价格到达区间或宽通道边缘)（L96）。

来源（链接中保留物理页码和条件）：[08C·2](lessons/08C.md#r2)、[18B·3](lessons/18B.md#r3)、[18C·1](lessons/18C.md#r1)、[23B·3](lessons/23B.md#r3)、[25A·5](lessons/25A.md#r5)、[25B·2](lessons/25B.md#r2)、[26A·1](lessons/26A.md#r1)、[26A·2](lessons/26A.md#r2)、[29B·4](lessons/29B.md#r4)、[29E·4](lessons/29E.md#r4)、[39C·2](lessons/39C.md#r2)、[40E·2](lessons/40E.md#r2)、[45C·3](lessons/45C.md#r3)、[45E·2](lessons/45E.md#r2)、[46C·2](lessons/46C.md#r2)、[46E·2](lessons/46E.md#r2)、[48B·1](lessons/48B.md#r1)、[48D·1](lessons/48D.md#r1)、[48F·2](lessons/48F.md#r2)、[48G·1](lessons/48G.md#r1)、[49B·1](lessons/49B.md#r1)、[49D·3](lessons/49D.md#r3)、[49E·2](lessons/49E.md#r2)。

<a id="d034"></a>

## D034 复杂分批及专家方法的个人能力准入

**部分吸收。** 已有分级练习和能力/经济验收；没有课程中专家限价、逆势分层、1 分钟、快速反手等逐策略个人门槛。部分来源案例未限制专家，不能一律补上。

系统定位：[Practice 晋级与退回](../../practice/README.md#晋级与退回)（L245）；[trade 四、加仓与分层](../../trading_system/trade.md#四加仓与分层)（L214）。

来源（链接中保留物理页码和条件）：[08D·2](lessons/08D.md#r2)、[14D·5](lessons/14D.md#r5)、[15C·4](lessons/15C.md#r4)、[15G·2](lessons/15G.md#r2)、[16E·1](lessons/16E.md#r1)、[16F·1](lessons/16F.md#r1)、[17B·2](lessons/17B.md#r2)、[18B·2](lessons/18B.md#r2)、[18C·3](lessons/18C.md#r3)、[18D·3](lessons/18D.md#r3)、[18F·2](lessons/18F.md#r2)、[18F·3](lessons/18F.md#r3)、[19D·3](lessons/19D.md#r3)、[19E·1](lessons/19E.md#r1)、[24E·3](lessons/24E.md#r3)、[30E·2](lessons/30E.md#r2)、[31A·4](lessons/31A.md#r4)、[31C·1](lessons/31C.md#r1)、[31C·4](lessons/31C.md#r4)、[31C·5](lessons/31C.md#r5)、[31D·2](lessons/31D.md#r2)、[32B·2](lessons/32B.md#r2)、[33B·2](lessons/33B.md#r2)、[33G·4](lessons/33G.md#r4)、[33G·5](lessons/33G.md#r5)、[35A·1](lessons/35A.md#r1)、[35A·3](lessons/35A.md#r3)、[35A·4](lessons/35A.md#r4)、[35C·1](lessons/35C.md#r1)、[35C·3](lessons/35C.md#r3)、[37A·3](lessons/37A.md#r3)、[37B·1](lessons/37B.md#r1)、[38D·3](lessons/38D.md#r3)、[39C·2](lessons/39C.md#r2)、[40A·3](lessons/40A.md#r3)、[41A·3](lessons/41A.md#r3)、[41B·4](lessons/41B.md#r4)、[41C·1](lessons/41C.md#r1)、[41D·2](lessons/41D.md#r2)、[42A·1](lessons/42A.md#r1)、[42A·2](lessons/42A.md#r2)、[42A·3](lessons/42A.md#r3)、[43C·1](lessons/43C.md#r1)、[43C·2](lessons/43C.md#r2)、[44C·1](lessons/44C.md#r1)、[44C·2](lessons/44C.md#r2)、[47C·1](lessons/47C.md#r1)、[47C·2](lessons/47C.md#r2)、[48B·2](lessons/48B.md#r2)、[48J·2](lessons/48J.md#r2)、[49A·2](lessons/49A.md#r2)、[49B·1](lessons/49B.md#r1)、[49B·3](lessons/49B.md#r3)、[49C·3](lessons/49C.md#r3)、[50A·1](lessons/50A.md#r1)、[50A·3](lessons/50A.md#r3)、[50B·1](lessons/50B.md#r1)、[50C·2](lessons/50C.md#r2)、[50C·3](lessons/50C.md#r3)、[50D·1](lessons/50D.md#r1)、[51D·3](lessons/51D.md#r3)、[52A·4](lessons/52A.md#r4)。

<a id="d035"></a>

## D035 Actual/Implied Pullback 的相邻极值最低判据

**部分吸收。** 当前 actual pullback 只写已出现反向高低点运动；未完整列出来源按相邻棒极值、暂停/反色 implied pullback 的最低几何及交叉关系。

系统定位：[market E. K 线与运动事实](../../trading_system/market.md#e-k-线与运动事实)（L598）；[market D. H/L 次序与重置](../../trading_system/market.md#d-hl-次序与重置)（L568）。

来源（链接中保留物理页码和条件）：[09A·1](lessons/09A.md#r1)、[12C·1](lessons/12C.md#r1)、[41B·1](lessons/41B.md#r1)。

<a id="d036"></a>

## D036 严格 H/L 触发计数与来源结构/段数映射

**定义/口径差异。** 系统明确严格 above/below 触发；来源还有 at-or、按段数、未触发 H2 标签、H4/H6 两组三推等口径。不能用图表计数替代实际成交。

系统定位：[market D. H/L 次序与重置](../../trading_system/market.md#d-hl-次序与重置)（L568）。

来源（链接中保留物理页码和条件）：[09A·5](lessons/09A.md#r5)、[09B·1](lessons/09B.md#r1)、[09B·4](lessons/09B.md#r4)、[09C·2](lessons/09C.md#r2)、[11D·4](lessons/11D.md#r4)、[16A·3](lessons/16A.md#r3)、[16B·3](lessons/16B.md#r3)、[16B·6](lessons/16B.md#r6)、[16C·3](lessons/16C.md#r3)、[17B·5](lessons/17B.md#r5)、[21B·3](lessons/21B.md#r3)、[24D·2](lessons/24D.md#r2)、[25A·1](lessons/25A.md#r1)、[25A·4](lessons/25A.md#r4)、[30E·4](lessons/30E.md#r4)、[33B·1](lessons/33B.md#r1)、[33F·4](lessons/33F.md#r4)、[39D·3](lessons/39D.md#r3)、[41A·3](lessons/41A.md#r3)、[42B·3](lessons/42B.md#r3)、[43D·3](lessons/43D.md#r3)、[44D·3](lessons/44D.md#r3)、[46C·2](lessons/46C.md#r2)、[48B·1](lessons/48B.md#r1)、[48E·1](lessons/48E.md#r1)、[48F·3](lessons/48F.md#r3)、[49B·2](lessons/49B.md#r2)、[49C·2](lessons/49C.md#r2)、[49D·3](lessons/49D.md#r3)、[50D·2](lessons/50D.md#r2)、[50E·3](lessons/50E.md#r3)、[52A·2](lessons/52A.md#r2)、[来源台账：SRC-10-PATTERNS at or / SRC-GLOSSARY above below](../../reference/official_sources.md#来源锚点定位)。

<a id="d037"></a>

## D037 连续反转尝试增加相对概率的启发式

**未具体吸收。** 当前不以编号增加概率；来源连续尝试、第二次信号更可靠的条件启发未完整保留。强趋势逆向连续失败并非单调提高下一次胜率。

系统定位：[market D. H/L 次序与重置](../../trading_system/market.md#d-hl-次序与重置)（L568）；[scenarios 八、趋势受损后尝试反转](../../trading_system/scenarios.md#八趋势受损后尝试反转)（L157）。

来源（链接中保留物理页码和条件）：[09B·5](lessons/09B.md#r5)、[14B·4](lessons/14B.md#r4)、[16B·2](lessons/16B.md#r2)、[16B·5](lessons/16B.md#r5)、[16C·4](lessons/16C.md#r4)、[16E·4](lessons/16E.md#r4)、[16F·5](lessons/16F.md#r5)、[17B·5](lessons/17B.md#r5)、[19A·1](lessons/19A.md#r1)、[24B·2](lessons/24B.md#r2)、[24E·2](lessons/24E.md#r2)、[26A·4](lessons/26A.md#r4)、[27B·2](lessons/27B.md#r2)、[32C·1](lessons/32C.md#r1)、[33B·1](lessons/33B.md#r1)、[38A·3](lessons/38A.md#r3)、[39A·1](lessons/39A.md#r1)、[48E·1](lessons/48E.md#r1)、[51B·3](lessons/51B.md#r3)。

<a id="d038"></a>

## D038 逆势持仓在原趋势 H2/L2 触发退出

**未具体吸收。** 已有反向证据失效退出；没有默认逆势持仓在原方向 H2/L2 或第二反向信号触发时退出的具体管理规则。

系统定位：[trade 3.5 出场、目标与期限](../../trading_system/trade.md#35-出场目标与期限)（L109）；[scenarios 八、趋势受损后尝试反转](../../trading_system/scenarios.md#八趋势受损后尝试反转)（L157）。

来源（链接中保留物理页码和条件）：[09C·3](lessons/09C.md#r3)、[21B·3](lessons/21B.md#r3)、[30A·3](lessons/30A.md#r3)、[31B·2](lessons/31B.md#r2)、[33A·4](lessons/33A.md#r4)、[34A·4](lessons/34A.md#r4)、[35A·4](lessons/35A.md#r4)、[38A·3](lessons/38A.md#r3)、[38B·2](lessons/38B.md#r2)、[38C·2](lessons/38C.md#r2)、[39D·3](lessons/39D.md#r3)、[42B·3](lessons/42B.md#r3)、[45E·1](lessons/45E.md#r1)、[46E·1](lessons/46E.md#r1)。

<a id="d039"></a>

## D039 Measuring gap 中点相对运动起点的对称投射

**部分吸收。** 当前有 gap 中点候选与普通高度投射，缺 gap 中点 M 相对运动起点 S 的 2M−S 对称构造，以及开放/负 gap 选边差异。

系统定位：[market 从哪些锚点投射候选区域](../../trading_system/market.md#从哪些锚点投射候选区域)（L519）；[market F. Gap：分离事实、直接引用与后续结果](../../trading_system/market.md#f-gap分离事实直接引用与后续结果)（L640）。

来源（链接中保留物理页码和条件）：[11A·4](lessons/11A.md#r4)、[11C·4](lessons/11C.md#r4)、[11D·1](lessons/11D.md#r1)、[14C·2](lessons/14C.md#r2)、[14E·7](lessons/14E.md#r7)、[15E·1](lessons/15E.md#r1)、[17B·4](lessons/17B.md#r4)、[18C·4](lessons/18C.md#r4)、[18E·2](lessons/18E.md#r2)、[20B·3](lessons/20B.md#r3)、[29A·2](lessons/29A.md#r2)、[29C·2](lessons/29C.md#r2)、[29D·2](lessons/29D.md#r2)、[29E·2](lessons/29E.md#r2)、[33E·5](lessons/33E.md#r5)、[34B·1](lessons/34B.md#r1)、[36A·1](lessons/36A.md#r1)、[38A·1](lessons/38A.md#r1)、[41D·3](lessons/41D.md#r3)、[46A·1](lessons/46A.md#r1)、[46E·3](lessons/46E.md#r3)、[来源台账：measuring gap / micro measuring gap](../../reference/official_sources.md#来源锚点定位)。

<a id="d040"></a>

## D040 岛形反转的几何变体和非独立预测力

**定义/口径差异。** 岛形、单棒或多棒及无实际空白的近似岛形变体没有具名定义；其一般突破失败/反转逻辑可由当前规则解释，不新增独立优势。

系统定位：[market F. Gap：分离事实、直接引用与后续结果](../../trading_system/market.md#f-gap分离事实直接引用与后续结果)（L640）；[market A. 结构视图怎样共享事实](../../trading_system/market.md#a-结构视图怎样共享事实)（L481）。

来源（链接中保留物理页码和条件）：[11A·2](lessons/11A.md#r2)。

<a id="d041"></a>

## D041 Gap Open Bar 的趋势组合及市场适用权重

**部分吸收。** 单棒 open 相对前 close 的 gap 已定义；连续 Gap Open Bars 的顺向强度线索及外汇报价适用权重未完整列出。

系统定位：[market F. Gap：分离事实、直接引用与后续结果](../../trading_system/market.md#f-gap分离事实直接引用与后续结果)（L640）；[market 当前运动的强弱](../../trading_system/market.md#当前运动的强弱)（L227）。

来源（链接中保留物理页码和条件）：[11C·2](lessons/11C.md#r2)。

<a id="d042"></a>

## D042 Stairs 的缺口重叠定义及逆势可获利诊断

**部分吸收。** Stairs 有重叠/回撤概括，但突破点与后续 PB 重叠、增量缩小，以及逆势 Limit/Stop 盈利作为变宽诊断的具体关系未全部保留。

系统定位：[market F. Gap：分离事实、直接引用与后续结果](../../trading_system/market.md#f-gap分离事实直接引用与后续结果)（L640）；[scenarios 通道突破的方向与目标](../../trading_system/scenarios.md#通道突破的方向与目标)（L134）。

来源（链接中保留物理页码和条件）：[11D·3](lessons/11D.md#r3)、[11D·4](lessons/11D.md#r4)、[12A·5](lessons/12A.md#r5)、[14D·3](lessons/14D.md#r3)、[14D·6](lessons/14D.md#r6)、[16E·1](lessons/16E.md#r1)、[18C·3](lessons/18C.md#r3)、[18C·5](lessons/18C.md#r5)、[24A·2](lessons/24A.md#r2)、[24C·1](lessons/24C.md#r1)、[24D·3](lessons/24D.md#r3)、[31C·1](lessons/31C.md#r1)、[33F·1](lessons/33F.md#r1)、[37B·1](lessons/37B.md#r1)、[41B·2](lessons/41B.md#r2)、[42A·1](lessons/42A.md#r1)、[43B·2](lessons/43B.md#r2)、[44B·2](lessons/44B.md#r2)、[45A·2](lessons/45A.md#r2)、[45D·2](lessons/45D.md#r2)、[46D·2](lessons/46D.md#r2)、[47B·1](lessons/47B.md#r1)、[48G·2](lessons/48G.md#r2)、[49D·1](lessons/49D.md#r1)、[50A·2](lessons/50A.md#r2)。

<a id="d043"></a>

## D043 短区间继承方向、长区间逐渐中性的时间关系

**部分吸收。** 成熟区间可重置旧趋势已有；短区间继承方向、约 20 棒乃至更久逐渐中性等时间衰减关系未完整表达，具体时间不是硬阈值。

系统定位：[market 3.4 市场结构与持续能力](../../trading_system/market.md#34-市场结构与持续能力)（L111）；[scenarios 五、价格到达区间或宽通道边缘](../../trading_system/scenarios.md#五价格到达区间或宽通道边缘)（L96）。

来源（链接中保留物理页码和条件）：[12B·2](lessons/12B.md#r2)、[12C·2](lessons/12C.md#r2)、[14B·1](lessons/14B.md#r1)、[15F·3](lessons/15F.md#r3)、[18A·2](lessons/18A.md#r2)、[18D·1](lessons/18D.md#r1)、[20A·3](lessons/20A.md#r3)、[21A·4](lessons/21A.md#r4)、[22C·3](lessons/22C.md#r3)、[26A·2](lessons/26A.md#r2)、[27B·2](lessons/27B.md#r2)、[28·1](lessons/28.md#r1)、[30B·3](lessons/30B.md#r3)、[33D·2](lessons/33D.md#r2)、[43D·3](lessons/43D.md#r3)、[48G·1](lessons/48G.md#r1)。

<a id="d044"></a>

## D044 广义回调可始于最终极值之前及破坏趋势后的相对命名

**定义/口径差异。** 来源相对旧运动命名的 PB/新通道可以始于旧最终极值之前，甚至沿用在旧趋势已破坏后；系统主要按当前运动与首次有意义回调组织，未保留所有广义命名。

系统定位：[market E. K 线与运动事实](../../trading_system/market.md#e-k-线与运动事实)（L598）；[scenarios 通道突破的方向与目标](../../trading_system/scenarios.md#通道突破的方向与目标)（L134）。

来源（链接中保留物理页码和条件）：[12C·1](lessons/12C.md#r1)、[16C·1](lessons/16C.md#r1)、[24C·3](lessons/24C.md#r3)、[40E·4](lessons/40E.md#r4)。

<a id="d045"></a>

## D045 弱通道至少部分 scalp 与状态限定的管理默认

**方法取舍。** 来源按状态设置弱通道/区间及逆势偏 scalp、强趋势偏 Swing、部分仓位长持的默认；系统逐案比较。宽通道和 TR 本身也可有 10–20 棒局部 Swing，不能统一压成只准 scalp。

系统定位：[trade 3.1 从条件路径开始](../../trading_system/trade.md#31-从条件路径开始)（L33）；[scenarios 五、价格到达区间或宽通道边缘](../../trading_system/scenarios.md#五价格到达区间或宽通道边缘)（L96）；[scenarios 通道突破的方向与目标](../../trading_system/scenarios.md#通道突破的方向与目标)（L134）。

来源（链接中保留物理页码和条件）：[12C·4](lessons/12C.md#r4)、[14D·4](lessons/14D.md#r4)、[14E·5](lessons/14E.md#r5)、[16B·4](lessons/16B.md#r4)、[16D·4](lessons/16D.md#r4)、[16E·1](lessons/16E.md#r1)、[16F·5](lessons/16F.md#r5)、[18B·2](lessons/18B.md#r2)、[18C·3](lessons/18C.md#r3)、[18C·5](lessons/18C.md#r5)、[18F·1](lessons/18F.md#r1)、[19E·5](lessons/19E.md#r5)、[21A·2](lessons/21A.md#r2)、[22A·2](lessons/22A.md#r2)、[23B·1](lessons/23B.md#r1)、[24B·4](lessons/24B.md#r4)、[25A·3](lessons/25A.md#r3)、[27A·3](lessons/27A.md#r3)、[30A·1](lessons/30A.md#r1)、[30E·6](lessons/30E.md#r6)、[31B·2](lessons/31B.md#r2)、[31C·5](lessons/31C.md#r5)、[32C·2](lessons/32C.md#r2)、[37A·1](lessons/37A.md#r1)、[37B·1](lessons/37B.md#r1)、[37B·3](lessons/37B.md#r3)、[41A·3](lessons/41A.md#r3)、[41C·1](lessons/41C.md#r1)、[41D·2](lessons/41D.md#r2)、[42A·1](lessons/42A.md#r1)、[42C·1](lessons/42C.md#r1)、[43B·1](lessons/43B.md#r1)、[43B·2](lessons/43B.md#r2)、[44B·2](lessons/44B.md#r2)、[45A·1](lessons/45A.md#r1)、[45B·2](lessons/45B.md#r2)、[45D·4](lessons/45D.md#r4)、[46A·1](lessons/46A.md#r1)、[46A·3](lessons/46A.md#r3)、[46C·1](lessons/46C.md#r1)、[47A·1](lessons/47A.md#r1)、[47D·1](lessons/47D.md#r1)、[48C·3](lessons/48C.md#r3)、[48H·3](lessons/48H.md#r3)、[49A·2](lessons/49A.md#r2)、[49B·2](lessons/49B.md#r2)、[49E·1](lessons/49E.md#r1)、[50A·1](lessons/50A.md#r1)、[50C·3](lessons/50C.md#r3)、[50D·1](lessons/50D.md#r1)、[50E·1](lessons/50E.md#r1)。

<a id="d046"></a>

## D046 能否可靠重入决定穿越回调持有或止盈重入

**部分吸收。** 退出重入与整段成本已有；来源把能否可靠及时重入作为选择穿越 PB 持有还是退出的个人能力条件，系统未明确这一选择因素。

系统定位：[trade 3.5 出场、目标与期限](../../trading_system/trade.md#35-出场目标与期限)（L109）；[governance 连续过程与经济表现](../../trading_system/governance.md#连续过程与经济表现)（L55）；[Practice 晋级与退回](../../practice/README.md#晋级与退回)（L245）。

来源（链接中保留物理页码和条件）：[13B·4](lessons/13B.md#r4)、[30E·5](lessons/30E.md#r5)、[31A·2](lessons/31A.md#r2)、[31D·3](lessons/31D.md#r3)、[33B·3](lessons/33B.md#r3)、[37B·3](lessons/37B.md#r3)、[39D·1](lessons/39D.md#r1)、[45D·1](lessons/45D.md#r1)、[46C·3](lessons/46C.md#r3)、[48H·2](lessons/48H.md#r2)。

<a id="d047"></a>

## D047 Always In 不清时回看最近未被反转的主导突破

**部分吸收。** 当前不清时保留分歧；没有 Always In 不清便回看最近未被明确反转的强主导突破这一具体恢复方向判断方法。

系统定位：[market 3.4 市场结构与持续能力](../../trading_system/market.md#34-市场结构与持续能力)（L111）。

来源（链接中保留物理页码和条件）：[13A·3](lessons/13A.md#r3)。

<a id="d048"></a>

## D048 从通道外侧两点反向平移构造趋势线的取点约束

**部分吸收。** 当前允许平行复制或另一侧两点连线；未明确先取外侧两极值、再平移到对侧拐点的反向构造及取点约束。

系统定位：[market G. 趋势线与通道线](../../trading_system/market.md#g-趋势线与通道线)（L669）。

来源（链接中保留物理页码和条件）：[14A·5](lessons/14A.md#r5)、[16A·2](lessons/16A.md#r2)、[16B·1](lessons/16B.md#r1)、[19B·4](lessons/19B.md#r4)、[40E·4](lessons/40E.md#r4)。

<a id="d049"></a>

## D049 TFO 的开局极值含义、连续市场命名与后续分支

**部分吸收。** 来源 Trend From Open 把开局/早期日极值与趋势关系联系，首 Swing 可事后 5–20 棒才清楚；系统只有一般 Session 背景，缺具名条件及连续市场限定。

系统定位：[scenarios 固定 Session 中的背景与等待](../../trading_system/scenarios.md#固定-session-中的背景与等待)（L33）；[scenarios 通道突破的方向与目标](../../trading_system/scenarios.md#通道突破的方向与目标)（L134）。

来源（链接中保留物理页码和条件）：[14C·3](lessons/14C.md#r3)、[14D·1](lessons/14D.md#r1)、[48A·1](lessons/48A.md#r1)、[48A·2](lessons/48A.md#r2)、[48B·1](lessons/48B.md#r1)、[48E·1](lessons/48E.md#r1)、[49B·3](lessons/49B.md#r3)。

<a id="d050"></a>

## D050 Trending TR 的新区间序列、重叠和回上一区间预期

**部分吸收。** 已有 Trending TR 名称与双向空间；新公平区经短突破迁移、回测并与前一区间重叠的序列预期未完整保留。

系统定位：[scenarios 通道突破的方向与目标](../../trading_system/scenarios.md#通道突破的方向与目标)（L134）；[scenarios 五、价格到达区间或宽通道边缘](../../trading_system/scenarios.md#五价格到达区间或宽通道边缘)（L96）。

来源（链接中保留物理页码和条件）：[14D·2](lessons/14D.md#r2)、[41C·1](lessons/41C.md#r1)、[42A·1](lessons/42A.md#r1)、[45A·2](lessons/45A.md#r2)、[46A·1](lessons/46A.md#r1)。

<a id="d051"></a>

## D051 宽通道前段中间三分之一入场及加仓后的退出关系

**部分吸收。** 系统有三分之一区域，但来源还有上一段中间三分之一、半程、底部两分之三/顶区等不同参与区域；区间和最后趋势段分母不能交换，原课亦有文字冲突。

系统定位：[market 从哪些锚点投射候选区域](../../trading_system/market.md#从哪些锚点投射候选区域)（L519）；[scenarios 五、价格到达区间或宽通道边缘](../../trading_system/scenarios.md#五价格到达区间或宽通道边缘)（L96）。

来源（链接中保留物理页码和条件）：[14D·5](lessons/14D.md#r5)、[31C·1](lessons/31C.md#r1)、[37B·2](lessons/37B.md#r2)、[45B·2](lessons/45B.md#r2)、[45E·1](lessons/45E.md#r1)、[46B·1](lessons/46B.md#r1)、[46E·1](lessons/46E.md#r1)、[47A·1](lessons/47A.md#r1)、[47B·3](lessons/47B.md#r3)、[47D·3](lessons/47D.md#r3)、[48G·3](lessons/48G.md#r3)。

<a id="d052"></a>

## D052 小回调趋势时段末较大回调、通常恢复及少见反转

**部分吸收。** 普通小回调趋势已有；持续两小时后后段出现较大 PB 通常先为旗形/恢复、少数反转的时段模板未列明。

系统定位：[market 回撤与恢复怎样改变原判断](../../trading_system/market.md#回撤与恢复怎样改变原判断)（L273）；[scenarios 固定 Session 中的背景与等待](../../trading_system/scenarios.md#固定-session-中的背景与等待)（L33）。

来源（链接中保留物理页码和条件）：[14E·4](lessons/14E.md#r4)。

<a id="d053"></a>

## D053 无需说清突破对象的微观教学用法与系统明确锚点要求

**定义/口径差异。** 课程把每根趋势棒/每次微小越界也称 BO、可不强调对象；系统要求明确被越过的参照，最低命名范围不同。

系统定位：[market E. K 线与运动事实](../../trading_system/market.md#e-k-线与运动事实)（L598）；[market 边界处是否改变此前作用](../../trading_system/market.md#边界处是否改变此前作用)（L292）。

来源（链接中保留物理页码和条件）：[15A·1](lessons/15A.md#r1)、[21A·3](lessons/21A.md#r3)、[29A·1](lessons/29A.md#r1)。

<a id="d054"></a>

## D054 强区间突破确认后停止逆向交易多棒的等待要求

**部分吸收。** 强 BO 后更新旧边缘预期已有；没有明确停止旧侧淡化数棒、等待新反向依据的教学管理默认，不能继续套普通 TR 首破失败先验。

系统定位：[market 边界处是否改变此前作用](../../trading_system/market.md#边界处是否改变此前作用)（L292）；[trade 3.2 确认程度与订单条件](../../trading_system/trade.md#32-确认程度与订单条件)（L58）。

来源（链接中保留物理页码和条件）：[15C·4](lessons/15C.md#r4)、[30E·6](lessons/30E.md#r6)、[38B·1](lessons/38B.md#r1)、[40C·1](lessons/40C.md#r1)。

<a id="d055"></a>

## D055 Surprise 的事前低概率与确认后重新定价关系

**部分吸收。** 已保留预期差及更新；Surprise 还包含事前低预期、意外强 BO 后立即弃旧先验重新定价的特定解释，未完整命名。

系统定位：[market 由表现更新预期](../../trading_system/market.md#由表现更新预期)（L321）；[market 边界处是否改变此前作用](../../trading_system/market.md#边界处是否改变此前作用)（L292）。

来源（链接中保留物理页码和条件）：[15C·1](lessons/15C.md#r1)、[16E·5](lessons/16E.md#r5)、[24E·1](lessons/24E.md#r1)、[29D·2](lessons/29D.md#r2)。

<a id="d056"></a>

## D056 形成中突破棒的停留位置与单次/重复回撤轨迹

**未具体吸收。** 允许事先约定盘中事件已有；课程形成中大棒在末段停留、回撤 1/4、1/3、2/3 及反复回吐轨迹的判断配方没有表达。

系统定位：[market 3.2 观察边界与多周期](../../trading_system/market.md#32-观察边界与多周期)（L80）；[market 当前运动的强弱](../../trading_system/market.md#当前运动的强弱)（L227）。

来源（链接中保留物理页码和条件）：[15D·4](lessons/15D.md#r4)、[32A·5](lessons/32A.md#r5)、[32B·2](lessons/32B.md#r2)、[32C·3](lessons/32C.md#r3)。

<a id="d057"></a>

## D057 极端相对成交量强化跟随与测量预期

**部分吸收。** 成交量辅助已有；异常相对量约 10–20 倍配 BO/FT 支持 MM 的特定组合未采用，数字无样本校准。

系统定位：[market 3.1 事实、关系与判断](../../trading_system/market.md#31-事实关系与判断)（L47）；[market 当前运动的强弱](../../trading_system/market.md#当前运动的强弱)（L227）。

来源（链接中保留物理页码和条件）：[15D·5](lessons/15D.md#r5)。

<a id="d058"></a>

## D058 首次回调时点、入场保本价测试与突破强弱

**部分吸收。** 回试守住及强弱 PB 已有；首次 PB 何时发生、是否先给原价 BE、这些怎样区分强弱突破的具体链未完整列出。

系统定位：[market 回撤与恢复怎样改变原判断](../../trading_system/market.md#回撤与恢复怎样改变原判断)（L273）；[market 边界处是否改变此前作用](../../trading_system/market.md#边界处是否改变此前作用)（L292）。

来源（链接中保留物理页码和条件）：[15D·7](lessons/15D.md#r7)。

<a id="d059"></a>

## D059 Micro gap 可接触不重叠与正宽度 gap 的边界

**定义/口径差异。** 来源某 micro gap 定义允许恰好相接而不重叠；系统正 gap 需保留空间，零宽度临界未明确。不能把接触、正空白、负重叠三者混同。

系统定位：[market F. Gap：分离事实、直接引用与后续结果](../../trading_system/market.md#f-gap分离事实直接引用与后续结果)（L640）。

来源（链接中保留物理页码和条件）：[15D·6](lessons/15D.md#r6)。

<a id="d060"></a>

## D060 末段衰竭高潮后通常先双顶/微双顶再反转

**部分吸收。** 当前高潮与修正分支已有；末段衰竭后通常先 DT/微 DT 再真正反转的中间路径未明确，不能直接认定高潮即顶。

系统定位：[scenarios 七、趋势异常加速或持续过久](../../trading_system/scenarios.md#七趋势异常加速或持续过久)（L122）；[scenarios 八、趋势受损后尝试反转](../../trading_system/scenarios.md#八趋势受损后尝试反转)（L157）。

来源（链接中保留物理页码和条件）：[15E·2](lessons/15E.md#r2)、[33D·2](lessons/33D.md#r2)。

<a id="d061"></a>

## D061 固定 scalp 目标陷阱、提前一跳退出及弱 setup 反做分批方案

**部分吸收。** 来源固定 scalp 目标差一跳、走够多两跳才常可填、早退、弱 setup 反做及分层有完整案例链；系统只覆盖成本/成交/目标通则，未保留具体配方。

系统定位：[market 3.5 重要区域图与路径作用](../../trading_system/market.md#35-重要区域图与路径作用)（L178）；[trade 3.2 确认程度与订单条件](../../trading_system/trade.md#32-确认程度与订单条件)（L58）；[trade 3.5 出场、目标与期限](../../trading_system/trade.md#35-出场目标与期限)（L109）。

来源（链接中保留物理页码和条件）：[15G·1](lessons/15G.md#r1)、[15G·2](lessons/15G.md#r2)、[15G·4](lessons/15G.md#r4)、[15G·5](lessons/15G.md#r5)、[19E·4](lessons/19E.md#r4)、[40D·1](lessons/40D.md#r1)、[40D·2](lessons/40D.md#r2)。

<a id="d062"></a>

## D062 趋势线三点的时间对称、独立性与超时失去相关性

**部分吸收。** 当前按反应/强越界保留与重画；三点相邻间隔约 3–5 倍、第三点太近并非独立测试、过久未测相关性降低的画线启发未列明。

系统定位：[market G. 趋势线与通道线](../../trading_system/market.md#g-趋势线与通道线)（L669）。

来源（链接中保留物理页码和条件）：[16A·4](lessons/16A.md#r4)、[16B·1](lessons/16B.md#r1)。

<a id="d063"></a>

## D063 Nested wedge 的大第三段内小楔形与衰减证据

**部分吸收。** 已有同源结构共享；外层大第三推动内部再现小楔形、HS 各组件/ET 中嵌套的几何与次序增量未完整定义。

系统定位：[market A. 结构视图怎样共享事实](../../trading_system/market.md#a-结构视图怎样共享事实)（L481）；[scenarios 八、趋势受损后尝试反转](../../trading_system/scenarios.md#八趋势受损后尝试反转)（L157）。

来源（链接中保留物理页码和条件）：[16B·2](lessons/16B.md#r2)、[21C·3](lessons/21C.md#r3)、[22D·2](lessons/22D.md#r2)、[22D·3](lessons/22D.md#r3)、[24A·2](lessons/24A.md#r2)、[24C·3](lessons/24C.md#r3)、[26B·2](lessons/26B.md#r2)、[27A·3](lessons/27A.md#r3)、[31A·2](lessons/31A.md#r2)、[33A·4](lessons/33A.md#r4)、[38B·1](lessons/38B.md#r1)、[40E·3](lessons/40E.md#r3)。

<a id="d064"></a>

## D064 通道对侧最低目标需越线一 tick/pip 的设定

**定义/口径差异。** 通道对侧目标已有，但来源最低目标要求越对侧至少一 tick/pip；系统由预先完成条件确定触及/穿越/接受，没有这个默认偏移。

系统定位：[scenarios 通道突破的方向与目标](../../trading_system/scenarios.md#通道突破的方向与目标)（L134）；[market 从哪些锚点投射候选区域](../../trading_system/market.md#从哪些锚点投射候选区域)（L519）。

来源（链接中保留物理页码和条件）：[16F·4](lessons/16F.md#r4)、[26B·3](lessons/26B.md#r3)、[40E·3](lessons/40E.md#r3)。

<a id="d065"></a>

## D065 Micro Channel 相邻极值、起始基点与结束棒的严格定义

**部分吸收。** 当前使用 Microchannel 但缺严格连续相邻低点不降低/高点不升高、起始基点和终止棒规则；公开 glossary 又允许零或一两次小回调，应保留两种语境。

系统定位：[market E. K 线与运动事实](../../trading_system/market.md#e-k-线与运动事实)（L598）；[scenarios 通道突破的方向与目标](../../trading_system/scenarios.md#通道突破的方向与目标)（L134）。

来源（链接中保留物理页码和条件）：[17A·3](lessons/17A.md#r3)、[17B·2](lessons/17B.md#r2)、[24D·2](lessons/24D.md#r2)、[29C·1](lessons/29C.md#r1)、[29E·4](lessons/29E.md#r4)、[33C·2](lessons/33C.md#r2)、[38A·3](lessons/38A.md#r3)、[42B·2](lessons/42B.md#r2)、[来源台账：micro channel 可零或一两次小回调](../../reference/official_sources.md#来源锚点定位)。

<a id="d066"></a>

## D066 紧通道与 TTR 相对平均棒、最小 scalp 的两种空间门槛

**未具体吸收。** 紧通道 PB 相对约两根平均棒/2–3 最小 scalp、TTR 高度以平均棒或最小 scalp 判断的阈值未采用；来源 OR/AND 和品种例外不可合成一个判式。

系统定位：[market 3.4 市场结构与持续能力](../../trading_system/market.md#34-市场结构与持续能力)（L111）；[scenarios 五、价格到达区间或宽通道边缘](../../trading_system/scenarios.md#五价格到达区间或宽通道边缘)（L96）。

来源（链接中保留物理页码和条件）：[17A·2](lessons/17A.md#r2)、[17B·1](lessons/17B.md#r1)、[18D·4](lessons/18D.md#r4)、[43A·1](lessons/43A.md#r1)、[44A·1](lessons/44A.md#r1)、[47D·3](lessons/47D.md#r3)。

<a id="d067"></a>

## D067 Micro trend line 有用而对侧微通道线可省略

**未具体吸收。** 来源建议微趋势线可用、对侧微通道线通常无须画；系统只有一般线条取舍，没有这一微尺度优先级。

系统定位：[market G. 趋势线与通道线](../../trading_system/market.md#g-趋势线与通道线)（L669）。

来源（链接中保留物理页码和条件）：[17B·2](lessons/17B.md#r2)。

<a id="d068"></a>

## D068 晚期高潮微通道首次反破后暂停原方向并观察

**部分吸收。** 晚期微通道反破可扩大修正已有；首反破后暂停原方向约 5–10 棒再观察的特定等待建议未列入。

系统定位：[market 回撤与恢复怎样改变原判断](../../trading_system/market.md#回撤与恢复怎样改变原判断)（L273）；[scenarios 七、趋势异常加速或持续过久](../../trading_system/scenarios.md#七趋势异常加速或持续过久)（L122）。

来源（链接中保留物理页码和条件）：[17B·6](lessons/17B.md#r6)、[42B·2](lessons/42B.md#r2)。

<a id="d069"></a>

## D069 长紧通道高潮后至少二十棒两段修正的特定预期

**未具体吸收。** 特定长紧通道/连续高潮后约 70% 至少二十棒两腿修正，不是普通十棒 TBTL；系统没有保留这项较长尺度模板。

系统定位：[scenarios 七、趋势异常加速或持续过久](../../trading_system/scenarios.md#七趋势异常加速或持续过久)（L122）；[market TBTL 与运动尺度](../../trading_system/market.md#tbtl-与运动尺度)（L259）。

来源（链接中保留物理页码和条件）：[18C·6](lessons/18C.md#r6)、[29E·3](lessons/29E.md#r3)、[42B·2](lessons/42B.md#r2)。

<a id="d070"></a>

## D070 LOM 的限价可行而突破单无空间及普通人避开的默认

**部分吸收。** 双向空间与窄区间等待已有；LOM 中 Limit 可赚而追突破不能赚、多数人暂避的具体默认未完整保留。部分课程也允许强段 Stop，不能写绝对禁令。

系统定位：[scenarios 五、价格到达区间或宽通道边缘](../../trading_system/scenarios.md#五价格到达区间或宽通道边缘)（L96）；[trade 3.2 确认程度与订单条件](../../trading_system/trade.md#32-确认程度与订单条件)（L58）；[Practice 晋级与退回](../../practice/README.md#晋级与退回)（L245）。

来源（链接中保留物理页码和条件）：[18D·3](lessons/18D.md#r3)、[18F·3](lessons/18F.md#r3)、[32B·4](lessons/32B.md#r4)、[32C·1](lessons/32C.md#r1)、[37B·1](lessons/37B.md#r1)、[43C·1](lessons/43C.md#r1)、[44C·1](lessons/44C.md#r1)、[47A·1](lessons/47A.md#r1)、[47B·3](lessons/47B.md#r3)、[47D·3](lessons/47D.md#r3)、[48B·2](lessons/48B.md#r2)、[48G·3](lessons/48G.md#r3)、[48I·2](lessons/48I.md#r2)、[49A·3](lessons/49A.md#r3)、[49B·1](lessons/49B.md#r1)、[49E·1](lessons/49E.md#r1)、[50A·1](lessons/50A.md#r1)。

<a id="d071"></a>

## D071 紧区间大部分位于 EMA 一侧的轻微突破方向偏向

**未具体吸收。** 紧区间多数棒位于 EMA 一侧时有轻微该方向突破偏置，当前一般 EMA 参照没有包含这一条件经验。

系统定位：[scenarios 五、价格到达区间或宽通道边缘](../../trading_system/scenarios.md#五价格到达区间或宽通道边缘)（L96）；[market 3.5 重要区域图与路径作用](../../trading_system/market.md#35-重要区域图与路径作用)（L178）。

来源（链接中保留物理页码和条件）：[18D·5](lessons/18D.md#r5)。

<a id="d072"></a>

## D072 早盘区间日的组合线索、各自观察窗口及延续时长

**部分吸收。** 早盘重叠、doji、反转次数、均线平、无 gap、昨日 TR 的组合及前 5–10 棒/1–2 小时、后 2–3 小时预期未完整列出。

系统定位：[scenarios 固定 Session 中的背景与等待](../../trading_system/scenarios.md#固定-session-中的背景与等待)（L33）；[scenarios 五、价格到达区间或宽通道边缘](../../trading_system/scenarios.md#五价格到达区间或宽通道边缘)（L96）。

来源（链接中保留物理页码和条件）：[18F·3](lessons/18F.md#r3)。

<a id="d073"></a>

## D073 区间日末三分之一回测中部及两种收盘分支

**未具体吸收。** TR 日最后三分之一常测试中部，开盘在中间三分之一尤其相关；可收近开盘 doji，也可到极值趋势收盘。系统未保留这条时序，开盘与中点不严格相等。

系统定位：[scenarios 固定 Session 中的背景与等待](../../trading_system/scenarios.md#固定-session-中的背景与等待)（L33）；[market 3.5 重要区域图与路径作用](../../trading_system/market.md#35-重要区域图与路径作用)（L178）。

来源（链接中保留物理页码和条件）：[18F·4](lessons/18F.md#r4)、[47D·2](lessons/47D.md#r2)、[48C·1](lessons/48C.md#r1)、[48H·1](lessons/48H.md#r1)、[48H·2](lessons/48H.md#r2)、[48K·1](lessons/48K.md#r1)。

<a id="d074"></a>

## D074 支撑阻力候选清单中的信号/入场棒、收盘极值、scalp目标及Daily pivots

**部分吸收。** 通用 OHLC/SR 已有；信号/入场棒端点、最高最低趋势收盘、scalp 目标、Daily pivots 等具名参照未全部列明，列出候选不等于授权。

系统定位：[market 3.5 重要区域图与路径作用](../../trading_system/market.md#35-重要区域图与路径作用)（L178）。

来源（链接中保留物理页码和条件）：[19C·4](lessons/19C.md#r4)、[19D·2](lessons/19D.md#r2)、[19D·4](lessons/19D.md#r4)、[19E·2](lessons/19E.md#r2)、[19E·4](lessons/19E.md#r4)、[40A·1](lessons/40A.md#r1)、[40B·1](lessons/40B.md#r1)、[45D·1](lessons/45D.md#r1)、[46D·1](lessons/46D.md#r1)、[46D·2](lessons/46D.md#r2)、[48K·2](lessons/48K.md#r2)、[49A·4](lessons/49A.md#r4)、[49C·3](lessons/49C.md#r3)、[49E·2](lessons/49E.md#r2)。

<a id="d075"></a>

## D075 月末年末对高周期开收及上期极值的特别关注

**部分吸收。** 重要开高低收已有；周/月/年结束前对本期开盘、前期收盘和高低点、两周高点等的关注时点未完整保留。

系统定位：[market 3.5 重要区域图与路径作用](../../trading_system/market.md#35-重要区域图与路径作用)（L178）；[scenarios 固定 Session 中的背景与等待](../../trading_system/scenarios.md#固定-session-中的背景与等待)（L33）。

来源（链接中保留物理页码和条件）：[19C·1](lessons/19C.md#r1)、[48K·2](lessons/48K.md#r2)。

<a id="d076"></a>

## D076 收盘追随失望后分批回原价退出及最高最低收盘的角色切换

**部分吸收。** 一般分批及加权成本已有；首价首仓 BE/低仓获利、均价组合 BE、缩目标减损、恢复 Swing 等具体分支没有作为默认模板。数量未知的图不能假定等量净盈利。

系统定位：[trade 3.5 出场、目标与期限](../../trading_system/trade.md#35-出场目标与期限)（L109）；[trade 四、加仓与分层](../../trading_system/trade.md#四加仓与分层)（L214）。

来源（链接中保留物理页码和条件）：[19C·4](lessons/19C.md#r4)、[19D·1](lessons/19D.md#r1)、[19D·2](lessons/19D.md#r2)、[19E·1](lessons/19E.md#r1)、[23B·2](lessons/23B.md#r2)、[25A·2](lessons/25A.md#r2)、[30B·2](lessons/30B.md#r2)、[31D·2](lessons/31D.md#r2)、[33C·2](lessons/33C.md#r2)、[33D·3](lessons/33D.md#r3)、[33D·4](lessons/33D.md#r4)、[33G·5](lessons/33G.md#r5)、[34A·3](lessons/34A.md#r3)、[35A·1](lessons/35A.md#r1)、[35A·4](lessons/35A.md#r4)、[35B·3](lessons/35B.md#r3)、[35C·2](lessons/35C.md#r2)、[35C·4](lessons/35C.md#r4)、[37A·2](lessons/37A.md#r2)、[37B·1](lessons/37B.md#r1)、[39C·1](lessons/39C.md#r1)、[39C·2](lessons/39C.md#r2)、[40A·1](lessons/40A.md#r1)、[40A·3](lessons/40A.md#r3)、[40B·2](lessons/40B.md#r2)、[40B·3](lessons/40B.md#r3)、[40C·2](lessons/40C.md#r2)、[40D·1](lessons/40D.md#r1)、[40D·3](lessons/40D.md#r3)、[41B·1](lessons/41B.md#r1)、[41C·2](lessons/41C.md#r2)、[42A·1](lessons/42A.md#r1)、[42A·3](lessons/42A.md#r3)、[43A·3](lessons/43A.md#r3)、[43B·1](lessons/43B.md#r1)、[43C·2](lessons/43C.md#r2)、[43D·1](lessons/43D.md#r1)、[44A·3](lessons/44A.md#r3)、[44B·1](lessons/44B.md#r1)、[44C·2](lessons/44C.md#r2)、[44D·1](lessons/44D.md#r1)、[45C·3](lessons/45C.md#r3)、[45D·3](lessons/45D.md#r3)、[45E·1](lessons/45E.md#r1)、[46C·1](lessons/46C.md#r1)、[46D·3](lessons/46D.md#r3)、[47A·2](lessons/47A.md#r2)、[47B·1](lessons/47B.md#r1)、[47C·3](lessons/47C.md#r3)、[47D·1](lessons/47D.md#r1)、[47D·2](lessons/47D.md#r2)、[49A·3](lessons/49A.md#r3)、[49C·1](lessons/49C.md#r1)、[49C·2](lessons/49C.md#r2)、[49C·3](lessons/49C.md#r3)、[49D·1](lessons/49D.md#r1)、[49E·1](lessons/49E.md#r1)、[49E·3](lessons/49E.md#r3)、[50A·2](lessons/50A.md#r2)、[50B·1](lessons/50B.md#r1)、[50C·2](lessons/50C.md#r2)、[50D·4](lessons/50D.md#r4)、[50E·2](lessons/50E.md#r2)、[50E·4](lessons/50E.md#r4)、[51A·3](lessons/51A.md#r3)、[51B·1](lessons/51B.md#r1)、[52A·4](lessons/52A.md#r4)、[52B·1](lessons/52B.md#r1)。

<a id="d077"></a>

## D077 越过晚期高潮棒边界即趋势结束与系统主要结构接受判据

**定义/口径差异。** 课程有越过晚期高潮棒端点即称趋势结束的宽泛口径；系统分开局部段结束、主要结构接受和持续控制，不能用该端点自动确认反向趋势。

系统定位：[market 3.4 市场结构与持续能力](../../trading_system/market.md#34-市场结构与持续能力)（L111）；[scenarios 七、趋势异常加速或持续过久](../../trading_system/scenarios.md#七趋势异常加速或持续过久)（L122）。

来源（链接中保留物理页码和条件）：[19E·5](lessons/19E.md#r5)、[21B·2](lessons/21B.md#r2)、[25B·2](lessons/25B.md#r2)、[30B·4](lessons/30B.md#r4)。

<a id="d078"></a>

## D078 深回调后等距最低目标及弱通道第二段结束倾向

**未具体吸收。** 深 PB 后 Leg1=Leg2 作为最低目标及弱通道第二段易终止的条件预期未完整采用；系统允许第二段短、横向或失败，目标仍需自身依据。

系统定位：[market 第二段预期与分段尺度](../../trading_system/market.md#第二段预期与分段尺度)（L246）；[market 从哪些锚点投射候选区域](../../trading_system/market.md#从哪些锚点投射候选区域)（L519）。

来源（链接中保留物理页码和条件）：[20A·1](lessons/20A.md#r1)。

<a id="d079"></a>

## D079 突破起点优先与区间起止分隔趋势两段的具体选点

**部分吸收。** 投射锚点固定已有；课程从明显 BO 起点而非绝对极值起算，以及 TR 首末段分隔两腿的具体选点启发未全部写入。

系统定位：[market 从哪些锚点投射候选区域](../../trading_system/market.md#从哪些锚点投射候选区域)（L519）；[market 第二段预期与分段尺度](../../trading_system/market.md#第二段预期与分段尺度)（L246）。

来源（链接中保留物理页码和条件）：[20A·2](lessons/20A.md#r2)、[20A·3](lessons/20A.md#r3)、[20B·1](lessons/20B.md#r1)。

<a id="d080"></a>

## D080 以区间中点为对称中心的测量及较低权重

**未具体吸收。** 区间中点 M 相对原运动起点 S 投射 2M−S 的方法及较低权重未定义；普通区间高度从边界外延不等于此式。

系统定位：[market 从哪些锚点投射候选区域](../../trading_system/market.md#从哪些锚点投射候选区域)（L519）。

来源（链接中保留物理页码和条件）：[20B·1](lessons/20B.md#r1)。

<a id="d081"></a>

## D081 反转/MTR 的广义状态命名及先按次要、反向破线持续十棒的默认

**定义/口径差异。** 来源 reversal/MTR 有趋势变 TR、初次反转和完整逆向趋势等广义用法；系统细分阶段。持续约十棒反向破线的教学前提也未作默认。

系统定位：[scenarios 八、趋势受损后尝试反转](../../trading_system/scenarios.md#八趋势受损后尝试反转)（L157）；[market 3.4 市场结构与持续能力](../../trading_system/market.md#34-市场结构与持续能力)（L111）。

来源（链接中保留物理页码和条件）：[21A·1](lessons/21A.md#r1)、[21A·2](lessons/21A.md#r2)、[21C·2](lessons/21C.md#r2)、[22A·3](lessons/22A.md#r3)、[27A·1](lessons/27A.md#r1)、[38D·2](lessons/38D.md#r2)、[39A·2](lessons/39A.md#r2)、[39D·3](lessons/39D.md#r3)。

<a id="d082"></a>

## D082 杯柄、圆弧顶底等别名与已有反转/旗形过程的映射

**仅别名或资料。** 杯柄、圆弧/碟形等名称未收录，但可归入已有旗形、双测试和反转过程；未发现这些别名本身新增独立交易逻辑。

系统定位：[market A. 结构视图怎样共享事实](../../trading_system/market.md#a-结构视图怎样共享事实)（L481）；[scenarios 八、趋势受损后尝试反转](../../trading_system/scenarios.md#八趋势受损后尝试反转)（L157）。

来源（链接中保留物理页码和条件）：[21B·4](lessons/21B.md#r4)、[21D·5](lessons/21D.md#r5)、[28·1](lessons/28.md#r1)。

<a id="d083"></a>

## D083 主要反转压力所需极大棒、较小棒与普通棒的经验尺度

**未具体吸收。** MTR 压力约 5 强棒/10 普通棒、2–3 极大棒等强度—持续时间配方未采用。开盘可 1–5、极强一棒等例外分开，系统不统一等固定棒数。

系统定位：[scenarios 八、趋势受损后尝试反转](../../trading_system/scenarios.md#八趋势受损后尝试反转)（L157）；[market 当前运动的强弱](../../trading_system/market.md#当前运动的强弱)（L227）。

来源（链接中保留物理页码和条件）：[21C·2](lessons/21C.md#r2)、[22A·2](lessons/22A.md#r2)、[22C·3](lessons/22C.md#r3)、[22D·1](lessons/22D.md#r1)、[24D·2](lessons/24D.md#r2)、[25B·4](lessons/25B.md#r4)、[26A·4](lessons/26A.md#r4)、[26B·1](lessons/26B.md#r1)、[27A·1](lessons/27A.md#r1)、[38A·1](lessons/38A.md#r1)、[38A·2](lessons/38A.md#r2)、[38B·3](lessons/38B.md#r3)、[39A·1](lessons/39A.md#r1)、[39A·3](lessons/39A.md#r3)、[39B·1](lessons/39B.md#r1)、[39D·2](lessons/39D.md#r2)。

<a id="d084"></a>

## D084 TBTL 作为最低目标与系统非最低等待的条件尺度

**定义/口径差异。** 课程多处把 TBTL 当最低修正/目标；系统明确它不是统一最低等待。双方都保留尺度和最高相关周期，但最低要求的强度不同，不能用完成十棒替代反转证据。

系统定位：[market TBTL 与运动尺度](../../trading_system/market.md#tbtl-与运动尺度)（L259）；[trade 3.5 出场、目标与期限](../../trading_system/trade.md#35-出场目标与期限)（L109）。

来源（链接中保留物理页码和条件）：[21D·2](lessons/21D.md#r2)、[21D·4](lessons/21D.md#r4)、[22A·1](lessons/22A.md#r1)、[22D·4](lessons/22D.md#r4)、[24A·2](lessons/24A.md#r2)、[24E·2](lessons/24E.md#r2)、[25B·1](lessons/25B.md#r1)、[29B·2](lessons/29B.md#r2)、[29C·4](lessons/29C.md#r4)、[29D·1](lessons/29D.md#r1)、[29D·2](lessons/29D.md#r2)、[29D·3](lessons/29D.md#r3)、[29E·3](lessons/29E.md#r3)、[29E·4](lessons/29E.md#r4)、[31A·3](lessons/31A.md#r3)、[33A·3](lessons/33A.md#r3)、[33E·3](lessons/33E.md#r3)、[38A·2](lessons/38A.md#r2)、[42A·3](lessons/42A.md#r3)、[43D·3](lessons/43D.md#r3)、[48G·3](lessons/48G.md#r3)、[49A·2](lessons/49A.md#r2)、[49B·2](lessons/49B.md#r2)、[49C·3](lessons/49C.md#r3)、[49D·3](lessons/49D.md#r3)、[52B·4](lessons/52B.md#r4)、[来源台账：SRC-10-PATTERNS general goal 与 SRC-ABBREVIATIONS TBTL](../../reference/official_sources.md#来源锚点定位)。

<a id="d085"></a>

## D085 反转第一目标至少减半及TBTL/2R后最终获利的管理模板

**未具体吸收。** 2R 退出半仓、3R 再退四分之一、余仓跟踪，以及初始/Actual Risk 不同版本等具体默认未采用；系统仅要求事先明确数量、保护和后续出场。

系统定位：[trade 3.5 出场、目标与期限](../../trading_system/trade.md#35-出场目标与期限)（L109）。

来源（链接中保留物理页码和条件）：[21D·4](lessons/21D.md#r4)、[22B·3](lessons/22B.md#r3)、[36B·1](lessons/36B.md#r1)、[36B·3](lessons/36B.md#r3)、[37A·1](lessons/37A.md#r1)、[37B·4](lessons/37B.md#r4)、[38A·2](lessons/38A.md#r2)、[38B·1](lessons/38B.md#r1)、[38C·2](lessons/38C.md#r2)、[38D·1](lessons/38D.md#r1)、[39A·2](lessons/39A.md#r2)、[39B·3](lessons/39B.md#r3)、[39D·1](lessons/39D.md#r1)、[39D·2](lessons/39D.md#r2)、[39D·3](lessons/39D.md#r3)、[42B·1](lessons/42B.md#r1)、[43D·2](lessons/43D.md#r2)、[44D·2](lessons/44D.md#r2)、[45D·1](lessons/45D.md#r1)、[46D·1](lessons/46D.md#r1)、[49B·2](lessons/49B.md#r2)。

<a id="d086"></a>

## D086 所有顶底可视为DT/DB的广义测试分类与系统同区测试判据

**定义/口径差异。** 课程广义称所有顶底均可视作 DT/DB、允许明显 HH/LL；系统须两次测试同一有意义区域及中间反向 Swing，分类范围更窄。

系统定位：[market C. Double Test 与 Neckline](../../trading_system/market.md#c-double-test-与-neckline)（L551）；[scenarios 八、趋势受损后尝试反转](../../trading_system/scenarios.md#八趋势受损后尝试反转)（L157）。

来源（链接中保留物理页码和条件）：[21D·3](lessons/21D.md#r3)、[22C·2](lessons/22C.md#r2)、[22D·3](lessons/22D.md#r3)、[25A·1](lessons/25A.md#r1)、[25A·5](lessons/25A.md#r5)、[25B·3](lessons/25B.md#r3)、[25B·4](lessons/25B.md#r4)、[49C·2](lessons/49C.md#r2)。

<a id="d087"></a>

## D087 底部MTR向旧低方向至少三分之一回撤的要求

**未具体吸收。** 底部 MTR 测旧低至少回撤反弹的三分之一等具体门槛未列入；系统只按位置、压力、测试和恢复判断。

系统定位：[scenarios 八、趋势受损后尝试反转](../../trading_system/scenarios.md#八趋势受损后尝试反转)（L157）；[market 从哪些锚点投射候选区域](../../trading_system/market.md#从哪些锚点投射候选区域)（L519）。

来源（链接中保留物理页码和条件）：[22A·1](lessons/22A.md#r1)、[29B·1](lessons/29B.md#r1)。

<a id="d088"></a>

## D088 按首次反向段强弱选择HH/LL提前反转或等待LH/HL

**部分吸收。** 早期反向 Swing 已允许；首次反向段强时可在 HH/LL 提前反转、弱时等 LH/HL 的条件选择未完整表达。

系统定位：[scenarios 八、趋势受损后尝试反转](../../trading_system/scenarios.md#八趋势受损后尝试反转)（L157）；[trade 3.2 确认程度与订单条件](../../trading_system/trade.md#32-确认程度与订单条件)（L58）。

来源（链接中保留物理页码和条件）：[22A·4](lessons/22A.md#r4)、[22C·4](lessons/22C.md#r4)、[22D·1](lessons/22D.md#r1)、[27A·2](lessons/27A.md#r2)、[31B·4](lessons/31B.md#r4)、[38A·2](lessons/38A.md#r2)、[39A·3](lessons/39A.md#r3)。

<a id="d089"></a>

## D089 趋势中反侧MAG的最后一段预警与系统长期未触均线的限定

**部分吸收。** 来源一般趋势中的反侧 MAG 也可提示最后一段测试；当前专门场景要求长期同侧且未触 EMA 后首次深回调，覆盖范围较窄。

系统定位：[scenarios 长期远离 EMA 后的首次测试](../../trading_system/scenarios.md#长期远离-ema-后的首次测试)（L76）；[market F. Gap：分离事实、直接引用与后续结果](../../trading_system/market.md#f-gap分离事实直接引用与后续结果)（L640）。

来源（链接中保留物理页码和条件）：[22C·1](lessons/22C.md#r1)、[22D·1](lessons/22D.md#r1)、[38A·1](lessons/38A.md#r1)、[39A·1](lessons/39A.md#r1)、[39C·2](lessons/39C.md#r2)、[48K·1](lessons/48K.md#r1)、[来源台账：moving average gap bar / second moving average gap bar setup](../../reference/official_sources.md#来源锚点定位)。

<a id="d090"></a>

## D090 头肩的HH到LH、LL到HL及肩头内部嵌套结构映射

**部分吸收。** 系统列肩头颈线，未完整说明 HH 头到 LH 肩/LL 到 HL 的结构次序和肩、头各自可嵌套小 MTR/楔形。

系统定位：[market A. 结构视图怎样共享事实](../../trading_system/market.md#a-结构视图怎样共享事实)（L481）；[scenarios 八、趋势受损后尝试反转](../../trading_system/scenarios.md#八趋势受损后尝试反转)（L157）。

来源（链接中保留物理页码和条件）：[22D·2](lessons/22D.md#r2)、[22D·3](lessons/22D.md#r3)、[27A·2](lessons/27A.md#r2)、[27B·1](lessons/27B.md#r1)、[38B·1](lessons/38B.md#r1)。

<a id="d091"></a>

## D091 MTR结构失败后须重新破线和测试的重置条件

**部分吸收。** 旧趋势恢复后重置已覆盖；失败 MTR 后约 20 多棒紧密恢复须重新破线及测试的具体重置模板未列明。

系统定位：[market D. H/L 次序与重置](../../trading_system/market.md#d-hl-次序与重置)（L568）；[scenarios 八、趋势受损后尝试反转](../../trading_system/scenarios.md#八趋势受损后尝试反转)（L157）。

来源（链接中保留物理页码和条件）：[22D·4](lessons/22D.md#r4)、[27B·3](lessons/27B.md#r3)、[38A·3](lessons/38A.md#r3)。

<a id="d092"></a>

## D092 最终旗形不先顺原趋势突破的广义用法

**定义/口径差异。** 来源 Final Flag 可不先沿旧趋势方向突破就反转；系统以延续失败组织，未明确该无顺势 BO 变体，不能声称系统绝对要求先顺势突破。

系统定位：[scenarios 哪些背景会改变普通回调预期](../../trading_system/scenarios.md#哪些背景会改变普通回调预期)（L62）。

来源（链接中保留物理页码和条件）：[23B·2](lessons/23B.md#r2)。

<a id="d093"></a>

## D093 楔形三推动各有反转、同向倾斜通道与收敛可选的最低定义

**部分吸收。** 当前三次可区分同向推动已有；来源各推间反转、同向通道、可不收敛、四推/截短第三推/单棒内部结构等边界未全部明示。

系统定位：[market A. 结构视图怎样共享事实](../../trading_system/market.md#a-结构视图怎样共享事实)（L481）。

来源（链接中保留物理页码和条件）：[24A·2](lessons/24A.md#r2)、[24B·1](lessons/24B.md#r1)、[24B·2](lessons/24B.md#r2)、[24B·3](lessons/24B.md#r3)、[24B·4](lessons/24B.md#r4)、[24C·2](lessons/24C.md#r2)、[24C·3](lessons/24C.md#r3)、[24E·1](lessons/24E.md#r1)、[25A·5](lessons/25A.md#r5)、[39A·3](lessons/39A.md#r3)。

<a id="d094"></a>

## D094 当前图无回调时推断低周期三推与可见事实要求

**定义/口径差异。** 来源常由当前棒推断低周期三推/回调；系统要求注明推断与实际可见数据，不允许把想象的低周期结构记作已观察事实。

系统定位：[market 3.2 观察边界与多周期](../../trading_system/market.md#32-观察边界与多周期)（L80）；[market 3.1 事实、关系与判断](../../trading_system/market.md#31-事实关系与判断)（L47）。

来源（链接中保留物理页码和条件）：[24B·1](lessons/24B.md#r1)、[24C·3](lessons/24C.md#r3)、[24D·1](lessons/24D.md#r1)、[29B·1](lessons/29B.md#r1)、[30E·4](lessons/30E.md#r4)、[42B·2](lessons/42B.md#r2)、[46E·2](lessons/46E.md#r2)、[47A·3](lessons/47A.md#r3)、[49E·3](lessons/49E.md#r3)。

<a id="d095"></a>

## D095 抛物线楔形的连续高潮三推、加速不重叠与普通衰减楔形区别

**部分吸收。** 抛物线楔形未完整定义为紧通道连续三次高潮 surge，与普通衰减楔形区别不清；来源和公开文章不统一要求逐推更陡，应保留不重叠/加速各自条件。

系统定位：[market A. 结构视图怎样共享事实](../../trading_system/market.md#a-结构视图怎样共享事实)（L481）；[scenarios 七、趋势异常加速或持续过久](../../trading_system/scenarios.md#七趋势异常加速或持续过久)（L122）。

来源（链接中保留物理页码和条件）：[24D·1](lessons/24D.md#r1)、[24D·2](lessons/24D.md#r2)、[29A·3](lessons/29A.md#r3)、[29D·1](lessons/29D.md#r1)、[33D·3](lessons/33D.md#r3)、[38C·2](lessons/38C.md#r2)、[39B·3](lessons/39B.md#r3)、[40E·3](lessons/40E.md#r3)、[来源台账：SRC-10-PATTERNS parabolic wedge](../../reference/official_sources.md#来源锚点定位)。

<a id="d096"></a>

## D096 楔形反转先形态对端、再局部测量的目标层级

**部分吸收。** 楔形/ET 反转先看形态对端、再局部高度 MM 的目标层级未完整写出；系统只按通用障碍/候选可达性处理。

系统定位：[market 从哪些锚点投射候选区域](../../trading_system/market.md#从哪些锚点投射候选区域)（L519）；[scenarios 八、趋势受损后尝试反转](../../trading_system/scenarios.md#八趋势受损后尝试反转)（L157）。

来源（链接中保留物理页码和条件）：[24D·4](lessons/24D.md#r4)、[26B·3](lessons/26B.md#r3)、[40E·3](lessons/40E.md#r3)。

<a id="d097"></a>

## D097 楔形意外突破后预留反向测量目标外宽止损并分批反做

**部分吸收。** 意外楔形 BO 后预先在不利 MM 外放宽结构保护并分层反做，系统没有该策略模板；事先宽 stop 可研究，但持仓后再放宽被当前规则禁止。

系统定位：[market 从哪些锚点投射候选区域](../../trading_system/market.md#从哪些锚点投射候选区域)（L519）；[trade 四、加仓与分层](../../trading_system/trade.md#四加仓与分层)（L214）；[trade 3.3 交易前提、路径失效与保护性止损](../../trading_system/trade.md#33-交易前提路径失效与保护性止损)（L81）。

来源（链接中保留物理页码和条件）：[24E·3](lessons/24E.md#r3)、[33A·1](lessons/33A.md#r1)、[33E·5](lessons/33E.md#r5)。

<a id="d098"></a>

## D098 Micro DT/DB 的二至四或五棒尺度与外部波段背景确认作用

**定义/口径差异。** 来源 micro DT/DB 有 2–4 与 2–5 棒冲突，公开词条还有一棒旗形用法；当前只有一般同区双测试，未具体区分这些微尺度定义及背景。

系统定位：[market A. 结构视图怎样共享事实](../../trading_system/market.md#a-结构视图怎样共享事实)（L481）；[market C. Double Test 与 Neckline](../../trading_system/market.md#c-double-test-与-neckline)（L551）。

来源（链接中保留物理页码和条件）：[25A·3](lessons/25A.md#r3)、[29B·1](lessons/29B.md#r1)、[29B·4](lessons/29B.md#r4)、[33D·4](lessons/33D.md#r4)、[40D·2](lessons/40D.md#r2)、[来源台账：micro double bottom / top 单棒旗形](../../reference/official_sources.md#来源锚点定位)。

<a id="d099"></a>

## D099 三角形至少单侧三推五交替段、各边斜率与微型变体的定义

**部分吸收。** 三角形一侧三推、至少五交替段、ET 第2/4拐点及双方边线斜率关系未完整定义；官方至少五次反转又是另一计数对象，不能直接等同五段。

系统定位：[market A. 结构视图怎样共享事实](../../trading_system/market.md#a-结构视图怎样共享事实)（L481）。

来源（链接中保留物理页码和条件）：[26A·1](lessons/26A.md#r1)、[26B·1](lessons/26B.md#r1)、[26B·2](lessons/26B.md#r2)、[26B·4](lessons/26B.md#r4)。

<a id="d100"></a>

## D100 从横向三角形到倾斜楔形的方向先验连续变化

**未具体吸收。** 从水平三角形双向接近 50/50 到倾斜楔形约 75/25 的连续先验变化未采用；系统保留倾斜/压力，但没有该数值映射。

系统定位：[market A. 结构视图怎样共享事实](../../trading_system/market.md#a-结构视图怎样共享事实)（L481）；[governance 3. 已校准的数值规则](../../trading_system/governance.md#3-已校准的数值规则)（L191）。

来源（链接中保留物理页码和条件）：[26A·3](lessons/26A.md#r3)、[44D·2](lessons/44D.md#r2)。

<a id="d101"></a>

## D101 头肩颈线两水平与两点斜线三种画法及逐层测试

**未具体吸收。** 头肩颈线可取两处水平参考或连两点成斜线，并分层测试的具体画法未列明；系统只有颈线概括和通用投射。

系统定位：[market A. 结构视图怎样共享事实](../../trading_system/market.md#a-结构视图怎样共享事实)（L481）；[market G. 趋势线与通道线](../../trading_system/market.md#g-趋势线与通道线)（L669）；[market 从哪些锚点投射候选区域](../../trading_system/market.md#从哪些锚点投射候选区域)（L519）。

来源（链接中保留物理页码和条件）：[27B·1](lessons/27B.md#r1)。

<a id="d102"></a>

## D102 每根趋势棒皆有高潮性质与停止后才命名高潮的宽窄定义

**定义/口径差异。** 课程称每根趋势棒都有 minor climactic behavior；系统偏异常加速/持续过久，公开 glossary 又含停止后的事后定义。不同名称范围不能互相覆盖。

系统定位：[scenarios 七、趋势异常加速或持续过久](../../trading_system/scenarios.md#七趋势异常加速或持续过久)（L122）；[market E. K 线与运动事实](../../trading_system/market.md#e-k-线与运动事实)（L598）。

来源（链接中保留物理页码和条件）：[29A·1](lessons/29A.md#r1)、[29C·1](lessons/29C.md#r1)、[33C·4](lessons/33C.md#r4)、[42A·2](lessons/42A.md#r2)。

<a id="d103"></a>

## D103 单次高潮偏真空、连续高潮偏衰竭及真空全程/末段两种范围

**部分吸收。** 单次高潮常解释为真空、连续高潮常解释为衰竭，以及真空可指全段或末段的范围，未完整表达；系统只用可见进展支持条件预期。

系统定位：[scenarios 七、趋势异常加速或持续过久](../../trading_system/scenarios.md#七趋势异常加速或持续过久)（L122）；[market 3.1 事实、关系与判断](../../trading_system/market.md#31-事实关系与判断)（L47）。

来源（链接中保留物理页码和条件）：[29A·4](lessons/29A.md#r4)、[29E·4](lessons/29E.md#r4)、[33D·2](lessons/33D.md#r2)。

<a id="d104"></a>

## D104 普通高潮后先三至十棒区间及恢复/反转各半的默认

**未具体吸收。** 普通高潮先约 3–10 棒 TR、再近 50/50 延续/反转，与 Big Up Big Down 较长整理不同；系统没有这些具体默认。

系统定位：[scenarios 七、趋势异常加速或持续过久](../../trading_system/scenarios.md#七趋势异常加速或持续过久)（L122）；[scenarios 五、价格到达区间或宽通道边缘](../../trading_system/scenarios.md#五价格到达区间或宽通道边缘)（L96）。

来源（链接中保留物理页码和条件）：[29A·2](lessons/29A.md#r2)、[29B·4](lessons/29B.md#r4)、[29C·3](lessons/29C.md#r3)。

<a id="d105"></a>

## D105 高潮收盘到前棒极值及更早突破点的Gap距离定义

**定义/口径差异。** 课程高潮收盘至前棒极值或旧 BO 点也称 Gap 距离，即便中间已交易；系统正 gap 强调未重新交易空间，未完整容纳这一测距用法。

系统定位：[market F. Gap：分离事实、直接引用与后续结果](../../trading_system/market.md#f-gap分离事实直接引用与后续结果)（L640）。

来源（链接中保留物理页码和条件）：[29B·3](lessons/29B.md#r3)、[29C·4](lessons/29C.md#r4)、[42A·2](lessons/42A.md#r2)、[47B·1](lessons/47B.md#r1)、[49E·1](lessons/49E.md#r1)、[50D·3](lessons/50D.md#r3)。

<a id="d106"></a>

## D106 买入高潮后LH至少收复前下跌三分之一与底部源内方向疑点

**未具体吸收。** 买高潮后 LH 需回收前下跌至少三分之一的经验门槛未采用；镜像底部文本方向存在疑点，不强行对称修正。

系统定位：[scenarios 八、趋势受损后尝试反转](../../trading_system/scenarios.md#八趋势受损后尝试反转)（L157）；[market 从哪些锚点投射候选区域](../../trading_system/market.md#从哪些锚点投射候选区域)（L519）。

来源（链接中保留物理页码和条件）：[29B·1](lessons/29B.md#r1)、[29B·2](lessons/29B.md#r2)。

<a id="d107"></a>

## D107 高潮后最低修正棒数约原趋势一半的比例时间预期

**未具体吸收。** 修正棒数至少约原趋势一半的比例时间预期未列入；不能从系统一般 TBTL 推导该条件。

系统定位：[scenarios 七、趋势异常加速或持续过久](../../trading_system/scenarios.md#七趋势异常加速或持续过久)（L122）；[market TBTL 与运动尺度](../../trading_system/market.md#tbtl-与运动尺度)（L259）。

来源（链接中保留物理页码和条件）：[29E·3](lessons/29E.md#r3)。

<a id="d108"></a>

## D108 最后趋势段回撤深度与半程/三分之一内的方向概率和RR交换

**部分吸收。** 最后趋势段的半程、外三分之一、40–60% 深度与方向/RR 交换未完整保留；已定义计算比例，不等于采用来源各档交易经验。

系统定位：[market 从哪些锚点投射候选区域](../../trading_system/market.md#从哪些锚点投射候选区域)（L519）；[market 回撤与恢复怎样改变原判断](../../trading_system/market.md#回撤与恢复怎样改变原判断)（L273）。

来源（链接中保留物理页码和条件）：[30B·4](lessons/30B.md#r4)、[43A·1](lessons/43A.md#r1)、[43D·1](lessons/43D.md#r1)、[44A·1](lessons/44A.md#r1)、[44D·1](lessons/44D.md#r1)。

<a id="d109"></a>

## D109 每笔凭经验估计数值概率与系统仅经校准才用于决策

**方法取舍。** 课程允许当场凭经验估计每笔数值胜率；系统只用定性依据，生产数字须校准发布。当前没有合格数字并不自动禁止交易。

系统定位：[governance 3. 已校准的数值规则](../../trading_system/governance.md#3-已校准的数值规则)（L191）；[trade 3.7 判断是否值得](../../trading_system/trade.md#37-判断是否值得)（L166）。

来源（链接中保留物理页码和条件）：[30B·1](lessons/30B.md#r1)、[30B·3](lessons/30B.md#r3)、[30C·4](lessons/30C.md#r4)、[30C·7](lessons/30C.md#r7)、[30E·3](lessons/30E.md#r3)、[31C·5](lessons/31C.md#r5)、[31D·3](lessons/31D.md#r3)、[38A·1](lessons/38A.md#r1)、[40E·2](lessons/40E.md#r2)、[41A·1](lessons/41A.md#r1)。

<a id="d110"></a>

## D110 十棒高低突破机械反向策略（大赢家分布意识已覆盖）

**范围未纳入。** 十棒高低突破机械反向策略未实现。少数大赢家依赖与过早退出损害已经在 Governance/Practice 明确覆盖，撤销其完全缺失判定。

系统定位：[market D. H/L 次序与重置](../../trading_system/market.md#d-hl-次序与重置)（L568）；[governance 待验证的交易与使用效果](../../trading_system/governance.md#待验证的交易与使用效果)（L256）。

来源（链接中保留物理页码和条件）：[30C·2](lessons/30C.md#r2)、[51C·3](lessons/51C.md#r3)。

<a id="d111"></a>

## D111 Always In 以当前价上下等距离先到概率定义

**部分吸收。** 当前 Always In 是清晰方向摘要；未完整定义为从现价上下等距离目标的先到概率比较，状态频率/远近目标胜率不可混用。

系统定位：[market 3.4 市场结构与持续能力](../../trading_system/market.md#34-市场结构与持续能力)（L111）；[governance 3. 已校准的数值规则](../../trading_system/governance.md#3-已校准的数值规则)（L191）。

来源（链接中保留物理页码和条件）：[30C·5](lessons/30C.md#r5)、[30E·3](lessons/30E.md#r3)、[37B·2](lessons/37B.md#r2)。

<a id="d112"></a>

## D112 正期望但回报低于风险的交易与净回报硬筛选

**方法取舍。** 来源存在成本前正期望但 reward 小于 risk 的计划；系统明文要求完整计划净回报不低于全仓止损净损失。它是筛选取舍，不是正期望定义或课程数学错误的修复方式。

系统定位：[trade 3.7 判断是否值得](../../trading_system/trade.md#37-判断是否值得)（L166）。

来源（链接中保留物理页码和条件）：[30C·6](lessons/30C.md#r6)、[30D·1](lessons/30D.md#r1)、[30E·1](lessons/30E.md#r1)、[35C·1](lessons/35C.md#r1)、[35C·3](lessons/35C.md#r3)、[43C·1](lessons/43C.md#r1)、[44C·1](lessons/44C.md#r1)、[45D·3](lessons/45D.md#r3)、[50C·2](lessons/50C.md#r2)。

<a id="d113"></a>

## D113 Scalp 小于二倍风险与 Swing 至少二倍的教学定义

**定义/口径差异。** 来源既用 scalp<2R/Swing≥2R，也用持有>10棒、品种最低点数与管理意图；系统按具体参与运动和允许过程制定方案，不设统一 2R 命名阈值。

系统定位：[trade 3.1 从条件路径开始](../../trading_system/trade.md#31-从条件路径开始)（L33）；[trade 3.5 出场、目标与期限](../../trading_system/trade.md#35-出场目标与期限)（L109）。

来源（链接中保留物理页码和条件）：[30D·2](lessons/30D.md#r2)、[31A·3](lessons/31A.md#r3)、[31A·5](lessons/31A.md#r5)、[31B·1](lessons/31B.md#r1)、[31D·4](lessons/31D.md#r4)、[41B·1](lessons/41B.md#r1)、[48A·3](lessons/48A.md#r3)、[50E·1](lessons/50E.md#r1)。

<a id="d114"></a>

## D114 连续突破按最新收盘至原共同止损距离延伸目标

**部分吸收。** 连续突破将最新收盘到原共同止损的距离当新 1R、从最新价延伸目标的滚动方法未写入；Trade 3.5 入场后 PB 投射使用不同锚点，不能替代。

系统定位：[trade 3.5 出场、目标与期限](../../trading_system/trade.md#35-出场目标与期限)（L109）；[trade 3.3 交易前提、路径失效与保护性止损](../../trading_system/trade.md#33-交易前提路径失效与保护性止损)（L81）。

来源（链接中保留物理页码和条件）：[30D·3](lessons/30D.md#r3)、[30D·4](lessons/30D.md#r4)。

<a id="d115"></a>

## D115 突破入场价只容忍一次回测、二次偏区间的状态启发式

**部分吸收。** 普通原价复测可容忍、第二次复测/两次目标未填更偏 TR 或退出的模板未完整保留；来源也有弱新高第二次仍容忍的例外，不是一条无条件强制退出。

系统定位：[market 边界处是否改变此前作用](../../trading_system/market.md#边界处是否改变此前作用)（L292）；[trade 3.5 出场、目标与期限](../../trading_system/trade.md#35-出场目标与期限)（L109）。

来源（链接中保留物理页码和条件）：[31B·3](lessons/31B.md#r3)、[33G·2](lessons/33G.md#r2)、[38B·2](lessons/38B.md#r2)、[39C·3](lessons/39C.md#r3)、[49A·4](lessons/49A.md#r4)、[49C·3](lessons/49C.md#r3)、[52A·3](lessons/52A.md#r3)、[52B·2](lessons/52B.md#r2)。

<a id="d116"></a>

## D116 最小scalp目标取近期平均棒高与日均波幅比例较大值及品种例外

**未具体吸收。** 最小 scalp 取平均棒高与约 5–10% ADR 较大者，以及品种固定最小值、1–2 最小目标与 Actual Risk 配套规则未采用；这类阈值须按产品验证。

系统定位：[trade 3.5 出场、目标与期限](../../trading_system/trade.md#35-出场目标与期限)（L109）；[market 从哪些锚点投射候选区域](../../trading_system/market.md#从哪些锚点投射候选区域)（L519）。

来源（链接中保留物理页码和条件）：[31C·3](lessons/31C.md#r3)、[31C·5](lessons/31C.md#r5)、[34B·2](lessons/34B.md#r2)、[35B·3](lessons/35B.md#r3)、[36A·1](lessons/36A.md#r1)、[36B·1](lessons/36B.md#r1)、[36B·3](lessons/36B.md#r3)、[41B·1](lessons/41B.md#r1)、[45D·1](lessons/45D.md#r1)、[45D·3](lessons/45D.md#r3)、[45E·1](lessons/45E.md#r1)、[46D·1](lessons/46D.md#r1)、[46D·3](lessons/46D.md#r3)、[49D·2](lessons/49D.md#r2)、[50A·2](lessons/50A.md#r2)、[50E·6](lessons/50E.md#r6)、[51D·1](lessons/51D.md#r1)。

<a id="d117"></a>

## D117 新手优先Stop入场、顺强趋势例外及暂避Stop-limit/marketable-limit的教学默认

**方法取舍。** 新手优先 Stop、成熟 TR 的专家 Limit、强趋势 Market/close、暂避 Stop-limit 和 marketable Limit 的教学默认未采用；当前按计划条件和平台能力选择。

系统定位：[trade 3.2 确认程度与订单条件](../../trading_system/trade.md#32-确认程度与订单条件)（L58）；[Practice 晋级与退回](../../practice/README.md#晋级与退回)（L245）。

来源（链接中保留物理页码和条件）：[32A·1](lessons/32A.md#r1)、[32A·6](lessons/32A.md#r6)、[32B·1](lessons/32B.md#r1)、[32B·3](lessons/32B.md#r3)、[47C·1](lessons/47C.md#r1)、[48B·2](lessons/48B.md#r2)、[48J·2](lessons/48J.md#r2)、[50D·2](lessons/50D.md#r2)、[来源台账：SRC-STOP-ORDERS](../../reference/official_sources.md#来源锚点定位)。

<a id="d118"></a>

## D118 本应成交而未成交时联系经纪商及责任合同的处理范围

**部分吸收。** 已有未知状态联系支持；缺价格表现似应成交却未填时的专项 Broker 核对路径。Not Held/99% 等法律或故障频率主张仅留来源，不外推。

系统定位：[account 三、提交与平台记录](../../trading_system/account.md#三提交与平台记录)（L42）；[account 五、低频平台检查](../../trading_system/account.md#五低频平台检查)（L112）。

来源（链接中保留物理页码和条件）：[32A·6](lessons/32A.md#r6)。

<a id="d119"></a>

## D119 五分钟形成中突破切一分钟连续棒提前入场及局部保护配方

**部分吸收。** 已有事先多周期参与；5 分钟形成中 BO 切 1 分钟，用 3–5/4–5 普通棒或 1–2 巨棒提前入场、保留较大保护的具体配方未采用。

系统定位：[market 3.2 观察边界与多周期](../../trading_system/market.md#32-观察边界与多周期)（L80）；[trade 3.2 确认程度与订单条件](../../trading_system/trade.md#32-确认程度与订单条件)（L58）。

来源（链接中保留物理页码和条件）：[32C·3](lessons/32C.md#r3)、[37A·3](lessons/37A.md#r3)、[41B·5](lessons/41B.md#r5)、[45B·2](lessons/45B.md#r2)、[46B·1](lessons/46B.md#r1)、[48H·1](lessons/48H.md#r1)、[50B·2](lessons/50B.md#r2)。

<a id="d120"></a>

## D120 固定金额或信号外固定距离止损与优先结构保护的选择

**方法取舍。** 课程并列固定金额、固定距离、信号外、宽 Swing stop 等选择；系统优先按本笔前提与正常波动选结构保护，不允许单靠想要的风险数值决定止损。

系统定位：[trade 3.3 交易前提、路径失效与保护性止损](../../trading_system/trade.md#33-交易前提路径失效与保护性止损)（L81）；[trade 3.7 判断是否值得](../../trading_system/trade.md#37-判断是否值得)（L166）。

来源（链接中保留物理页码和条件）：[33A·1](lessons/33A.md#r1)、[33B·2](lessons/33B.md#r2)、[33C·3](lessons/33C.md#r3)、[33E·2](lessons/33E.md#r2)、[33E·4](lessons/33E.md#r4)、[33F·4](lessons/33F.md#r4)、[34A·1](lessons/34A.md#r1)、[41A·2](lessons/41A.md#r2)、[41D·1](lessons/41D.md#r1)、[47C·2](lessons/47C.md#r2)、[48J·1](lessons/48J.md#r1)、[49E·3](lessons/49E.md#r3)、[50A·1](lessons/50A.md#r1)、[50B·1](lessons/50B.md#r1)。

<a id="d121"></a>

## D121 宽止损按最小scalp倍数、平均棒高及日均波幅比例定距

**未具体吸收。** 宽止损用 2–5 倍最小 scalp、平均趋势棒或 10–20% ADR 定距的候选规则未列出；这些与结构止损并非必然同价。

系统定位：[trade 3.3 交易前提、路径失效与保护性止损](../../trading_system/trade.md#33-交易前提路径失效与保护性止损)（L81）；[trade 3.5 出场、目标与期限](../../trading_system/trade.md#35-出场目标与期限)（L109）。

来源（链接中保留物理页码和条件）：[33E·2](lessons/33E.md#r2)、[33E·4](lessons/33E.md#r4)、[33F·4](lessons/33F.md#r4)。

<a id="d122"></a>

## D122 信号棒、区间或测量缺口投射外保护以容忍明显止损位假突破

**部分吸收。** 可用完整结构保护已有；超过明显 stop、信号/区间/MG 投射乃至不利 MM 的具体保护清单与偏移未全部明示。

系统定位：[trade 3.3 交易前提、路径失效与保护性止损](../../trading_system/trade.md#33-交易前提路径失效与保护性止损)（L81）；[market 从哪些锚点投射候选区域](../../trading_system/market.md#从哪些锚点投射候选区域)（L519）。

来源（链接中保留物理页码和条件）：[33E·5](lessons/33E.md#r5)、[33F·1](lessons/33F.md#r1)、[33F·3](lessons/33F.md#r3)、[33F·4](lessons/33F.md#r4)、[34A·1](lessons/34A.md#r1)、[39C·1](lessons/39C.md#r1)、[40E·1](lessons/40E.md#r1)、[40E·3](lessons/40E.md#r3)、[42B·1](lessons/42B.md#r1)、[45D·3](lessons/45D.md#r3)、[46D·3](lessons/46D.md#r3)、[47C·2](lessons/47C.md#r2)、[47D·1](lessons/47D.md#r1)、[48G·3](lessons/48G.md#r3)、[48H·2](lessons/48H.md#r2)、[48J·2](lessons/48J.md#r2)、[49C·1](lessons/49C.md#r1)、[49E·2](lessons/49E.md#r2)、[52A·2](lessons/52A.md#r2)。

<a id="d123"></a>

## D123 强趋势追入以指定涨段半程外保护并止损后重入

**未具体吸收。** 强趋势追入按指定最近腿 50% 外保护、止损后在新信号重新参与的具体配方未列入，比例几何和再入通则不能替代选段规则。

系统定位：[trade 3.3 交易前提、路径失效与保护性止损](../../trading_system/trade.md#33-交易前提路径失效与保护性止损)（L81）；[market 回撤与恢复怎样改变原判断](../../trading_system/market.md#回撤与恢复怎样改变原判断)（L273）。

来源（链接中保留物理页码和条件）：[33F·2](lessons/33F.md#r2)、[36B·2](lessons/36B.md#r2)、[41A·2](lessons/41A.md#r2)、[41D·1](lessons/41D.md#r1)。

<a id="d124"></a>

## D124 完美突破测试距突破点或保本位一二跳的定义与失守转换

**部分吸收。** 来源“完美测试”允许距 BO/BE 一二 tick/pip 未触及，及之后失守转换的细化未采用；系统把未触、触及、越界分开，容差需事先说明。

系统定位：[market 边界处是否改变此前作用](../../trading_system/market.md#边界处是否改变此前作用)（L292）；[account 三、提交与平台记录](../../trading_system/account.md#三提交与平台记录)（L42）。

来源（链接中保留物理页码和条件）：[33G·2](lessons/33G.md#r2)、[33G·3](lessons/33G.md#r3)、[38D·3](lessons/38D.md#r3)、[52B·3](lessons/52B.md#r3)。

<a id="d125"></a>

## D125 Scalp完成目标八九成后反转时近似保本的管理条件

**未具体吸收。** Scalp 已走目标 80–90% 随后反转时近 BE 退出的默认未保留；系统只按已选具体前提与当前交换管理。

系统定位：[trade 3.5 出场、目标与期限](../../trading_system/trade.md#35-出场目标与期限)（L109）。

来源（链接中保留物理页码和条件）：[33G·1](lessons/33G.md#r1)、[36A·1](lessons/36A.md#r1)。

<a id="d126"></a>

## D126 Actual Risk/Perfect Stop事后存活距离与系统初始风险不改、仅作未来目标参考

**定义/口径差异。** 未来 PB 距离投射用途已在 Trade 3.5 吸收。差别是课程 Perfect Stop/Actual Risk 的事后刚好存活距离及“所有人相同”表述，系统不改初始 R/预算且不反证事前优势；不计为整项缺失。

系统定位：[trade 3.5 出场、目标与期限](../../trading_system/trade.md#35-出场目标与期限)（L109）；[governance 连续过程与经济表现](../../trading_system/governance.md#连续过程与经济表现)（L55）。

来源（链接中保留物理页码和条件）：[34A·2](lessons/34A.md#r2)、[34A·4](lessons/34A.md#r4)、[34B·2](lessons/34B.md#r2)、[35C·2](lessons/35C.md#r2)、[35C·3](lessons/35C.md#r3)、[36A·1](lessons/36A.md#r1)、[36B·1](lessons/36B.md#r1)、[36B·3](lessons/36B.md#r3)、[37B·3](lessons/37B.md#r3)、[38A·2](lessons/38A.md#r2)、[38B·1](lessons/38B.md#r1)、[38C·2](lessons/38C.md#r2)、[38D·1](lessons/38D.md#r1)、[39A·2](lessons/39A.md#r2)、[39B·3](lessons/39B.md#r3)、[39C·1](lessons/39C.md#r1)、[39D·1](lessons/39D.md#r1)、[39D·2](lessons/39D.md#r2)、[41B·1](lessons/41B.md#r1)、[41B·4](lessons/41B.md#r4)、[43D·2](lessons/43D.md#r2)、[44D·2](lessons/44D.md#r2)、[45D·1](lessons/45D.md#r1)、[45D·3](lessons/45D.md#r3)、[46B·3](lessons/46B.md#r3)、[46D·1](lessons/46D.md#r1)、[46D·3](lessons/46D.md#r3)、[47D·1](lessons/47D.md#r1)、[49C·1](lessons/49C.md#r1)、[51A·3](lessons/51A.md#r3)、[51D·1](lessons/51D.md#r1)、[来源台账：SRC-MAKE-MONEY-2016](../../reference/official_sources.md#来源锚点定位)。

<a id="d127"></a>

## D127 亏损后排除异常值及假定极端盈亏抵消与连续全样本评价

**研究/隔离。** 来源事后删极端损失或假定极端盈亏互抵的样本处理未采用；系统保留连续全样本及证据缺口。该取舍已经有明确治理依据。

系统定位：[governance 四、知识进入方法前先拆清楚](../../trading_system/governance.md#四知识进入方法前先拆清楚)（L139）；[governance 3. 已校准的数值规则](../../trading_system/governance.md#3-已校准的数值规则)（L191）。

来源（链接中保留物理页码和条件）：[34B·3](lessons/34B.md#r3)、[34B·4](lessons/34B.md#r4)。

<a id="d128"></a>

## D128 加仓间距至少scalp尺度及原止损距离三分之一、首层预留比例

**未具体吸收。** 首层1/3–1/2预算、距前层≥1scalp/距首价2–3scalp、原stop距离1/3、25/25/50等配置未作为默认。当前必须预声明每层与全预算；来源不同方案不拼成统一加仓规则。

系统定位：[trade 四、加仓与分层](../../trading_system/trade.md#四加仓与分层)（L214）；[trade 3.7 判断是否值得](../../trading_system/trade.md#37-判断是否值得)（L166）。

来源（链接中保留物理页码和条件）：[35A·3](lessons/35A.md#r3)、[35B·1](lessons/35B.md#r1)、[35B·2](lessons/35B.md#r2)、[35B·3](lessons/35B.md#r3)、[35C·1](lessons/35C.md#r1)、[35C·3](lessons/35C.md#r3)、[43C·1](lessons/43C.md#r1)、[43D·1](lessons/43D.md#r1)、[44C·1](lessons/44C.md#r1)、[45D·3](lessons/45D.md#r3)、[46D·3](lessons/46D.md#r3)、[47C·2](lessons/47C.md#r2)、[47D·1](lessons/47D.md#r1)、[47D·3](lessons/47D.md#r3)、[48H·2](lessons/48H.md#r2)、[50A·1](lessons/50A.md#r1)、[50A·2](lessons/50A.md#r2)、[50B·1](lessons/50B.md#r1)、[50D·4](lessons/50D.md#r4)、[50E·2](lessons/50E.md#r2)、[50E·4](lessons/50E.md#r4)、[51D·3](lessons/51D.md#r3)、[51D·4](lessons/51D.md#r4)、[52A·4](lessons/52A.md#r4)、[52B·1](lessons/52B.md#r1)、[52B·2](lessons/52B.md#r2)。

<a id="d129"></a>

## D129 盈利加仓动能转弱后快速降回常态数量及核心/后层分工

**部分吸收。** 有加仓独立补偿与余仓方案；盈利加仓后弱动能快速退回常态数量、核心留 Swing/新层 scalp、重新充分参与的具体分工未完整列出。

系统定位：[trade 四、加仓与分层](../../trading_system/trade.md#四加仓与分层)（L214）；[trade 3.5 出场、目标与期限](../../trading_system/trade.md#35-出场目标与期限)（L109）。

来源（链接中保留物理页码和条件）：[35A·3](lessons/35A.md#r3)、[36A·2](lessons/36A.md#r2)、[37B·4](lessons/37B.md#r4)、[38D·1](lessons/38D.md#r1)、[38D·2](lessons/38D.md#r2)、[41A·3](lessons/41A.md#r3)、[41C·3](lessons/41C.md#r3)、[41D·2](lessons/41D.md#r2)。

<a id="d130"></a>

## D130 按月固定数量长期分时买入与短线战术加仓

**范围未纳入。** 按月固定数量买入的长期投资方式未纳入短线分层管理；它不等于固定金额 DCA，也不等于同笔不利价位加仓。

系统定位：[trade 四、加仓与分层](../../trading_system/trade.md#四加仓与分层)（L214）；[Practice 晋级与退回](../../practice/README.md#晋级与退回)（L245）。

来源（链接中保留物理页码和条件）：[35A·2](lessons/35A.md#r2)。

<a id="d131"></a>

## D131 不会加仓者等待专家追加位置作首次入场

**未具体吸收。** 无法执行专家分层的人，可等专家追加处作为自己首笔、用新反转信号入场；系统有等待/减量但未保留该替代参与启发。

系统定位：[trade 3.2 确认程度与订单条件](../../trading_system/trade.md#32-确认程度与订单条件)（L58）；[Practice 晋级与退回](../../practice/README.md#晋级与退回)（L245）。

来源（链接中保留物理页码和条件）：[35A·2](lessons/35A.md#r2)、[51D·3](lessons/51D.md#r3)。

<a id="d132"></a>

## D132 管理必须忽略入场价的绝对主张与当前全仓核算

**方法取舍。** 来源“管理须忽略入场价”的绝对强调与当前未来交换/累计预算并用不同；系统当前风险从现价算，仍需入场价核算真实净结果。来源首价 BE 模板本身也依赖入场价。

系统定位：[trade 3.7 判断是否值得](../../trading_system/trade.md#37-判断是否值得)（L166）；[trade 3.5 出场、目标与期限](../../trading_system/trade.md#35-出场目标与期限)（L109）。

来源（链接中保留物理页码和条件）：[36A·4](lessons/36A.md#r4)、[39C·3](lessons/39C.md#r3)、[52A·3](lessons/52A.md#r3)。

<a id="d133"></a>

## D133 尾盘反转必须迅速推进及前棒反向四tick退出条件

**部分吸收。** 尾盘缺跟随应快退已有；BTC/STC 3–6棒窗口、2–3棒识别、1–3次短机会、前棒反向4ticks/其他缓冲及最后一分钟处理未完整保留，各模板有不同语境。

系统定位：[scenarios 固定 Session 中的背景与等待](../../trading_system/scenarios.md#固定-session-中的背景与等待)（L33）；[trade 3.5 出场、目标与期限](../../trading_system/trade.md#35-出场目标与期限)（L109）。

来源（链接中保留物理页码和条件）：[38D·3](lessons/38D.md#r3)、[41A·3](lessons/41A.md#r3)、[41D·2](lessons/41D.md#r2)、[48H·3](lessons/48H.md#r3)、[48I·2](lessons/48I.md#r2)、[48J·1](lessons/48J.md#r1)、[48K·2](lessons/48K.md#r2)、[49D·2](lessons/49D.md#r2)、[49E·3](lessons/49E.md#r3)、[50D·3](lessons/50D.md#r3)、[50D·4](lessons/50D.md#r4)、[50E·6](lessons/50E.md#r6)、[51B·4](lessons/51B.md#r4)、[52A·2](lessons/52A.md#r2)、[52B·2](lessons/52B.md#r2)。

<a id="d134"></a>

## D134 平仓后多数人先空仓一至三棒再评估反手

**方法取舍。** 来源多数人退出后空仓观察1–3或1–2棒再反手，熟练者可直接反手；系统以清理旧执行风险及新方案合格为条件，没有固定心理冷却棒数。

系统定位：[trade 3.5 出场、目标与期限](../../trading_system/trade.md#35-出场目标与期限)（L109）；[Practice 晋级与退回](../../practice/README.md#晋级与退回)（L245）。

来源（链接中保留物理页码和条件）：[38D·3](lessons/38D.md#r3)、[41C·1](lessons/41C.md#r1)、[42A·1](lessons/42A.md#r1)、[43C·2](lessons/43C.md#r2)、[44C·2](lessons/44C.md#r2)。

<a id="d135"></a>

## D135 Noise作为相对目标尺度的反转及不存在随机噪音的强断言

**研究/隔离。** 相对目标尺度的噪声/小反转思想可由系统尺度规则表达；“根本没有噪声或随机运动”的绝对论未采用，没有把每个 tick 当可预测优势。

系统定位：[market 3.1 事实、关系与判断](../../trading_system/market.md#31-事实关系与判断)（L47）；[Practice 晋级与退回](../../practice/README.md#晋级与退回)（L245）。

来源（链接中保留物理页码和条件）：[40A·1](lessons/40A.md#r1)、[40B·1](lessons/40B.md#r1)、[51A·1](lessons/51A.md#r1)。

<a id="d136"></a>

## D136 BTC/STC首次动能减弱后缩目标、积极管理及转Limit的阶段配方

**部分吸收。** BTC/STC 首次失望可从追收盘转向更近目标、Limit、宽保护与计划内补仓的阶段配方未完整保留；系统有双边化后重评的一般原则。

系统定位：[trade 3.5 出场、目标与期限](../../trading_system/trade.md#35-出场目标与期限)（L109）；[trade 3.2 确认程度与订单条件](../../trading_system/trade.md#32-确认程度与订单条件)（L58）。

来源（链接中保留物理页码和条件）：[40A·3](lessons/40A.md#r3)、[40B·3](lessons/40B.md#r3)、[40D·1](lessons/40D.md#r1)、[40E·1](lessons/40E.md#r1)、[41B·2](lessons/41B.md#r2)、[50D·4](lessons/50D.md#r4)。

<a id="d137"></a>

## D137 Final Trend Bar事后定义与其后Give-up反转棒的区分

**定义/口径差异。** Final Trend Bar 事后才知，后续 Give-up 为放弃产生的反向大棒；系统未明确两个术语和次序，不能把大反向棒认成旧趋势最后顺向棒。

系统定位：[scenarios 七、趋势异常加速或持续过久](../../trading_system/scenarios.md#七趋势异常加速或持续过久)（L122）；[market E. K 线与运动事实](../../trading_system/market.md#e-k-线与运动事实)（L598）。

来源（链接中保留物理页码和条件）：[40B·1](lessons/40B.md#r1)、[40C·1](lessons/40C.md#r1)、[48G·3](lessons/48G.md#r3)、[51B·2](lessons/51B.md#r2)、[52A·3](lessons/52A.md#r3)。

<a id="d138"></a>

## D138 末端收盘两次方向测试失败后转试另一方向的预期

**未具体吸收。** 末端两次尝试同一方向失败后转试另一方向的启发未列明；系统仅按各方成果更新，不以两次计数自动推对侧目标。

系统定位：[market 由表现更新预期](../../trading_system/market.md#由表现更新预期)（L321）；[market 边界处是否改变此前作用](../../trading_system/market.md#边界处是否改变此前作用)（L292）。

来源（链接中保留物理页码和条件）：[40B·2](lessons/40B.md#r2)、[40D·2](lessons/40D.md#r2)、[49E·2](lessons/49E.md#r2)。

<a id="d139"></a>

## D139 收盘价为最重要单一价格及折线图的教学优先级

**方法取舍。** 来源将收盘价视为最重要单一价格并建议用折线图突出；系统共同比较多种价格事实，没有这种固定优先排序。

系统定位：[market 当前运动的强弱](../../trading_system/market.md#当前运动的强弱)（L227）；[market 3.5 重要区域图与路径作用](../../trading_system/market.md#35-重要区域图与路径作用)（L178）。

来源（链接中保留物理页码和条件）：[40B·1](lessons/40B.md#r1)、[45A·3](lessons/45A.md#r3)。

<a id="d140"></a>

## D140 第一次任何回调即结束突破阶段与系统首次有意义回调的门槛

**定义/口径差异。** 课程第一回调即结束 BO 阶段；系统明确第一“有意义”回调，小停顿迅速恢复仍可归 BO。阶段起点与后续通道目标选择会不同。

系统定位：[scenarios 通道突破的方向与目标](../../trading_system/scenarios.md#通道突破的方向与目标)（L134）；[market 回撤与恢复怎样改变原判断](../../trading_system/market.md#回撤与恢复怎样改变原判断)（L273）。

来源（链接中保留物理页码和条件）：[41B·2](lessons/41B.md#r2)、[43B·2](lessons/43B.md#r2)、[44B·2](lessons/44B.md#r2)。

<a id="d141"></a>

## D141 强反向旗形信号未触发即被顺向突破的陷阱确认序列

**部分吸收。** 来源反向旗形信号尚未触发就被原趋势突破是一种强延续证据；系统区分 setup/trigger，但未明确这个阻止触发的序列与已触发失败的差别。

系统定位：[market D. H/L 次序与重置](../../trading_system/market.md#d-hl-次序与重置)（L568）；[market 边界处是否改变此前作用](../../trading_system/market.md#边界处是否改变此前作用)（L292）。

来源（链接中保留物理页码和条件）：[41B·3](lessons/41B.md#r3)。

<a id="d142"></a>

## D142 剩余趋势仓至少两个重要阻力或支撑理由重合再退出的默认

**未具体吸收。** 课程剩余趋势仓至少两个重要 SR 理由重合才退出的默认未保留；系统评价信息增量和实际前提，不用固定理由数授权退出。

系统定位：[trade 3.5 出场、目标与期限](../../trading_system/trade.md#35-出场目标与期限)（L109）；[market 3.5 重要区域图与路径作用](../../trading_system/market.md#35-重要区域图与路径作用)（L178）。

来源（链接中保留物理页码和条件）：[43D·2](lessons/43D.md#r2)、[44D·2](lessons/44D.md#r2)。

<a id="d143"></a>

## D143 宽通道五棒以上段、三倍最小scalp、二至三均棒及三上三下/百棒确认的尺度簇

**未具体吸收。** 宽通道≥5棒段、≥3最小scalp、≥2–3平均棒、三上三下/约100棒成熟，以及10–20棒/2–3日典型长度未列入；来源早期三上推与严格双向成熟不同。

系统定位：[scenarios 通道突破的方向与目标](../../trading_system/scenarios.md#通道突破的方向与目标)（L134）；[market 3.4 市场结构与持续能力](../../trading_system/market.md#34-市场结构与持续能力)（L111）。

来源（链接中保留物理页码和条件）：[45A·1](lessons/45A.md#r1)、[45A·2](lessons/45A.md#r2)、[45C·2](lessons/45C.md#r2)、[46A·1](lessons/46A.md#r1)、[46A·2](lessons/46A.md#r2)、[46B·3](lessons/46B.md#r3)。

<a id="d144"></a>

## D144 屏幕约百棒与五分钟仅当日或前日形态、跨三日改高周期的观察范围默认

**方法取舍。** 课程约100–200棒画面、5分钟主要当日/前日、跨3日改高周期等观察默认未采用；系统按当前问题需要选择历史与周期，不固定屏幕长度。

系统定位：[market 3.2 观察边界与多周期](../../trading_system/market.md#32-观察边界与多周期)（L80）；[README 1. 低频准备](../../practice/README.md#1-低频准备)（L21）。

来源（链接中保留物理页码和条件）：[45A·2](lessons/45A.md#r2)、[45B·2](lessons/45B.md#r2)、[46A·2](lessons/46A.md#r2)、[46B·1](lessons/46B.md#r1)。

<a id="d145"></a>

## D145 此前失败突破幅度用于入场加仓止盈及旧极值外两倍最大突破的灾难止损

**部分吸收。** 来源用此前失败突破最大幅度选择更远入场、层距、半幅目标及旧极值外两倍最大幅度的灾难stop；系统缺具体投射方法。46D明确展示该远stop仍被击中，不能当保本保证。

系统定位：[market 从哪些锚点投射候选区域](../../trading_system/market.md#从哪些锚点投射候选区域)（L519）；[trade 3.3 交易前提、路径失效与保护性止损](../../trading_system/trade.md#33-交易前提路径失效与保护性止损)（L81）；[trade 四、加仓与分层](../../trading_system/trade.md#四加仓与分层)（L214）。

来源（链接中保留物理页码和条件）：[45D·2](lessons/45D.md#r2)、[45D·3](lessons/45D.md#r3)、[45D·4](lessons/45D.md#r4)、[46D·2](lessons/46D.md#r2)、[46D·3](lessons/46D.md#r3)、[47C·2](lessons/47C.md#r2)。

<a id="d146"></a>

## D146 宽通道开始形成LL/LH即停止原趋势交易的简化终止门槛

**部分吸收。** 宽牛通道一处以开始 LL/LH 停止原趋势交易，镜像另处明确 major HH；系统按主要结构与接受判断，局部点保护仍可另设。缺的是来源简化默认，非所有最近HL/LH跟踪都被禁止。

系统定位：[market 3.4 市场结构与持续能力](../../trading_system/market.md#34-市场结构与持续能力)（L111）；[trade 3.4 移动止损](../../trading_system/trade.md#34-移动止损)（L98）；[scenarios 通道突破的方向与目标](../../trading_system/scenarios.md#通道突破的方向与目标)（L134）。

来源（链接中保留物理页码和条件）：[45E·3](lessons/45E.md#r3)、[46E·3](lessons/46E.md#r3)、[51D·1](lessons/51D.md#r1)、[52A·1](lessons/52A.md#r1)。

<a id="d147"></a>

## D147 成熟区间至少两上两下且双向各10–20棒Always In swing的典型结构

**未具体吸收。** 成熟 TR 至少两上两下且双向各10–20棒 Always In Swing 的典型条件未采用；系统只定性要求明确边界和反复测试。

系统定位：[scenarios 五、价格到达区间或宽通道边缘](../../trading_system/scenarios.md#五价格到达区间或宽通道边缘)（L96）；[market 3.4 市场结构与持续能力](../../trading_system/market.md#34-市场结构与持续能力)（L111）。

来源（链接中保留物理页码和条件）：[47A·3](lessons/47A.md#r3)。

<a id="d148"></a>

## D148 区间突破只差一根跟进成为Always In时反向交易当前收盘

**未具体吸收。** TR 突破只差一根 FT 成为 clear AI 时，在当前收盘反做赌无 FT 的特定策略未列入；这与已确认强 BO 后继续淡化不同。

系统定位：[scenarios 五、价格到达区间或宽通道边缘](../../trading_system/scenarios.md#五价格到达区间或宽通道边缘)（L96）；[trade 3.2 确认程度与订单条件](../../trading_system/trade.md#32-确认程度与订单条件)（L58）。

来源（链接中保留物理页码和条件）：[47C·1](lessons/47C.md#r1)。

<a id="d149"></a>

## D149 新手区间止损后最多第二次反转重入、第三次不再进的默认

**方法取舍。** 新手 TR 止损后最多第二次反转重入、第三次不进的次数限制未采用；系统按新证据、预算、执行和连续成本重评。

系统定位：[trade 3.5 出场、目标与期限](../../trading_system/trade.md#35-出场目标与期限)（L109）；[Practice 晋级与退回](../../practice/README.md#晋级与退回)（L245）。

来源（链接中保留物理页码和条件）：[47C·2](lessons/47C.md#r2)。

<a id="d150"></a>

## D150 开盘与尾盘偏突破Swing、中段偏通道区间的日内三阶段框架

**部分吸收。** 开盘/尾盘偏 BO Swing、中段偏 CH/TR 的三阶段模型及1–3小时转换、2–4小时中段等未完整保留；不是把交易日等分三段。

系统定位：[scenarios 固定 Session 中的背景与等待](../../trading_system/scenarios.md#固定-session-中的背景与等待)（L33）。

来源（链接中保留物理页码和条件）：[48A·1](lessons/48A.md#r1)、[48A·3](lessons/48A.md#r3)、[48B·1](lessons/48B.md#r1)、[48C·3](lessons/48C.md#r3)、[48D·2](lessons/48D.md#r2)、[48F·3](lessons/48F.md#r3)、[48G·1](lessons/48G.md#r1)、[48H·1](lessons/48H.md#r1)、[48I·1](lessons/48I.md#r1)、[49A·1](lessons/49A.md#r1)、[49B·1](lessons/49B.md#r1)。

<a id="d151"></a>

## D151 初始摆动占平均日振幅25–50%或50–100%用于反转后趋势与区间预期

**未具体吸收。** 首段占 ADR25–50% 后反转更可能相反趋势，50–100% 更偏TR，极强反转例外；来源说明可用于所有反转，系统无该尺度模板。

系统定位：[scenarios 固定 Session 中的背景与等待](../../trading_system/scenarios.md#固定-session-中的背景与等待)（L33）；[market 回撤与恢复怎样改变原判断](../../trading_system/market.md#回撤与恢复怎样改变原判断)（L273）。

来源（链接中保留物理页码和条件）：[48A·2](lessons/48A.md#r2)。

<a id="d152"></a>

## D152 日线方向与早晚影线由日内反转形成的对应及早期逆向测试偏置

**部分吸收。** 日线方向与早晚影线由日内逆向测试形成、高周期趋势下早期逆向尝试易失败的时序模型未完整表达；一般多周期规则不足以推出。

系统定位：[scenarios 固定 Session 中的背景与等待](../../trading_system/scenarios.md#固定-session-中的背景与等待)（L33）；[market 3.2 观察边界与多周期](../../trading_system/market.md#32-观察边界与多周期)（L80）。

来源（链接中保留物理页码和条件）：[48B·1](lessons/48B.md#r1)、[48C·1](lessons/48C.md#r1)。

<a id="d153"></a>

## D153 昨日高潮后可先延续1–2小时再两小时横盘反向的次日路径

**未具体吸收。** 昨日高潮可先延续1–2小时再两小时横盘/反向的次日模板未列入；50/75/25%分别对应不同事件，已在昨日整理等例外也保留。

系统定位：[scenarios 固定 Session 中的背景与等待](../../trading_system/scenarios.md#固定-session-中的背景与等待)（L33）；[scenarios 七、趋势异常加速或持续过久](../../trading_system/scenarios.md#七趋势异常加速或持续过久)（L122）。

来源（链接中保留物理页码和条件）：[48C·2](lessons/48C.md#r2)、[49D·3](lessons/49D.md#r3)。

<a id="d154"></a>

## D154 开盘BOM首根两侧测试、初始不超过一棒及5–10棒/30–50%日振幅成熟度

**部分吸收。** Opening BOM 的首棒两侧测试、初始腿≤1棒、5–10棒范围及约30–50%ADR等具体识别没有保留；同图BOM命名冲突仍未统一，不作为无条件标准。

系统定位：[scenarios 固定 Session 中的背景与等待](../../trading_system/scenarios.md#固定-session-中的背景与等待)（L33）；[scenarios 五、价格到达区间或宽通道边缘](../../trading_system/scenarios.md#五价格到达区间或宽通道边缘)（L96）。

来源（链接中保留物理页码和条件）：[48D·1](lessons/48D.md#r1)、[48D·2](lessons/48D.md#r2)。

<a id="d155"></a>

## D155 前18棒范围突破独立于BOM，15–25棒关注窗及反侧日极值保持预期

**未具体吸收。** 前18棒范围突破与Opening BOM独立，15–25/16–20棒关注窗及对侧日极值保持预期未定义；来源有延到21棒和只说大部分时段保持的例子。

系统定位：[scenarios 固定 Session 中的背景与等待](../../trading_system/scenarios.md#固定-session-中的背景与等待)（L33）；[scenarios 五、价格到达区间或宽通道边缘](../../trading_system/scenarios.md#五价格到达区间或宽通道边缘)（L96）。

来源（链接中保留物理页码和条件）：[48D·2](lessons/48D.md#r2)。

<a id="d156"></a>

## D156 窄昨日范围更易外包日、反转日不远过开盘另一端并收近开盘的预期

**未具体吸收。** 昨日窄范围更易outside day；reversal day通常不远过开盘另一端并收近开盘的日型启发未采用。

系统定位：[scenarios 固定 Session 中的背景与等待](../../trading_system/scenarios.md#固定-session-中的背景与等待)（L33）。

来源（链接中保留物理页码和条件）：[48E·1](lessons/48E.md#r1)。

<a id="d157"></a>

## D157 跳空相对昨收/收盘区间/昨日极值及近端改为当日极值的动态边界

**部分吸收。** 已有session gap与旧OHLC，但昨收/closing TR/昨高低三种参照，以及近端从open改首棒或当日极值的动态配对未完整列出。

系统定位：[market F. Gap：分离事实、直接引用与后续结果](../../trading_system/market.md#f-gap分离事实直接引用与后续结果)（L640）；[scenarios 固定 Session 中的背景与等待](../../trading_system/scenarios.md#固定-session-中的背景与等待)（L33）。

来源（链接中保留物理页码和条件）：[48F·1](lessons/48F.md#r1)。

<a id="d158"></a>

## D158 最后一小时新反转通道弱于较早通道、末30分钟横盘延续及避免逆向分层的默认

**部分吸收。** 最后1小时新反转通道较早建立者更易仅TR一腿、末30分钟TR延续及避免逆向Limit分层等限制未完整保留；系统仅概括时间不足需更快重评。

系统定位：[scenarios 固定 Session 中的背景与等待](../../trading_system/scenarios.md#固定-session-中的背景与等待)（L33）；[trade 3.2 确认程度与订单条件](../../trading_system/trade.md#32-确认程度与订单条件)（L58）；[trade 3.5 出场、目标与期限](../../trading_system/trade.md#35-出场目标与期限)（L109）。

来源（链接中保留物理页码和条件）：[48I·1](lessons/48I.md#r1)、[48I·2](lessons/48I.md#r2)、[48J·2](lessons/48J.md#r2)、[52A·2](lessons/52A.md#r2)。

<a id="d159"></a>

## D159 NYSE TICK逐股最新成交方向求和与价格tick区分、对齐价格周期

**范围未纳入。** NYSE TICK 的逐股最新成交方向+1/0/−1求和、与价格tick区别及1/5分钟对齐未定义；当前通用辅助信息要求不等于采用此指标。

系统定位：[market 3.1 事实、关系与判断](../../trading_system/market.md#31-事实关系与判断)（L47）；[market 3.2 观察边界与多周期](../../trading_system/market.md#32-观察边界与多周期)（L80）。

来源（链接中保留物理页码和条件）：[50C·1](lessons/50C.md#r1)。

<a id="d160"></a>

## D160 TICK首次±700/1000极值顺势、后期重复极值高潮的阶段规则

**范围未纳入。** TICK首次±700/1000极值顺势，后期20多棒弱stairs或重复第3/4极值更偏高潮的阶段规则未纳入。

系统定位：[market 3.1 事实、关系与判断](../../trading_system/market.md#31-事实关系与判断)（L47）；[trade 3.2 确认程度与订单条件](../../trading_system/trade.md#32-确认程度与订单条件)（L58）。

来源（链接中保留物理页码和条件）：[50C·2](lessons/50C.md#r2)。

<a id="d161"></a>

## D161 TICK新价格极值背离结合支阻的专家逆势与先顺势重测流程

**范围未纳入。** TICK首次极值后先顺势重测、价格创新极值但TICK未创新并结合SR的专家反做，以及对应目标/位置配方未纳入。

系统定位：[market 3.1 事实、关系与判断](../../trading_system/market.md#31-事实关系与判断)（L47）；[scenarios 八、趋势受损后尝试反转](../../trading_system/scenarios.md#八趋势受损后尝试反转)（L157）。

来源（链接中保留物理页码和条件）：[50C·3](lessons/50C.md#r3)。

<a id="d162"></a>

## D162 TICK自身前高前低支阻及持续零轴一侧的广度偏置

**范围未纳入。** TICK自身前高低可作支阻、多数时间在零轴同侧及多次700+增加突破偏置的规则未纳入。

系统定位：[market 3.1 事实、关系与判断](../../trading_system/market.md#31-事实关系与判断)（L47）；[market 3.5 重要区域图与路径作用](../../trading_system/market.md#35-重要区域图与路径作用)（L178）。

来源（链接中保留物理页码和条件）：[50C·4](lessons/50C.md#r4)。

<a id="d163"></a>

## D163 Body gap 的非相邻实体参照与系统相邻限定

**定义/口径差异。** 公开来源 body gap 不要求相邻实体；当前仅列相邻实体之间的body gap，非相邻版本未明确。

系统定位：[market F. Gap：分离事实、直接引用与后续结果](../../trading_system/market.md#f-gap分离事实直接引用与后续结果)（L640）。

来源（链接中保留物理页码和条件）：[来源台账：body gap 非相邻实体](../../reference/official_sources.md#来源锚点定位)。

<a id="d164"></a>

## D164 Gap reversal 越前棒一跳但不必到真正缺口边界

**未具体吸收。** 公开来源 gap reversal 是沿gap方向越前棒一跳、未必到真正gap边界；当前未保留该具体具名关系。

系统定位：[market F. Gap：分离事实、直接引用与后续结果](../../trading_system/market.md#f-gap分离事实直接引用与后续结果)（L640）；[market E. K 线与运动事实](../../trading_system/market.md#e-k-线与运动事实)（L598）。

来源（链接中保留物理页码和条件）：[来源台账：gap reversal 越前棒一跳](../../reference/official_sources.md#来源锚点定位)。

<a id="d165"></a>

## D165 Exhaustion gap 的停止或小反转定义不要求缺口关闭

**部分吸收。** 来源exhaustion不要求完整或迅速关闭gap，课程也允许只停止卖压；系统已分离时间修正与关闭，但未完整列出这些命名边界，不能误报为硬性要求全填。

系统定位：[market F. Gap：分离事实、直接引用与后续结果](../../trading_system/market.md#f-gap分离事实直接引用与后续结果)（L640）；[scenarios 七、趋势异常加速或持续过久](../../trading_system/scenarios.md#七趋势异常加速或持续过久)（L122）。

来源（链接中保留物理页码和条件）：[来源台账：exhaustion gap 不要求回补；11A/11B 横盘开放例](../../reference/official_sources.md#来源锚点定位)。

<a id="d166"></a>

## D166 来源 failure/success 的止损与目标先后及系统市场/交易结果分离

**定义/口径差异。** 来源failure/success绑定stop与所选目标先后；当前拆市场路径、实际交易与净结果。先后原则已吸收，区别是评价对象不再共用一个failure名称。

系统定位：[market 3.7 条件路径与目标](../../trading_system/market.md#37-条件路径与目标)（L357）；[account 三、提交与平台记录](../../trading_system/account.md#三提交与平台记录)（L42）；[governance 四、知识进入方法前先拆清楚](../../trading_system/governance.md#四知识进入方法前先拆清楚)（L139）。

来源（链接中保留物理页码和条件）：[来源台账：failure / success / trapped in a trade](../../reference/official_sources.md#来源锚点定位)。
