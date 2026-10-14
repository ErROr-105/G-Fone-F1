# SOFTWARE

- **系统：** 基于 LineageOS，无 GApps。
- **预装：** F-Droid、DuckDuckGo、Proton Mail。
- **Aurora Store：** 不预装。用户自行安装。责任由用户承担。
- **推送：** 可选网关（UnifiedPush/WebSocket）。合法拦截责任由应用开发者承担。
- **俄罗斯兼容性：** 官方不供应该市场。RTRCA 和 SORM 要求不适用。这是技术不兼容，而非政治声明。
- **端到端加密：** X25519、AES-256-GCM / ChaCha20-Poly1305。密钥存储在 TEE。
- **FBE：** file-based encryption。
- **SMD 按钮：**
  - 隐私模式：红色。
  - 充电指示：白 → 黄 → 绿。
  - 温度指示：青绿 → 黄 → 橙 → 红。
- **彩蛋：**
  - Roblox、RTRCA。
  - **Mindustry 加载箭头：** 打开 Mindustry 时，在**游戏自身加载画面**期间，可寻址灯光（SMD 4020 按钮 + SK6812 装饰线）复现 Mindustry 加载箭头动画——即从水平线中部展开的那些箭头——**使用与加载画面相同的光色**。

## 许可（软件）

- **Linux 内核（设备修改/补丁）：** **GPLv2-only**。Linux 内核以 GPLv2-only 分发；**GPLv3 与之不可兼容**，因此所有内核改动严格采用 GPLv2-only。
- **本项目 userspace 代码（适用处）：** GPLv3（见 LICENSE.md）。
- **LineageOS / AOSP 基础：** 主要为 **Apache License 2.0**。Apache 2.0 **与 GPLv3 兼容**（可同产品并存），但**混合许可并不取消原许可**：以 Apache 2.0 引入的代码仍保持 Apache 2.0；GPLv3 不会改写其原许可证。
