# 逆势修正 Scalp（Minor Reversal / Two-Leg Correction）

> **状态：Core / Application**
>
> 本文界定逆势修正家族与 MTR 的边界、抽象触发类别、特有失效和直接结果预期；它不能直接生成订单计划。

## 交易命题

逆着既有趋势的第一次反转通常先按 minor 处理：逆势方可做短线（scalp），期待两腿修正或先进入 trading range；顺势方则等待旗形结束后恢复原趋势。

以空头趋势中做多为例，多头趋势中做空完全镜像：

```text
既有空头趋势 -> 第一次可交易的反转尝试（如 wedge 底 / final flag 失败 / 高潮后修正）
           -> 尝试在重要位置获得暂时支撑或接受
           -> 逆势触发
           -> 两腿修正或进入 trading range（默认 scalp）
```

## 与 MTR 的边界

- Minor reversal 是当前周期中逆着既有趋势、但尚未建立相反趋势控制的反转尝试；状态定义见[市场周期](../01_market_cycle/00_market_cycle.md#reversal-与-minor-reversal)。
- MTR 要求成熟趋势失去控制：通道/趋势线破坏、旧极值测试失败、反方建立可持续 swing。课程保守默认每次反转先按 minor 处理；只有后续出现完整 MTR 证据链时才升级。
- 两族不是互斥的两笔交易，但升级必须走合法路径，不能临场把 scalp 改成 swing：
  1. **入场前预写 runner 分支**：在 Trade Plan 中把 scalp 部分与 MTR runner 分成两个管理分支（各自 stop、target 与数量预算）；
  2. **退出后重新入场**：原 scalp 按计划退出后，若出现完整 MTR 触发，建立新的 Trade Plan 再入场。

## 成立条件

- 原趋势仍存在但出现第一次可交易的反转尝试；趋势强到没有结构破坏、没有回探失败时，第一笔逆势交易经常失败；
- 反转尝试在重要位置（旧公平区域、均线、前 swing、区间边缘）获得暂时支撑或接受证据；
- 前方有到两腿修正目标或区间边缘的现实空间；
- 合理 stop 可放在尝试结构外，并满足 Trader's Equation。

## 触发类别

- 沿逆势修正方向的 stop entry 触发：逆势多单用 buy stop 越过反转尝试 signal bar 高点，逆势空单用 sell stop 越过其低点；
- 第二次信号（首次反转尝试缺乏延伸后再次出现）常比首次更可靠；
- 强背景中满足 [Context 三条例外判据](../02_context/00_context_location_control.md#always-in-是强控制判断)的单根强反转 K 线可以直接翻转 Always In，但一般情形仍等待确认。

## Premise 失效与 Stop 差异

Premise 失效与 protective stop 是两层，不能合并：

- **Premise 失效（可在结构 stop 触发前主动退出）**：在预写 scalp target 或修正目标实现前，原趋势以强 breakout、follow-through 或 Always In 翻转重新建立控制时，即使尚未触及尝试结构极值，也可能已经要求退出；逆势多单尝试低点被向下有效突破、逆势空单尝试高点被向上有效突破，同样使 premise 失效。
- **Stop 锚点**：逆势多单在反转尝试低点外，逆势空单在尝试高点外。合理 stop 更远时应调整仓位或放弃，不把 stop 塞进普通回调。

目标已实现后原趋势恢复，不追认为原交易失败。

## 结果与目标差异

- 直接预期：两腿修正或进入 trading range；TBTL 是条件性的路径/持有预期，不是最低结构或价格目标（权威定义见[Scalp 与 Swing](../06_trade_plan_and_management/01_scalp_vs_swing.md#tbtl-是时间与腿数预期)）；
- 默认 scalp 的实际目标仍是附近现实 magnet（均线、前 swing、旧公平区域、区间边缘）；只有预先设计的 runner 分支才引用 TBTL 描述持有时间；
- 升级 MTR 只走上方两条合法路径，升级后按[主要趋势反转](04_major_trend_reversal.md)管理；
- 课程对“下一次反转约 40% 成为主要反转”给出经验说法，但分母不明确，因此不作为概率先验进入本页；具体来源和口径冲突见[边界与冲突台账](../../reference/course/boundaries_and_conflicts.md)。

## 主要误读

- 把 minor 直接当 MTR 交易，或把 MTR 的结果预期套给 minor scalp；
- 趋势仍强、没有失败证据时无条件逆势；
- 脱离课程上下文，把“look for scalp, but sometimes get a swing profit”当成 minor reversal 与 MTR 的无差别规则；该表述的来源冲突不改变本页的家族边界。
- 用事后确认的 minor 标签反向制造当时不存在的交易许可。

## 相关来源

相关来源见[正式来源台账](../../reference/official_sources.md)中的 `SRC-COURSE-01-36`（课程 21A p1780–1785、21C p1828、21D p1851–1854、23B p1961、24D p2040 与 24E p2071）与 `SRC-MTR-2025`；课程归约见[课程综合与 Core 对齐](../../reference/course/course_to_core_alignment.md)，概率分母冲突见[边界与冲突](../../reference/course/boundaries_and_conflicts.md)。
