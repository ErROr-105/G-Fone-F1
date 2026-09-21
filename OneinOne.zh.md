# G-Fone F1 — Beta 4 (Engineering Edition)

> 概念。部分规格为设计假设，非已确认的量产组件。  
> 所有标记为 *（概念）* 的内容需与 ODM、SoC 供应商和认证实验室验证。  
> 许可证：CERN-OHL-P v2（硬件）、GPLv3（软件）、CC BY 4.0（文档）。  
> 商业使用需署名。

---

## 这是什么

G-Fone F1 是面向厌倦数据被随意读取之人的隐私智能手机概念。不是产品、不是销售要约、不是生产说明书。只是公开的工程理念，供讨论、批评和改进。

目标受众 — 隐私、可维修性和「无妥协硬件」爱好者。非大众市场。非企业。非俄罗斯市场。

---

## 主要规格

- **SoC *（概念）*：** MediaTek Dimensity 9600 Pro，2 nm，TSMC N2P。2+3+3。LPDDR6 + UFS 5.0。
- **内存 *（概念）*：** 16 GB LPDDR6 + 256 GB UFS 4.0。
- **屏幕：** 7 英寸 LTPS IPS QHD。
- **电池：** 5S1P，5 × 2500 mAh，18.5 V，**46.25 Wh**。棱柱形锂聚合物。
- **充电：** 80 W，效率 ≈ 95%。0–80% ≈ 29 分钟。
- **连接：** 1× nanoSIM + 1× microSD 至 1 TB + eSIM + 蓝牙外接卫星终端。不宣称直接卫星调制解调器。
- **价格：** 3200 欧元（小众旗舰参考价）。

### 为什么 2500 mAh 不是笔误

5S1P = 5 节串联 2500 mAh。电压 18.5 V。能量 46.25 Wh。是 Galaxy S24 Ultra 的 **2.4 倍**。3.7 V 等效 **12500 mAh**。棱柱电芯隔离简单、热接触平坦、BMS 成熟。

---

## 摄像头

主摄 50 MP Sony IMX907 f/1.4 OIS；长焦 50 MP；超广角 50 MP IMX858；景深 12 MP；自拍 50 MP。无生成式 AI。Zeiss 仅在许可下。相机周围保留 ≥ 7 mm 净空。

---

## 机身与散热

- 铝合金 **7075-T6**，无胶水，全可拆螺栓。
- 防护：无壳 IP69；带壳 IP69K。
- 三层均热板（IceLoop）。
- 鳍片 *（概念）*：12 片梯形，+30–35% 散热面积。
- Anti-Burn *（概念）*：压电 MEMS 微泵，均衡温度梯度，表面峰值降低 5–8 °C。

---

## 独特硬件

**SMD 按钮（Stop Meta Data）**：物理切断摄像头、麦克风、加速度计电源。多模式 RGB 指示（隐私红 / 充电白→黄→绿 / 温度青绿→黄→橙→红）。SK6812 IP65 装饰线条 + SMD 4020 RGB IP65 按钮。

---

## 软件

LineageOS 基础，无 GApps。预装 F-Droid、DuckDuckGo、Proton Mail。Aurora Store 不预装。可选 UnifiedPush 网关。E2EE：X25519 + AES-256-GCM / ChaCha20-Poly1305，密钥在 TEE。eBPF 过滤器作为用户隐私工具。

俄罗斯：官方不供应。RTRCA / SORM 因架构不兼容而不适用。

---

## 专利风险（摘要）

SEP 5G 10–15% 零售价；Motorola US 12,308,512 B2（伸缩天线）；US 20250357560 A1（5S1P）；MEMS 冷却；LED 按钮照明；SK6812；机身鳍片；G-Fone 商标；高通风险（即使使用 MediaTek SoC）。详情见 LEGAL.md 和 PATENTS.md。

---

## Beta 4 状态

可实现：机身、可拆盖、VC、鳍片、阳极氧化 Type III + 石墨烯、LineageOS、eBPF、UnifiedPush、FDE、SK6812、SMD 按钮。

概念：2 nm SoC、LPDDR6、UFS 5.0、5S1P 18.5 V、80 W、三层 VC、伸缩天线、MEMS 微泵、多模式 LED。

许可证：CERN-OHL-P v2 / GPLv3 / CC BY 4.0。

---

## 如何贡献

允许：CAD、热仿真、软件、BMS、文档、测试、翻译。  
禁止：规避专利建议、违法号召、黑名单、政治声明。  
贡献许可依类型适用 CERN-OHL-P v2 / GPLv3 / CC BY 4.0。

---

> **免责声明。** 这是概念。不是产品。不是销售要约。不是生产说明书。所有规格为设计假设。设备未经认证。专利风险见 LEGAL.md 和 PATENTS.md。未进行 FTO 审计。作者对使用材料的任何后果不承担责任。用户需自行遵守其所在司法管辖区的法律。
