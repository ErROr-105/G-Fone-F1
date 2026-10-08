# G-Fone F1 — Beta 5 (Engineering Edition)

> 概念。部分规格为设计假设或现有技术的非标准组合。  
> 所有标记为 *（概念）* 的内容需与 ODM 和认证实验室进一步验证。  
> 许可证：CERN-OHL-P v2（硬件）、GPLv3（软件）、CC BY 4.0（文档）。  
> 商业使用需署名。

---

## 这是什么

G-Fone F1 是面向厌倦数据被随意读取之人的隐私智能手机概念。不是产品、不是销售要约、不是生产说明书。只是公开的工程理念，供讨论、批评和改进。

目标受众 — 隐私、可维修性和「无妥协硬件」爱好者。非大众市场。非企业。非俄罗斯市场。

---

## 主要规格

- **SoC：** MediaTek Dimensity 9600 Pro，2 nm，TSMC N2P。2+3+3。LPDDR6 + UFS 5.0。（2026年9月发布）
- **内存：** 16 GB LPDDR6 + 256 GB UFS 4.0（UFS 5.0 视供应情况）。
- **屏幕：** 7 英寸 LTPS IPS QHD。
- **电池：** 5S1P，5 × 2500 mAh，18.5 V，**46.25 Wh**。棱柱形锂聚合物。（5S1P 在无人机/航模中已量产，手机中不常见）
- **充电：** 80 W，效率 ≈ 95%。0–80% ≈ 29 分钟。
- **连接：** 1× nanoSIM + 1× microSD 至 1 TB + eSIM + 蓝牙外接卫星终端。不宣称直接卫星调制解调器。
- **价格：** 3200 欧元（小众旗舰参考价）。

### 为什么 2500 mAh 不是笔误

5S1P = 5 节串联 2500 mAh。电压 18.5 V。能量 46.25 Wh。是 Galaxy S24 Ultra 的 **2.4 倍**。3.7 V 等效 **12500 mAh**。棱柱电芯隔离简单、热接触平坦、BMS 成熟。

### 电源 / PMIC — 更先进控制器的部分集成

经典单电芯手机 PMIC 难以同时适配 **18.5 V（5S1P）** 与 2 nm 旗舰热轨。采用**混合方案**：高压前端 18.5 V → 中间总线；SoC 核心轨部分集成**多相数字 buck 控制器** + power stage；其余域 companion PMIC。系统集成为工程方案（需 ODM、布局、热与 EMC）。

---

## 摄像头

主摄 50 MP Sony IMX907 f/1.4 OIS；长焦 50 MP；超广角 50 MP IMX858；景深 12 MP；自拍 50 MP。无生成式 AI。Zeiss 仅在许可下。相机周围保留 ≥ 7 mm 净空。

---

## 机身与散热

- 铝合金 **7075-T6**，无胶水，全可拆螺栓。
- 防护：无壳 IP69；带壳 IP69K。
- 三层均热板（IceLoop）*（概念）*。
- 鳍片 *（概念）*：12 片梯形，+30–35% 散热面积。
- Anti-Burn：压电 MEMS 微泵。**驱动功率：0.1–0.3 W**。

---

## 独特硬件

**SMD 按钮（Stop Meta Data）**：物理切断摄像头、麦克风、加速度计电源。多模式 RGB。SK6812 IP65 + SMD 4020 RGB IP65。

**彩蛋：Mindustry 加载箭头** — 打开 **Mindustry** 时，在**游戏自身加载画面**期间，灯光（SMD 4020 + SK6812）**复现加载箭头动画**——从水平线中部展开的那些箭头——**光色与画面一致**。与设备开机无关；本地 LED 图案。

---

## 软件

LineageOS 基础，无 GApps。预装 F-Droid、DuckDuckGo、Proton Mail。可选 UnifiedPush。E2EE；eBPF；**FBE**。俄罗斯：官方不供应；RTRCA/SORM 架构不兼容。

---

## 专利风险（摘要）

SEP 5G；Motorola US 12,308,512 B2；US 20250357560 A1；MEMS；LED；SK6812；鳍片；PMIC/multiphase FTO；G-Fone 商标；高通风险。详情 LEGAL.md / PATENTS.md。

---

## Beta 5 状态

可实现 / 量产：2 nm SoC、LPDDR6、UFS 5.0、5S1P、80 W、multiphase/HV 组件、MEMS（0.1–0.3 W）、7075-T6、LineageOS、eBPF、UnifiedPush、FBE、SK6812、SMD 按钮。

概念 / 系统集成：三层 VC、伸缩天线、鳍片、部分先进 PMIC 集成、多模式 LED、**Mindustry 加载箭头 LED 彩蛋**。

许可证：CERN-OHL-P v2 / GPLv3 / CC BY 4.0。

---

## 如何贡献

允许：CAD、热仿真、软件、BMS、电源/PMIC 布局、文档、测试、翻译。禁止规避专利、违法号召、黑名单、政治声明。

---

> **免责声明。** 这是概念。不是产品。规格为设计假设或现有技术组合。未认证。专利风险见 LEGAL.md / PATENTS.md。未做 FTO。作者不承担责任。用户须遵守所在司法管辖区法律。
