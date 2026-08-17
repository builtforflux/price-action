# 情景覆盖矩阵（Coverage Matrix）

> **状态：Strategy / Index（完整性核验工具）**
>
> 本矩阵用于核验：已注册的五个 Setup 家族 × 当前选定的状态与证据词汇，不存在未处理的组合。它不宣称覆盖所有可能的价格行为交易机会（core 明确五个家族只是示例、不是穷尽分类）。

## 使用方法

1. 每次读图先按「基础状态 → 阶段/叠加层 → 结构进度 → 空间检查 → 时段覆盖」的顺序（与矩阵列顺序一致）识别状态与候选，再由 `PREMISE_SELECT` 统一检查候选空间（G01）、硬 NO_TRADE 约束、Trader's Equation 与等待条件，输出唯一叶子；
2. 每行只能落一种叶子：`STRATEGY`（可交易策略页）/ `WATCH`（候选观察或等待新证据）/ `NO_TRADE`（显式不交易）。`STRATEGY` 表示进入该策略页继续检查六要素（premise、触发、失效、stop、目标、管理），并据此建立 Trade Plan，不直接构成交易许可；
3. **空间和时间都按候选判断**：目标、方向、合理 stop 与持有期属于同一份计划。一个候选空间或剩余时间不足，不代表反向候选或独立 scalp 也不成立；`G01` 只在**当前所有可识别候选到各自现实 target 的空间均不足**时命中。`R28` 在候选完成 entry、stop、target 与持有方式之后、最终 `PREMISE_SELECT` 之前逐候选过滤：拒绝时间不足的 swing，但保留已经独立建立且时间足够的 scalp，不能把 swing 的时间失败升级为全局 NO_TRADE。同一行情采用**多候选收集模型**：STRATEGY、等待型 WATCH、硬 NO_TRADE 与检查点可以同时产生；先做同家族精度消歧，再执行候选级 R28，最后送入 PSEL。PSEL 按固定顺序输出唯一叶子——① 用 R23/R24 过滤其实际适用位置内的候选；② 所有完整候选均被 R28 或 G01 拒绝 → NO_TRADE；③ 存在时间与空间均合格的完整 STRATEGY 候选：至少一个方程成立 → 明确选择 premise（多个均通过时记录交易者明确选择，方程不自动产生唯一排序）→ STRATEGY，全部方程不成立 → NO_TRADE；④ 无完整策略、存在等待型 WATCH → WATCH；⑤ 均无候选（含仅状态检查点提示）→ NO_TRADE。状态检查点行（R09/R10/R11）不参与最终叶子优先级，仅作为管理提示随所选 STRATEGY 保留；
4. 命中 `WATCH` 后，等待新数据从入口重新运行，矩阵内部不保留回边（流程图同样处理）；
5. 时段覆盖列只叠加约束（候选起点、最晚入场、时间风险），不改变底层家族；时间不足只把对应候选过滤为 NO_TRADE，不自动改变其他候选；
6. `R02`、`R22` 是全局行 G01 的具体示例，不单独构成新规则；
7. 行号格式：R01–R48 为正文行，G01 为全局行；既有 R01–R46 在重构时保持稳定，新增覆盖只向后追加，不再使用字母后缀。`R02`、`R22` 是 G01 的示例行（alias_of=G01），不要求 Mermaid 中存在独立节点；程序化 ID 校验应允许别名映射。

## 叶子枚举

| 枚举 | 含义 | 处理 |
| --- | --- | --- |
| STRATEGY | 可交易策略页 | 进入该策略页继续检查六要素，并据此建立 Trade Plan |
| WATCH | 候选观察或等待新证据 | 记录当前状态与所需证据；不建立入场 |
| NO_TRADE | 显式不交易 | 无需理由之外的等待或回避 |

## 全局优先行

| 行 | 基础状态 | 阶段/叠加层 | 结构进度 | 空间检查 | 时段覆盖 | 叶子 | Setup 家族页 | Pattern/Context 页 | 课程定义来源 | 课程综合复核 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| G01 | 任意 | 任意 | 任意 | 所有可识别候选均无空间 | — | NO_TRADE：当前所有可识别候选到各自现实 target 的空间均不足（全局优先；任一候选空间足够则交由 PSEL 按各自方程判断） | — | [支撑阻力与目标](../core/02_context/01_support_resistance_targets.md) | 19、20、31 | 49 |

