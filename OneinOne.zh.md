# G-Fone F1 — Beta 6.3.5 (Engineering Edition)

> 概念。部分规格为设计假设。许可证：CERN-OHL-P v2 / 内核 GPLv2-only / 用户态 GPLv3 / Lineage Apache 2.0 / CC BY 4.0。

## 这是什么
隐私向智能手机概念。非产品、非要约、非量产指南。

## 主要规格

- **SoC：** Dimensity 9600 Pro，2 nm。LPDDR6 + UFS 5.0。
- **屏幕：** 6.77 英寸 LTPS IPS QHD。
- **电池：** 5S1P，46.25 Wh。**X-Cross**；BMS **主动均衡**；分流器 + 每节 NTC。
- **充电：** 80 W。**18.5 V（5S1P）**，非 3.7 V 单电芯。滤波电感在**手机内**。
- **连接 / 卡槽：** **无机械 SIM、microSD 卡槽**。蜂窝 **仅 eSIM**（最多 2 个配置 — 视 ODM）。
- **外置存储：** USB host（USB-C），**任意容量** HDD/SSD/U 盘。
- **包装内：** **USB → SATA 转接器（带供电）** — 2.5″/3.5″ SATA。
- **机身：** 7075-T6；钢环磁吸主动散热。
- **散热面板：** **通风纹理**（定向微通道，增强自然对流；非 Junon 式通孔）。

## BMS
主动均衡为基线。被动 bleed 会局部过热且效率更低。监测：每节电压、每节 NTC、包电流分流器。

## Beta 6.3.5 状态
取消机械 SIM/SD；仅 eSIM；外置盘任意容量；包装内 USB→SATA+供电。（继承 6.3.4：分流器 + NTC）

> **免责声明。** 这是概念。不是产品。
