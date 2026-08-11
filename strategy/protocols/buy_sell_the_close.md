# 策略决策协议：BTC/STC（收盘跟随）

> **状态：Strategy / Application（Decision Protocol）（文本审阅通过，待回放验收）**
>
> **适用范围**：只处理顺势收盘附近的直接参与；已形成回踩后转入 [突破回踩](../breakout/breakout_pullback_test.md) 的决策协议，不继续使用本卡。

## 1. Must-have（全部成立才进入本卡）

- 清楚旧边界已被越过（前高低、区间边界、趋势线、通道线等）；
- 已有一根完成 K 线收在边界外（早期版）或连续强收盘 / 独立 follow-through（确认版）；
- 完整 breakout leg 的可定义结构 stop；
- 现实 target（第二腿或当时可见的 measured move / magnet）；
- 用该版本实际 entry、stop、target、概率与成本可评估 Trader's Equation。

## 2. 质量证据与反证

**质量证据（综合判断，缺一不自动否定）**：大实体、强收盘、少重叠、少反向影线、surprise、未快速收回——按 core [突破质量](../../core/01_market_cycle/03_breakouts_and_breakout_mode.md) 的证据组合综合判断。

**「首根足够强」的仓库严格操作口径**（仓库为一致执行选定的较严格口径，不重新定义 core 的 breakout）——早期版必须同时确认：

- 清楚边界被越过；
- 完成 K 线收在边界外；
- 实体和收盘相对近期表现出明确方向优势；
- 反向影线 / 重叠没有使突破重新落回双边状态；
- 完整 leg stop 与现实 target 的方程成立。

无法明确确认其中任一项 → WATCH。

**Candidate rejection（尚未入场，本卡不可用）**：
- 价格快速回到旧区域；
- 强反向收盘并获跟进；
- 目标空间被前方障碍封死（方程不成立）。

**Entry expiry（版本过期，不等于 premise 失效）**：
- 首根强 breakout bar 收盘时点已过 → 早期版不可追认，不得以「后来确认未快速收回」继承早期入场价（回踩后的归属见文末独立节）。

## 3. 版本选择（唯一）

- 首根足够强 breakout bar 收盘、尚无独立 follow-through → **早期版**（接受证据仍在累积，不要求已获接受）；
- 连续强收盘或独立 follow-through 已出现 → **确认版**；
- 两者都不满足 → 不参与（WATCH）。

## 4. Entry-Stop 绑定

- 早期版：**完整 breakout leg 外**（按早期时点可见的 leg 定义）；
- 确认版：**按确认时重新计算的完整 breakout leg 外**；不继承早期收盘价；
- 回踩后重新触发 → 离开本卡，进入 breakout-pullback 卡（其 stop 才绑定回踩 swing）；
- 不借用尚未出现的回踩结构或新趋势 major HL/LH。

## 5. 目标优先级

**管理版本选择（先于目标绑定，唯一）**：

- **没有可行 swing 计划**（结构不清楚，或近端障碍使 swing 方程不成立），但近端 magnet 的 scalp 方程成立 → **Scalp**；
- **有可行 swing 计划，且近端 magnet 不构成实质路径障碍** → **Swing**；
- **Scalp 与 Swing 两个子计划各自方程成立；近端 magnet 构成实质路径障碍并显著降低远端到达概率，但尚未使 swing 方程转负；数量、target、管理已预先拆分** → **预写分仓**；
- 其余 → WATCH / NO_TRADE。

关键判据是「**有没有可行 swing 计划**」，不是「图上有没有 swing 结构」——swing 结构存在但方程被近端障碍否定时，可行 scalp 不应被排除。

三条互斥（不重叠）：Swing 方程不可行而 Scalp 可行 → Scalp；Swing 方程可行且近端 magnet 不构成实质障碍 → Swing；两子计划均可行且近端 magnet 构成实质障碍但未使 swing 方程转负 → 预写分仓。

选定管理版本后，entry、target、仓位与退出规则全部绑定该版本：

- **Scalp 计划** → 采用路径上最近的现实 magnet；
- **Swing 计划** → 只有存在清楚的第二腿 / 量度结构且前方障碍不封闭时，才采用该结构目标；
- **预写分仓** → 每份各自绑定 target 与管理分支（部分止盈触发事件入场前写明）。

由当前版本完整 Trader's Equation 判断，**不设统一 1R 门槛**。

## 6. 管理分支

- **转入 channel / climax candidate / transition**：停止继续机械 BTC，重新判断当前阶段——**不自动退出已有仓位**（spike 首次回调后进入 channel 是正常趋势演化，不表示趋势结束）；
- **正常回调进入 channel**：按原计划管理已有仓位；新的入场转到趋势或 pullback 策略；
- **Premise invalidation（唯一定义，任一成立即触发）**：
  1. 价格明确回到旧区域并获得反向跟进；
  2. 在预先声明的管理周期上出现足以否定原接受结构的强反向突破与跟进；
  3. 同一管理周期的 Always In 明确翻转，并且该翻转否定原突破延续 premise。
  触发后：**全部依赖 BTC premise 的仓位主动退出**；结构 protective stop 在仓位归零前继续有效。后续管理条目只引用本定义，不重复条件。

  第 2、3 条的图形边界在回放中校准（不设机械参数），至少区分：强反向突破 + 跟进 → 退出；强反向 K 线但无跟进 → 不退出；正常 pullback 进入 channel → 不退出。
