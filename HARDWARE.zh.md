# HARDWARE

## 主要规格
- **SoC：** MediaTek Dimensity 9600 Pro，2 nm，TSMC N2P。2+3+3。LPDDR6 + UFS 5.0。（2026年9月发布）
- **内存：** 16 GB LPDDR6 + 256 GB UFS 4.0（UFS 5.0 视供应情况）。
- **屏幕：** 6.77 英寸 LTPS IPS QHD，高端。
- **电池：** 5S1P，5 × 2500 mAh，18.5 V，46.25 Wh。棱柱形锂聚合物。**X-Cross** 固定。Battery Board：BMS + **被动均衡**（主动可选）。
- **充电 / 电源路径：** 80 W，效率 ≈ 95%。充电与 power path 按 **18.5 V（5S1P）** 设计，而非经典 **3.7 V** 单电芯。
- **防护：** IP69 / IP69K（带保护壳）。
- **机身：** 7075-T6 铝合金，无胶水设计。机身内有小型**钢环**，用于**磁吸主动散热**（可拆卸 cooler）。

## 为什么 2500 mAh 不是笔误？
5S1P 提供 46.25 Wh。约为 Galaxy S24（典型容量 4000 mAh，官方 15.52 Wh）的 ≈3 倍（精确 2.9800257731958×）。在 3.7 V 下相当于 12500 mAh。

## X-Cross
**X-Cross** 是内部金属十字形零件，用于在 Battery Board 上固定 5S1P 棱柱电芯。

## 包级 PTC（pack-level）
- **Pack 级 PTC 膜**（低温保护）。5S1P 不宜 cell-level。

## BMS 与电芯均衡（5S1P）
- **被动均衡**为必需基线；**主动**为可选高端。每节 V/T；OV/UV/OT/OC。包级 PTC ≠ 均衡。

## 电源 / PMIC（部分集成）
- **高压前端（5S1P → 总线）：** 18.5 V → 中间总线（约 5–9 V）；80 W 充电与 BMS 独立路径。
- **滤波电感（choke）：** 位于**手机内**（不在外部电源适配器）—— charge path 入口和/或 HV step-down 之后的 LC/滤波；适配器为 80 W 源，滤波电感在机内板上。
- **SoC 核心轨：** 部分集成 multiphase digital buck；其余轨 companion PMIC。

## 摄像头
主摄 50 MP Sony IMX903；长焦 50 MP；超广角 50 MP IMX858；景深 12 MP；自拍 50 MP。无生成式 AI。

## 散热
- **磁吸主动散热：** 机身内小型**钢环**；可拆卸 cooler 磁吸固定。
- 三层均热板 *（概念）*、鳍片 *（概念）*。
- **xMEMS Lab XMC-2400：** 3 V，30 mW / 含驱动 70 mW。

## 附件与保护壳
织物指套；边框壳 + 硅胶镜头盖。
