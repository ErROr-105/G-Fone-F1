# CHANGELOG

G-Fone F1 概念的变更历史。早期版本（Beta 3 之前）未发布：部分决策已修订，部分因不可行而删除。

## Beta 5

- **彩蛋 — Mindustry 开机箭头：** 若在设备启动时打开 Mindustry，SMD 4020 按钮 + SK6812 装饰线复现 Mindustry 加载箭头（人字）动画，并与游戏加载画面同步。
- **电源 / PMIC：** 记录面向 SoC 热轨（CPU/GPU/NPU）的更先进多相数字 buck 控制器部分集成，以及 5S1P 18.5 V 高压前端；其余域用 companion。
- **概念标记：** 修订（SoC/LPDDR6/UFS 5.0/MEMS 为量产；三层 VC、伸缩天线、鳍片为概念/系统集成）。
- **MEMS：** 明确驱动功率 0.1–0.3 W。
- **加密：** 表述为 FBE（file-based encryption）。
- **文档：** 恢复俄文 OneinOne.md；HARDWARE/OneinOne 四语同步。

## Beta 4

- **LED 灯光：**
  - 装饰线条：可寻址 RGB 灯带 SK6812 IP65，60 LEDs/m，侧发光，SMD 4020。
  - SMD 按钮：可寻址 RGB SMD 4020，IP65。
  - Thermal Hue 引出至后盖线条，与按钮同步。
- **软件：**
  - 删除 Work Profile (Geo-Stable)，认为隔离过度。
  - 俄罗斯相关表述从“拒绝”改为“架构不兼容”。
  - 应用黑名单改为对 RTRCA 和 SORM 不兼容的说明。
- **许可证：**
  - 硬件：CERN-OHL-P v2。
  - 软件：GPLv3。
  - 文档：CC BY 4.0。
- **文档：**
  - 新增 LEGAL.md（法律分析）。
  - 新增 DISCLAIMER.md。
  - 新增 Encryption-Notification-Date.md（BIS 通知）。
  - OneinOne.md — 完整工程版单文件。

## Beta 3

- 新增 SMD（Stop Meta Data）按钮，可物理切断摄像头、麦克风和加速度计电源。
- 新增按钮多模式 LED 指示：
  - Privacy Mode（红色）。
  - Charge Y-Fill。
  - Thermal Hue。
- 完成初步专利分析：
  - SEP 5G（零售价的 10–15%）。
  - Motorola US 12,308,512 B2（伸缩天线）。
  - US 20250357560 A1（5S1P）。
- 描述 Anti-Burn 热稳定模块（MEMS 微泵）。

早期版本（Beta 1、Beta 2）未发布。