- **Active exit 预写**：
  - 属正常波动的反向收盘：普通回踩、单根反向 K 线——不触发退出；
  - 要求主动退出的情形：即上方 **Premise invalidation** 任一条件成立——在结构 stop 前主动退出，此处不重复定义；
  - Always In 翻转采用的管理周期：以本仓 entry 与 stop 所在的交易周期为准，不切换到更低周期寻找退出理由；翻转是否构成 premise 失效按上方第 3 条判断；
  - scalp / swing 退出边界（按可观察事件区分）：
    - 单根普通反向 K 线：正常波动，不退出；
    - 反向 signal 尚未触发：正常波动，不退出；
    - Premise invalidation 任一条件成立：**全部退出**（见上方唯一定义）；
    - **提前结构退出分支（当前关闭）**：尚无经案例验证的 BTC 提前结构退出；当前不使用该分支，只使用预写 target、明确 premise invalidation 与 active protective stop。未来验证出具体结构后加入协议白名单（含镜像触发：多仓跌破合格空头 signal bar 低点 / 空仓突破合格多头 signal bar 高点，signal bar 质量服从 context），**不允许交易者临场自定义**；
  - 部分退出：仅当入场前选择「预写分仓」版本时允许；触发只允许**预写 target 或 premise 削弱证据**；**premise 失效触发全部退出**。**BTC runner 必须继续依赖同一 BTC premise**，使用本卡预写的 swing target、stop 与管理；若后续持仓需要依赖 breakout-pullback、趋势延续、MTR 或其他新 premise，**不得把原 BTC 仓位临场改名**——原计划按自身规则结束，新 premise 出现独立触发后建立新的 Trade Plan。每份的数量、target 与触发事件必须入场前写明。

**Premise 削弱证据（可观察组合，允许预写分支减仓）**：以下组合同时成立——

- 外部价格尚未被旧区域重新接受（premise 尚未失效）；
- 顺势 K 线持续缩小，或关键顺势收盘失去跟进，或影线与重叠增加；
- 反方 K 线增加但尚未形成强反向突破与跟进。

无法确认该组合时，不触发部分减仓——只允许到预写 target 部分退出、premise 失效全部退出、active protective stop 保护。

## 7. 跨 premise 禁借

- 概率：本卡**不引用 MTR 的约 40%/60%**（那是 [MTR 早期与确认两版本](../reversal/mtr_early_and_confirmed.md) 的风险承担时点语境，不是 BTC/STC 的统一概率）；
- 参数：不借用 breakout-pullback 或趋势延续的 stop / target；
- 市场事实继续监控，但只有本卡第 6 块预写的证据才能改变本仓管理。

## 版本过期与回踩后的归属

- 尚未入场且已出现回踩 → 本卡不可用，转入「突破回踩协议」（待建）重新评估；
- 已有持仓 → 仍按本卡第 6 块与入场前锁定的 Trade Plan 管理，不因首次回调切换协议。

## 案例验收（试点通过前不批量复制）

| 案例 | 预期结果 | 状态 |
| --- | --- | --- |
| 正例：早期版 | 首根强 bar 收盘、无独立 follow-through、五条严格口径全满足 → 早期版 + 完整 leg stop + 管理版本选择 | 待回放 |
| 正例：确认版 | 连续强收盘或独立 follow-through 已出现 → 确认版，stop/target 按确认时重算 | 待回放 |
| 近似反例 | 突破 K 很大但收盘 / 重叠质量不足（严格口径第 3–4 条不满足）→ WATCH | 待回放 |
| 管理例 | 正常回调进入 channel → 不退出，按原计划管理；新入场转趋势/pullback 策略 | 待回放 |
| 失效例 | 旧区域被重新接受并获反向跟进 → premise 失效，主动退出 | 待回放 |
| 过期例 | 尚未入场已出现回踩 → 本卡不可用，转 breakout-pullback 重新评估 | 待回放 |
| 管理例：Scalp | 没有可行 swing 计划（结构不清楚或 swing 方程不成立）、近端 magnet 的 scalp 方程成立 → Scalp + 最近 magnet target | 待回放 |
| 管理例：Swing | 清楚 swing 结构且近端 magnet 不构成实质障碍 → Swing + 结构目标 | 待回放 |
| 管理例：预写分仓 | 近端 magnet 显著影响远端概率、两套方程均成立且数量已拆分 → 预写分仓 | 待回放 |
| 管理例：swing 方程被否定 | 有 swing 结构但近端障碍使 swing 方程不成立、scalp 方程成立 → Scalp（不被错误排除） | 待回放 |
| 削弱例：momentum 削弱 | 顺势 K 线缩小 / 跟进丢失 + 反方 K 线增加但未形成强反向突破 + 旧区域尚未重新接受（完整削弱组合）→ 允许预写分支减仓，不触发全部退出 | 待回放 |
| 正常波动例：无跟进反向 signal | 单个普通反向 signal 触发但无跟进：不单独构成 premise 失效；若同时满足完整削弱组合则按削弱处理，否则视为正常波动 | 待回放 |
| 失效例：全部退出 | 强反向突破 + 跟进 → premise 失效，**全部退出而非只减仓** | 待回放 |

## 相关来源

- [突破和突破模式](../../core/01_market_cycle/03_breakouts_and_breakout_mode.md#buy--sell-the-close)
- [突破延续 Setup](../../core/05_setups/02_breakout_continuation.md)
- [策略页：收盘跟随](../breakout/buy_sell_the_close.md)