## 矩阵

| 行 | 基础状态 | 阶段/叠加层 | 结构进度 | 空间检查 | 时段覆盖 | 叶子 | Setup 家族页 | Pattern/Context 页 | 课程定义来源 | 课程综合复核 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| R01 | spike | — | 首次浅回调，控制仍有效 | 足够 | — | STRATEGY：[趋势/第一次小回调](trend/first_small_pullback.md) | [趋势延续 Setup](../core/05_setups/01_trend_continuation.md) | [趋势和通道](../core/01_market_cycle/01_trends_and_channels.md) | 09、14、41 | 43、49 |
| R02 | spike | — | 首次浅回调，控制仍有效 | 不足 | — | NO_TRADE：目标空间不足（G01 示例） | — | [支撑阻力与目标](../core/02_context/01_support_resistance_targets.md) | 19、31 | 49 |
| R03 | spike | — | 强 breakout + follow-through 或后续连续强收盘，无回踩 | 足够 | — | STRATEGY：[突破/收盘跟随（确认版）](breakout/buy_sell_the_close.md) | [突破延续 Setup](../core/05_setups/02_breakout_continuation.md) | [突破和突破模式](../core/01_market_cycle/03_breakouts_and_breakout_mode.md) | 15、18、41 | 47、49 |
| R04 | spike | — | 强 breakout + follow-through 后回踩守住 | 足够 | — | STRATEGY：[突破/突破回踩](breakout/breakout_pullback_test.md) | [突破延续 Setup](../core/05_setups/02_breakout_continuation.md) | [突破和突破模式](../core/01_market_cycle/03_breakouts_and_breakout_mode.md) | 15、18 | 47、49 |
| R05 | spike | — | 仅越界，未获接受 | — | — | WATCH：等待接受证据（breakout attempt） | — | [突破和突破模式](../core/01_market_cycle/03_breakouts_and_breakout_mode.md) | 15 | 49 |
| R06 | trend 晚段 | climax | 高潮式推进，无反向证据 | 足够 | — | WATCH：不逆势；等反向证据或继续 | — | [高潮和状态转换](../core/01_market_cycle/04_climax_and_transition.md) | 29、42 | 40、49 |
| R07 | trend 晚段 | climax | 高潮后反向证据获接受（完整 MTR 链未成立） | 足够 | — | STRATEGY：[反转/高潮后修正](reversal/climax_correction.md)（两腿修正；TBTL 仅预写 runner 持有预期） | [逆势修正 Scalp](../core/05_setups/05_minor_reversal_scalp.md) | [高潮和状态转换](../core/01_market_cycle/04_climax_and_transition.md) | 21A、23B、29 | 49 |
| R08 | tight channel | — | 回调未破坏控制（约 20 根内） | 足够 | — | STRATEGY：[趋势/第一次小回调](trend/first_small_pullback.md)、[第二次恢复信号](trend/second_signal_continuation.md) | [趋势延续 Setup](../core/05_setups/01_trend_continuation.md) | [趋势和通道](../core/01_market_cycle/01_trends_and_channels.md) | 17、18C | 43–44 |
| R12 | tight channel | — | 合格逆势触发（完整 MTR 链未成立） | 足够 | — | STRATEGY（依结构二次判定）：无更具体形态用[通用逆势修正](reversal/minor_reversal_scalp.md)；wedge / final flag / climax 分别使用对应专页 | [逆势修正 Scalp](../core/05_setups/05_minor_reversal_scalp.md) | [市场周期](../core/01_market_cycle/00_market_cycle.md) | 21A、23–24 | 49 |
| R13 | tight channel | endless pullback | 趋势控制衰减（约 20 根以上） | — | — | WATCH：重新归类为长回调/反向通道/TR/BOM，等待反向接受 | — | [趋势和通道](../core/01_market_cycle/01_trends_and_channels.md) | 14E、37 | 43–46、49 |
| R14 | broad channel | — | 回调未破坏控制 | 足够 | — | STRATEGY：[趋势/宽通道参与区](trend/broad_channel_buy_zone.md)（最近腿下部区域） | [趋势延续 Setup](../core/05_setups/01_trend_continuation.md) | [趋势和通道](../core/01_market_cycle/01_trends_and_channels.md) | 14、16、45–46 | 45–46 |
| R15 | broad channel | transition | 趋势线破/回调加深/双边增加 | 足够 | — | WATCH：转换证据，检查旧极值测试 | — | [高潮和状态转换](../core/01_market_cycle/04_climax_and_transition.md) | 16、29 | 45–46、49 |
| R16 | trading range（成熟） | — | 边缘突破失败，重新入区 | 足够 | — | STRATEGY：[区间/边缘确认 fade](range/edge_fade_confirmed.md)（含失败突破回归子型） | [交易区间 Fade Setup](../core/05_setups/03_trading_range_fade.md) | [交易区间](../core/01_market_cycle/02_trading_ranges.md) | 18、47 | 47、49 |
| R17 | trading range（成熟） | — | 边缘测试（LOM 环境） | 足够 | — | STRATEGY：[区间/限价探针与预设加仓](range/edge_fade_limit_scalein.md) | [交易区间 Fade Setup](../core/05_setups/03_trading_range_fade.md) | [限价单市场](../core/03_acceptance_and_order_logic/02_limit_order_market.md) | 18D–18E、35 | 47 |
| R18 | trading range（成熟） | — | 边缘 H2/L2 指向区间内部 | 足够 | — | STRATEGY：[区间/边缘第二次信号](range/edge_second_signal.md) | [交易区间 Fade Setup](../core/05_setups/03_trading_range_fade.md) | [交易区间](../core/01_market_cycle/02_trading_ranges.md) | 09、18 | 47 |
| R19 | trading range（成熟） | — | 边缘真空快冲，未获接受 | 足够 | — | STRATEGY：[区间/失败突破回归](range/failed_breakout_return.md)（真空 fade） | [交易区间 Fade Setup](../core/05_setups/03_trading_range_fade.md) | [支撑阻力与目标](../core/02_context/01_support_resistance_targets.md) | 18、19 | 47、49 |
| R20 | trading range（成熟） | — | 强 breakout + follow-through 或连续强收盘，无回踩 | 足够 | — | STRATEGY：[突破/收盘跟随（确认版）](breakout/buy_sell_the_close.md) | [突破延续 Setup](../core/05_setups/02_breakout_continuation.md) | [突破和突破模式](../core/01_market_cycle/03_breakouts_and_breakout_mode.md) | 15、18、41 | 47、49 |
| R21 | trading range（成熟） | — | 强 breakout + follow-through 后回踩守住 | 足够 | — | STRATEGY：[突破/突破回踩](breakout/breakout_pullback_test.md) | [突破延续 Setup](../core/05_setups/02_breakout_continuation.md) | [突破和突破模式](../core/01_market_cycle/03_breakouts_and_breakout_mode.md) | 15、18 | 47、49 |
| R22 | trading range（成熟） | — | 突破获接受 | 不足 | — | NO_TRADE：量度空间不足/前方障碍压缩回报（G01 示例） | — | [支撑阻力与目标](../core/02_context/01_support_resistance_targets.md) | 19、20、31 | 47 |
| R23 | trading range（成熟） | — | 区间中部 | — | — | NO_TRADE：中部无优势 | — | [交易区间](../core/01_market_cycle/02_trading_ranges.md) | 18 | 47 |
| R24 | trading range（成熟） | — | 仍处于 barbwire 内 | — | — | NO_TRADE：信号质量低，等待脱离 | — | [交易区间](../core/01_market_cycle/02_trading_ranges.md) | 18 | 47 |
| R25 | trading range（成熟） | — | barbwire 脱离并获接受 | 足够 | — | STRATEGY（依接受证据二次判定）：[收盘跟随确认版](breakout/buy_sell_the_close.md)（无回踩）/[突破回踩](breakout/breakout_pullback_test.md)（回踩守住） | [突破延续 Setup](../core/05_setups/02_breakout_continuation.md) | [交易区间](../core/01_market_cycle/02_trading_ranges.md) | 18、47 | 47 |
| R26 | 任意 | BOM（压缩或非压缩双向候选） | 方向未决 | — | —（任意时段） | STRATEGY：[双向突破模式](breakout/breakout_mode.md)（可准备两套计划；未表态前不下单） | [突破延续 Setup](../core/05_setups/02_breakout_continuation.md) | [突破和突破模式](../core/01_market_cycle/03_breakouts_and_breakout_mode.md) | 15、26、47 | 47、49 |
| R27 | 任意 | — | 初始方向在已知位置失去接受，底层 premise 证据不足 | — | opening | WATCH：等待足以判定底层 premise 的新证据；证据足以分类时路由到 range fade / MTR / minor scalp 对应家族行 | — | [周期与时段 Context](../core/02_context/02_time_and_timeframes.md) | 48E | 48I–48K、49 |
| R28 | 任意 | — | 任意 | — | late | NO_TRADE（候选级）：拒绝剩余时间不足的当前计划；其他已独立建立且时间足够的候选继续进入 PSEL，全部候选均被拒绝时才形成全局 NO_TRADE | — | [周期与时段 Context](../core/02_context/02_time_and_timeframes.md) | 48I–48K | 49 |
| R29 | trend | transition | 通道/趋势线破坏（证据有时效） | — | — | WATCH：结构破坏证据，等待旧极值测试 | [主要趋势反转](../core/05_setups/04_major_trend_reversal.md) | [市场周期](../core/01_market_cycle/00_market_cycle.md) | 21–22、27 | 38–39、49 |
| R30 | trend | transition | 通道破坏 → 旧极值测试失败 → 反向触发（breakout 前） | 足够 | — | STRATEGY：[反转/MTR 早期版](reversal/mtr_early_and_confirmed.md)（约 40%，2R 基线） | [主要趋势反转](../core/05_setups/04_major_trend_reversal.md) | [市场周期](../core/01_market_cycle/00_market_cycle.md) | 21–22、38–39 | 49 |
| R31 | trend | transition | 通道破坏 → 旧极值测试失败 → 强反向 breakout + follow-through | 足够 | — | STRATEGY：[反转/MTR 确认版](reversal/mtr_early_and_confirmed.md)（约 60%；缺少旧极值测试时按突破延续或反转候选处理，不命名完整 MTR） | [主要趋势反转](../core/05_setups/04_major_trend_reversal.md) | [市场周期](../core/01_market_cycle/00_market_cycle.md) | 21–22、38–39 | 49 |
| R32 | trend 后期 | — | wedge 三推 + 合格逆势触发（完整 MTR 链未成立） | 足够 | — | STRATEGY：[反转/三推楔形反转](reversal/wedge_reversal.md)（逆势修正 scalp；完整链成立时优先按 MTR 处理） | [逆势修正 Scalp](../core/05_setups/05_minor_reversal_scalp.md) | [楔形](../core/04_patterns/03_wedges.md) | 24、27 | 42、49 |
| R33 | trend 晚段 | — | final flag 顺势失败 + 合格逆势触发（完整 MTR 链未成立） | 足够 | — | STRATEGY：[反转/最终旗形反转](reversal/final_flag_reversal.md)（result evidence 后；TBTL 仅预写 runner） | [逆势修正 Scalp](../core/05_setups/05_minor_reversal_scalp.md) | [最终旗形](../core/04_patterns/05_final_flags.md) | 23、40E | 48J、49 |
| R34 | trend | — | 旧极值被重新接受并获跟进，或新持续紧密趋势腿重新建立控制（约 20 根为案例线索，非阈值） | — | — | WATCH：MTR 证据链重置，等待新结构破坏 | [主要趋势反转](../core/05_setups/04_major_trend_reversal.md) | [市场周期](../core/01_market_cycle/00_market_cycle.md) | 22、38 | 49 |
| R35 | 任意 | 模糊状态 | 状态不清（trend/range 不分；含区间形成中/未成熟） | — | — | WATCH：按 core fallback 使用 trading-range 管理假设，等待基础状态成熟；若已能声明双向候选边界，同一快照可并行收集 R26，R35 不得截断它 | — | [市场周期](../core/01_market_cycle/00_market_cycle.md) | 12、37 | 49 |
| R36 | spike | — | 首根足够强的 breakout bar 收盘时，尚无独立 follow-through | 足够 | — | STRATEGY：[突破/收盘跟随（早期版）](breakout/buy_sell_the_close.md)（按早期版概率与方程重算；已过首根收盘后才确认未快速收回的，按当前 entry 重建计划，不能继承早期收盘价） | [突破延续 Setup](../core/05_setups/02_breakout_continuation.md) | [突破和突破模式](../core/01_market_cycle/03_breakouts_and_breakout_mode.md) | 15、18 | 47、49 |
| R37 | spike / tight | — | 回调两次测试近似低位/高位（double bottom/top flag，含 micro） | 足够 | — | STRATEGY：[趋势/双测试旗形](trend/double_flag_continuation.md) | [趋势延续 Setup](../core/05_setups/01_trend_continuation.md) | [双顶、双底和旗形变体](../core/04_patterns/04_double_tops_bottoms.md) | 09、21D、25 | 49 |
| R38 | spike / tight | — | 强趋势首次深回调穿过均线，或长期未触均线后首次触及 | 足够 | — | STRATEGY：[趋势/均线缺口回调](trend/moving_average_gap_bar.md) | [趋势延续 Setup](../core/05_setups/01_trend_continuation.md) | [缺口](../core/04_patterns/07_gaps.md#术语边界) | 11、14 | 43、49 |
| R39 | spike / tight | — | 趋势内三推回调（非趋势后期反转） | 足够 | — | STRATEGY：[趋势/三推楔形回调](trend/wedge_pullback_continuation.md) | [趋势延续 Setup](../core/05_setups/01_trend_continuation.md) | [楔形](../core/04_patterns/03_wedges.md) | 24 | 43、49 |
| R40 | spike / range | — | 首破失败 → 反向失败 → 原方向再次突破获接受 | 足够 | — | STRATEGY：[突破/失败再失败延续](breakout/failed_failure_continuation.md) | [突破延续 Setup](../core/05_setups/02_breakout_continuation.md) | [接受、失望与失败证据](../core/03_acceptance_and_order_logic/01_acceptance_and_failure.md) | 15、18 | 47、49 |
| R41 | 任意 | — | 离开明确声明的 opening-range 边界并获接受 | 足够 | opening | STRATEGY：[突破/开盘区间突破](breakout/opening_range_breakout.md) | [突破延续 Setup](../core/05_setups/02_breakout_continuation.md) | [周期与时段 Context](../core/02_context/02_time_and_timeframes.md) | 48D–48E | 48I–48K、49 |
| R42 | trend 后期 | — | 旧极值两次测试失败 + neckline 突破（完整 MTR 链未成立） | 足够 | — | STRATEGY：[反转/双顶双底逆势修正](reversal/double_top_bottom_reversal.md)（minor scalp；完整 MTR 链成立时改走 R30/R31） | [逆势修正 Scalp](../core/05_setups/05_minor_reversal_scalp.md) | [双顶、双底和旗形变体](../core/04_patterns/04_double_tops_bottoms.md) | 21D、22、25、27 | 38–39、49 |
| R43 | trend 后期 | — | ET 五腿以上 + 第四/五腿反向压力，反向 breakout + follow-through 确认 | 足够 | — | STRATEGY：[反转/扩张三角形 MTR 候选](reversal/expanding_triangle_mtr.md)（确认后交易） | [主要趋势反转](../core/05_setups/04_major_trend_reversal.md) | [Triangles、ii、ioi 和 oo](../core/04_patterns/06_triangles_ii_ioi_oo.md) | 26B、47 | 42、49 |
| R44 | trend | transition | 通道破坏 → 旧极值测试失败，尚无反向触发 | — | — | WATCH：等待反向触发或强反向 breakout（MTR 早期版候选） | [主要趋势反转](../core/05_setups/04_major_trend_reversal.md) | [市场周期](../core/01_market_cycle/00_market_cycle.md) | 21–22 | 38–39、49 |
| R45 | 任意 | BOM | 方向未决 | — | opening | STRATEGY：[双向突破模式](breakout/breakout_mode.md)（R26）+ [Opening BOM 覆盖层](session/opening_bom.md)（R45 叠加，仅增加开盘约束，不改变双向候选逻辑） | [突破延续 Setup](../core/05_setups/02_breakout_continuation.md) | [周期与时段 Context](../core/02_context/02_time_and_timeframes.md) | 48D | 48I–48K、49 |
| R46 | 任意 | — | 开盘后快速形成方向，初始极值保持，首次可交易回调 | 足够 | opening | 覆盖行（不产生独立候选）：STRATEGY 取趋势延续对应页（R01 首次小回调 / R03 收盘跟随 / R47 普通趋势回调，依实际结构与证据）+ [开盘趋势](session/trend_from_open.md)（R46 叠加，仅增加开盘约束，不参与 PSEL 候选） | [趋势延续 Setup](../core/05_setups/01_trend_continuation.md) | [周期与时段 Context](../core/02_context/02_time_and_timeframes.md) | 48A–48C | 48I–48K、49 |
| R47 | trend / channel | — | 普通回调未破坏控制，但不属于已登记命名子型；出现顺势恢复触发 | 足够 | — | STRATEGY：[普通趋势回调延续](trend/pullback_continuation.md)（通用兜底；命名子型成立时使用对应专页） | [趋势延续 Setup](../core/05_setups/01_trend_continuation.md) | [趋势和通道](../core/01_market_cycle/01_trends_and_channels.md) | 14、17、31 | 43–46、49 |
| R48 | trend | transition / 重要位置 | 合格逆势触发，完整 MTR 链未成立，且不属于 wedge/final flag/climax 子型 | 足够 | — | STRATEGY：[通用逆势修正 Scalp](reversal/minor_reversal_scalp.md)（两腿修正或区间；默认 scalp） | [逆势修正 Scalp](../core/05_setups/05_minor_reversal_scalp.md) | [市场周期](../core/01_market_cycle/00_market_cycle.md) | 21、23、27 | 42、49 |

## 状态检查点/管理提示行（不产生独立叶子）

以下行不参与叶子裁决（最终叶子只能是 STRATEGY / WATCH / NO_TRADE）；命中时作为管理提示随对应 STRATEGY 候选保留，单独出现且无合格候选时按 NO_TRADE 处理。

| 行 | 适用语境 | 管理提示 | 引用 STRATEGY 行 |
| --- | --- | --- | --- |
| R09 | tight channel，约 20 根无晚段证据（18C） | 提高晚段风险检查；趋势策略仍可候选，出现高潮/转换证据后降级 | R08、R37–R39 |
| R10 | tight channel，约 20 根 + 晚段证据，无 MTR/宽楔形顶底 | 首逆势约 70% minor，先按 pullback 处理 | R08、R12 |
| R11 | tight channel，晚段五根以上小 K 线微型通道 | 约 70% TBTL / 约 30% 延续（42B 语境，非通用） | R08、R12 |

核心依据：[高潮和状态转换](../core/01_market_cycle/04_climax_and_transition.md)、[趋势和通道](../core/01_market_cycle/01_trends_and_channels.md)。

### 检查点级概念登记（不产生独立叶子）

以下概念已有策略层落地（README 检查点或策略页内），此处登记保证矩阵可检索，不新增叶子：

| 概念 | 落地位置 | 引用行 |
| --- | --- | --- |
| Staircase / shrinking stairs | [趋势 README 状态检查点](trend/README.md) | R01、R08 |
| Trending trading range | [趋势 README 状态检查点](trend/README.md) | R08、R16 |
| 50% 回调参考 | [趋势 README 状态检查点](trend/README.md) | R01、R14 |
| 强区间腿与第二腿陷阱 | [区间 README 回避规则](range/README.md)、[区间内第二次信号](range/edge_second_signal.md) | R18、R19 |
| Surprise 与惯性 | [突破 README 状态检查点](breakout/README.md) | R03、R36 |
| 紧通道 ~20 根寿命线索（18C） | [高潮和状态转换](../core/01_market_cycle/04_climax_and_transition.md)、[趋势 README](trend/README.md) | R09 |
| 晚段微型通道 70% TBTL（42B） | [高潮和状态转换](../core/01_market_cycle/04_climax_and_transition.md) | R11 |
| Pain Trade（行为模型） | [跨情景基线](README.md#跨情景基线全部链接-core不在此重复定义)（接受与失败证据行） | R05、R40 |
| 专家限价卖出（强空头控制中的高位限价，非多数交易者默认方式） | [风险与心理纪律](../core/06_trade_plan_and_management/03_risk_psychology.md)（小仓宽 stop 早期参与）；课程 49A p1080 | R01、R03 |
| 限价空头加仓（弱多头反弹/交易区间腿语境，非强趋势） | [加仓与减仓](../core/06_trade_plan_and_management/02_scaling_in_out.md)（预设 scale-in 层数、全部层总风险与最外侧 stop）；课程 49D p1145–1148 | R16、R17 |
| 小仓宽 stop 分批卖出（强卖压背景，专家变体） | [风险与心理纪律](../core/06_trade_plan_and_management/03_risk_psychology.md)、[加仓与减仓](../core/06_trade_plan_and_management/02_scaling_in_out.md)；课程 38C p84 | R30、R31 |
| 跨周期检查（低周期紧通道 = 高周期强突破，按突破处理） | [周期与时段 Context](../core/02_context/02_time_and_timeframes.md)（多周期分工）；课程 43A p416–417、44A p502 | R08、R03 |
| 紧密通道「永不止损卖出/买入」教学规则（紧通道逆势 stop-entry 被排除） | [趋势和通道](../core/01_market_cycle/01_trends_and_channels.md)（误读清单）；课程 43C p448、44C p536 | R08、R12 |
| 区间日尾盘回测开盘价（opening price 作为 magnet） | [支撑阻力与目标](../core/02_context/01_support_resistance_targets.md)；课程 47D p880–881、48K | R28 |
| 大幅初始突破失败 → 双向大波动扩展全天为区间 | [市场周期](../core/01_market_cycle/00_market_cycle.md)；课程 48A | R35 |
| 尾盘确认-价格交换（越晚确认概率越高、价格/止损/时间更差） | [概率、风险和回报](../core/00_method/01_probability_risk_reward.md)（40–60 思维）；课程 48H | R03、R31 |
| 宽幅通道 60% 趋势交易区间反转与 50% 回调方程（语境概率，不入矩阵概率表） | 课程 45A p588、45E p675、46A p697 | R14 |
| 强突破占比语境（约 10% K 线处于突破阶段、约 5% 属趋势起点） | 课程 41A p264 | R03、R36 |
| 弱空头反转结果（约 40% 真反转 / 约 60% 横盘或继续，语境概率） | 课程 39D p156 | R32、R30 |
| 昨日买入高潮后前两小时约 75% 横盘到下跌（语境概率） | 课程 49D p1161 | R03、R28 |
| H4/H6 双底约 60% 两腿横盘到上涨（语境概率） | 课程 49B p1108–1114 | R37、R26 |

## 完整性声明

本矩阵只证明两件事：

1. 已注册的五个 Setup 家族在「基础状态 × 阶段/叠加 × 结构进度 × 空间 × 时段」的当前词汇组合下，除全局行 G01 外没有未处理的组合；
2. 23 个实际策略页全部在矩阵中直接链接（[量度目标构造](breakout/measured_move_breakout.md) 属目标构造页，明确排除；时段覆盖层页作为约束叠加在叶子上，其中 [Opening BOM 覆盖层](session/opening_bom.md) 以 R45 登记）。

既有 R01–R46 的课程核验列（38–42、43–49）已经课程案例回放验证；验证记录不随本文档维护，可在 git 历史中追溯（`strategy/walkthrough/` 已于 2026-08 移除）。新增 R47–R48 当前完成 Core 命题对齐、边界构造与流程可达性校验，尚未宣称完成独立真实图表回放。本矩阵不宣称覆盖所有未来可能的价格行为交易机会；新增家族或新增证据词汇时，矩阵必须同步扩展。

### 证据输入概念（刻意不入矩阵）

以下概念由 core 定义、策略层按需引用，不作为决策行进入矩阵：K 线几何与角色（[bar types](../core/04_patterns/01_bar_types.md)）、缺口家族术语细节（[gaps](../core/04_patterns/07_gaps.md)，如 body gap、exhaustion gap 的口径差异）、最终日型标签（[周期与时段 Context](../core/02_context/02_time_and_timeframes.md)）、多周期分工（同上）。它们的可交易落点已通过引用它们的策略页与矩阵行覆盖。

## 与决策流程图的关系

[决策流程图](decision_flow.md) 是本矩阵的候选收集投影：opening/session 信息先形成覆盖输出但不替代基础状态；trend 与 trading range 内的适用收集器可以同时产生 STRATEGY、WATCH、硬约束和检查点，再经同家族精度消歧与 PSEL 收敛为 STRATEGY / WATCH / NO_TRADE 三种唯一叶子。状态检查点行 R09–R11 不产生独立叶子；`WATCH` 表示当前快照等待新证据，下一次获得数据时从入口重新运行，图内不保留无限回边。
