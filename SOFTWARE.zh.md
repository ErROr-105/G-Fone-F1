# SOFTWARE

- **系统：** 基于 LineageOS，无 GApps。
- **预装：** F-Droid、DuckDuckGo、Proton Mail。
- **Aurora Store：** 不预装，用户自行安装，责任自负。
- **推送：** 可选网关（UnifiedPush/WebSocket）。合法拦截责任在应用开发者。
- **俄罗斯兼容性：** 官方不供应。不适用 RTRCA 与 SORM。技术不兼容，非政治声明。
- **E2EE：** X25519，AES-256-GCM / ChaCha20-Poly1305。密钥在 TEE。
- **FBE：** 基于文件的加密。
- **SMD 按钮：** Privacy 红；Charge Y-Fill 白→黄→绿；Thermal Hue 青→黄→橙→红。
- **彩蛋：** Roblox、RTRCA；**Mindustry 加载箭头** — 打开 Mindustry 时在游戏加载画面期间灯光复现水平中部箭头动画，光色与画面一致。

## 许可（软件）

- **Linux 内核（设备修改/补丁）：** **GPLv2-only**。上游 Linux 为 **GPLv2-only**；**GPLv3 与之不可兼容**，因此 G-Fone F1 的所有内核改动 **严格 GPLv2-only**。
- **G-Fone F1 项目修改与自有代码（userspace，适用处）：** **GPLv3**。设备/栈项目代码，非内核。
- **LineageOS / AOSP 基础：** 主要为 **Apache License 2.0**。**GPLv3 与 Apache 2.0 兼容**（可同产品并存），但**不可再许可（not relicenseable）**：Apache 代码**不能**改为 GPLv3。混合**不取消原许可**。使用 Apache 2.0 代码时**必须履行 Apache 2.0 要求**（含 NOTICE、署名、保留许可与变更声明）。见 NOTICE.md / LICENSE.md。
