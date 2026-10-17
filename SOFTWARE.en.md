# SOFTWARE

- **OS:** LineageOS-based, no GApps.
- **Pre-installed:** F-Droid, DuckDuckGo, Proton Mail.
- **Aurora Store:** not pre-installed. User installs. Responsibility on user.
- **Push:** optional gateway (UnifiedPush/WebSocket). Lawful intercept responsibility on app developers.
- **Russia compatibility:** officially not supplied. RTRCA and SORM requirements do not apply. Technical incompatibility, not a political statement.
- **E2EE:** X25519, AES-256-GCM / ChaCha20-Poly1305. Keys in TEE.
- **FBE:** file-based encryption.
- **SMD button:**
  - Privacy Mode: red.
  - Charge Y-Fill: white → yellow → green.
  - Thermal Hue: turquoise → yellow → orange → red.
- **Easter eggs:**
  - Roblox, RTRCA.
  - **Mindustry load arrows:** when opening Mindustry, during the **game’s own load screen**, addressable lighting (SMD 4020 button + SK6812 lines) replays the Mindustry loading-arrow animation — those arrows from the middle of the horizontal — **in the same light/color** as on the load screen.

## Licensing (software)

- **Linux kernel (device changes / patches):** **GPLv2-only**. Upstream Linux is **GPLv2-only**; **GPLv3 is incompatible** with it, so all kernel modifications for G-Fone F1 are **strictly GPLv2-only**.
- **G-Fone F1 project modifications and own code (userspace, where applicable):** **GPLv3**. Device/stack project code, not the kernel.
- **LineageOS / AOSP base:** primarily **Apache License 2.0**. **GPLv3 and Apache 2.0 are compatible** (they may coexist in one product) but **not relicenseable**: Apache-licensed code **cannot** be converted to GPLv3. Mixing **does not cancel the original**. When using Apache 2.0 code you **must fulfill Apache 2.0 requirements** (including NOTICE, attribution, and preserving license and change notices). See NOTICE.md / LICENSE.md.
