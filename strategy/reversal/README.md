# 反转情景

> **状态：Strategy / Index**
>
> 本页说明反转情景下各策略命题的职责与文件入口。

## 情景判定

反转情景包含两个强度不同的可交易家族：

1. **MTR（swing 命题）**：完整过程——成熟趋势 → 通道/趋势线破坏 → 对旧极值的测试失败 → 反方重新获得控制并建立可持续 swing。Climax、wedge、final flag 或单根强反转 bar 只能提供 Context，不能替代这组过程。
2. **逆势修正（minor scalp 命题）**：趋势后期的 wedge、final flag、climax 之后的首次反向运动通常只是 minor reversal、两腿修正或 trading range；逆势方按短线（scalp）交易。期待 MTR 仅限入场前预写 runner 分支，否则原 scalp 退出后按新 MTR 触发建立新计划。家族边界见 [逆势修正 Scalp](../../core/05_setups/05_minor_reversal_scalp.md)。

完整定义见 [市场周期](../../core/01_market_cycle/00_market_cycle.md#reversal-与-minor-reversal) 与 [主要趋势反转](../../core/05_setups/04_major_trend_reversal.md)。

## 策略页

| 策略 | 家族归属 | 直接预期 |
| --- | --- | --- |
| [MTR 早期与确认两版本](mtr_early_and_confirmed.md) | MTR 家族（swing） | 反向两腿 + swing |
| [扩张三角形 MTR 候选](expanding_triangle_mtr.md) | MTR 家族（候选，确认后交易） | 反向两腿（确认后） |
| [通用逆势修正 Scalp](minor_reversal_scalp.md) | 逆势修正家族（不属于下列命名子型时的兜底） | 两腿修正或区间 |
| [双顶双底逆势修正](double_top_bottom_reversal.md) | 逆势修正家族（完整 MTR 链未成立；完整链转 MTR） | neckline 确认后的两腿修正或区间 |
| [三推楔形反转](wedge_reversal.md) | 逆势修正家族（scalp） | 两腿修正或区间；升级需完整 MTR 链 |
| [最终旗形反转](final_flag_reversal.md) | 逆势修正家族（scalp） | 两腿修正或区间；升级需完整 MTR 链 |
| [高潮后修正](climax_correction.md) | 逆势修正家族（scalp） | 两腿修正或区间回归 |

命名子型成立时使用对应专页；重要位置的 reversal / two-bar reversal、micro double、非 wedge 第二信号或普通趋势线破坏后只期待短线修正时，由[通用逆势修正](minor_reversal_scalp.md)承接。双顶/双底只有在完整 MTR 链成立时才作为 MTR 结构证据；不足以构成 MTR 时按 minor scalp。兜底页不能替代完整 MTR，也不能为缺少位置和接受证据的第一根反色 K 线提供许可。

## 状态检查点（约束，不构成独立策略页）

- **Minor vs Major**：第一次逆势反转通常先按 minor 处理，按逆势修正家族做短线；只有完整 MTR 证据链成立才升级为 MTR swing。紧通道（且没有清楚 MTR 或宽楔形顶/底）中第一次逆势反转约 70% 是 minor。
- **Endless pullback 降级**：约 20 根以上的长回调（endless pullback）中，原方向恢复与反向突破的条件先验可能接近 50/50（课程语境，非机械阈值）；停止机械沿用普通短回调假设，按实际证据重新归类为长回调、反向通道、trading range 或 breakout mode，反向 breakout 和 follow-through 建立持续控制后才更新为 opposite trend。
- **证据链重置**：原趋势随后以新的持续紧密趋势腿重新建立控制时，旧的趋势线破坏和旧极值测试不能永久借给后来的 MTR；反转序列应重置。
- **两组 40/60 分母**：MTR 结果分类（约 60% 只成 minor reversal、40% 成 swing）与入场时点交换（突破前约 40%、确认后约 60%）是两组不同概率，不能互相替换。

## 相关来源

- [主要趋势反转](../../core/05_setups/04_major_trend_reversal.md)
- [市场周期](../../core/01_market_cycle/00_market_cycle.md)
- [高潮和状态转换](../../core/01_market_cycle/04_climax_and_transition.md)
- [Scalp 与 Swing](../../core/06_trade_plan_and_management/01_scalp_vs_swing.md)
