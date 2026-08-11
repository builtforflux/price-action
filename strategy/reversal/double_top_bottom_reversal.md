# 双顶双底反转（含头肩）

> **状态：Strategy / Application**
>
> 本文把反转命题实例化为旧极值两次测试失败；它不生成具体订单参数。

## 交易命题

市场第二次测试某个区域失败，说明突破或延续遇到阻力；跌破中间 swing low（双顶 neckline）或突破中间 swing high（双底 neckline）确认的是一次**反转尝试**——旧趋势可能结束，但后续仍可能只是 trading range。

## 情景判定

- 两个测试位于近似价格区域（不要求完全相等）；
- 第二次测试失败；
- 上下文决定家族归属：
  - **趋势后期语境**（趋势/通道后期、旧极值测试失败）属于本页的 MTR 反转命题；
  - **成熟区间顶部/底部语境**属于区间 fade 家族（见 [区间内第二次信号](../range/edge_second_signal.md)），不自动属于本页反转命题；
  - **趋势内回调语境**的双测试是 double top/bottom flag（延续逻辑），见 [双测试旗形延续](../trend/double_flag_continuation.md)。
- 头肩不作为独立形态（课程 27 归约）：其反转含义必须按完整 MTR 骨架核验——趋势线/通道破坏、旧极值测试失败、反方控制转移——不能缩成"右肩 + neckline"。

定义见 [双顶、双底和旗形变体](../../core/04_patterns/04_double_tops_bottoms.md)。

## 触发类别

Neckline 突破确认；确认的是一次反转尝试，不能把单次越界直接写成相反趋势已经确认。

## 失效与失败链

- 已确认的双顶下破失败后，价格重新上穿 neckline 并恢复上涨——保留"先突破、再失败、重新接受"的事件顺序，并可以提出反向量度假设；
- 已确认的双底上破失败后，价格重新下穿 neckline 并恢复下跌，完全镜像；
- 只有价格位于 neckline 哪一侧不能追认失败。

Stop 锚点类别：完整反转结构或 neckline 重新接受边界外。

## 目标与管理

Neckline 突破只确认一次**反转尝试**，后续结果是条件分支而非直接承诺：

- 市场进入 trading range：按区间回归管理；
- 只形成两腿修正：按修正管理；
- 完整 MTR 证据成立：按反向两腿与 swing 管理，TBTL 只描述持有时间；
- 形态高度量度只在清楚结构且方向获接受时加入，实际目标选择回到 [支撑阻力与目标](../../core/02_context/01_support_resistance_targets.md)。

## 常见误读

- 把双测试直接当成反转信号；
- 忽略 neckline 确认或失败链；
- 把 micro double 在 spike 内（one-bar flag）与 flag 末端（reversal setup）的含义混用。

## 相关来源

- [双顶、双底和旗形变体](../../core/04_patterns/04_double_tops_bottoms.md)
- [主要趋势反转](../../core/05_setups/04_major_trend_reversal.md)
- [接受、失望与失败证据](../../core/03_acceptance_and_order_logic/01_acceptance_and_failure.md)
