# SOFTWARE

- **OS:** LineageOS-based, no GApps.
- **Pre-installed:** F-Droid, DuckDuckGo, Proton Mail.
- **Aurora Store:** Not pre-installed. User installs it. Responsibility lies with the user.
- **Push:** Optional gateway (UnifiedPush/WebSocket). Lawful intercept responsibility lies with app developers.
- **Russia compatibility:** Officially not supplied. RTRCA and SORM requirements do not apply. This is technical incompatibility, not a political statement.
- **E2EE:** X25519, AES-256-GCM / ChaCha20-Poly1305. Keys in TEE.
- **FBE:** file-based encryption.
- **SMD Button:**
  - Privacy Mode: red.
  - Charge Y-Fill: white → yellow → green.
  - Thermal Hue: turquoise → yellow → orange → red.
- **Easter eggs:**
  - Roblox, RTRCA.
  - **Mindustry load arrows:** when opening Mindustry, during the **game’s own load screen**, the addressable lighting (SMD 4020 button + SK6812 accent lines) replays the Mindustry loading-arrow animation — those arrows from the middle of the horizontal — **in the same light/color** as on the load screen.

## Licensing (software)

- **Linux kernel (device changes / patches):** **GPLv2-only**. The Linux kernel is distributed as GPLv2-only; **GPLv3 is incompatible** with it, so all kernel modifications are strictly GPLv2-only.
- **Project userspace code (where applicable):** GPLv3 (see LICENSE.md).
- **LineageOS / AOSP base:** primarily **Apache License 2.0**. Apache 2.0 is **compatible with GPLv3** (they can coexist in one product), but **mixed licenses do not cancel the original**: code that arrived under Apache 2.0 remains under Apache 2.0; GPLv3 does not relicense it.
