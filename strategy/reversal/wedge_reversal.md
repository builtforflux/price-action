# 三推楔形反转（Wedge Reversal / Parabolic Wedge）

> **状态：Strategy / Application**
>
> 本文把逆势修正家族实例化为趋势后期三推结构；它不生成具体订单参数。

## 交易命题

趋势或通道后期出现三次推动后，反方尝试反转；按 minor reversal 先处理：逆势 scalp 期待两腿修正或进入 trading range。紧通道中至少三腿或三次 surge 构成的 climactic 加速形态称 parabolic wedge。

## 情景判定

- 确有至少三次可区分的推进；仍属于趋势/通道后期，接近重要位置或呈现高潮式推进；
- 反方获得 signal、micro double、趋势线突破或 follow-through 等候选证据；
- 反转尝试在重要位置（均线、旧公平区域、前 swing）获得暂时支撑或接受；
- 到两腿修正目标或区间边缘有现实空间；
- 只有三推而没有反向证据，仍可能只是强趋势继续。

## 触发类别

- 反向 signal、micro double、趋势线突破后的 higher low / lower high 测试构成候选证据；强度不足时等待第二信号；
- 强反向 breakout 可加强 MTR 候选；只有完整 MTR 链（趋势线/通道破坏、旧极值测试失败、反方控制转移）同时成立才转入 MTR 家族；
- 首次逆势交易经常失败，尤其在趋势仍强、没有结构破坏、没有回探失败时。

## 失效与 Stop 锚点

- 强趋势继续形成第二腿；
- 三推结构极值被反向接受；
- 原趋势以强 breakout 和 follow-through 恢复控制。

Premise 失效可在结构 stop 触发前主动退出（强反向动量或 Always In 翻转即可要求退出），不等待触及 stop。

Stop 锚点类别：完整三推结构极值外，或能否定"逆势尝试仍有效"的位置外。

## 目标与管理

- 直接预期：两腿修正或进入 trading range；TBTL 是条件性的路径/持有预期，不是最低结构或价格目标；默认 scalp 的实际目标仍是附近现实 magnet（均线、前 swing、旧公平区域、区间边缘）；
- 升级 MTR 只走两条合法路径：入场前预写 runner 分支（scalp 与 MTR runner 分开管理），或原 scalp 退出后按新 MTR 触发建立新 Trade Plan；升级后按 [MTR 早期与确认两版本](mtr_early_and_confirmed.md) 管理；
- Parabolic wedge 后的第一笔反向运动常只是 minor reversal、两腿修正或 trading range，不能因形态名称直接期待完整反向趋势。

## 语境先验

- 紧通道（且没有清楚 MTR 或宽楔形顶/底）第一次逆势反转约 70% 是 minor；
- "下一次反转约 40% 成为主要反转"分母不明确，不作为概率先验（见 [边界与冲突](../../reference/course/boundaries_and_conflicts.md)）；
- Wedge 方向倾向只在突破前且 Context 支持时有效；突破后按突破质量重新评估。

## 常见误读

- 把 wedge 反转直接当 MTR 交易；
- 三推后第一根反向 K 直接命名 MTR；
- 趋势仍强时无条件逆势。

## 相关来源

- [逆势修正 Scalp](../../core/05_setups/05_minor_reversal_scalp.md)
- [楔形](../../core/04_patterns/03_wedges.md)
- [主要趋势反转](../../core/05_setups/04_major_trend_reversal.md)
- [三推楔形回调延续](../trend/wedge_pullback_continuation.md)（同一三推结构的顺势解释边界）
