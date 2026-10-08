# CHANGELOG

History of changes to the G-Fone F1 concept. Early versions (before Beta 3) are not published: some decisions were revised, some removed as unfeasible.

## Beta 5

- **Easter egg — Mindustry load arrows:** when opening Mindustry, during the game’s load screen, SMD 4020 button + SK6812 accent lines replay the loading arrows from the middle of the horizontal **in the same light/color** as on screen (not tied to device boot).
- **Power / PMIC:** documented partial integration of an advanced multiphase digital buck controller for SoC hot rails (CPU/GPU/NPU) plus HV front-end for 5S1P 18.5 V; companions for other domains.
- **Concept markers:** revised (SoC/LPDDR6/UFS 5.0/MEMS as serial; triple VC, telescopic antenna, fins as concept/system integration).
- **MEMS:** driver power stated explicitly — 0.1–0.3 W.
- **Encryption:** FBE (file-based encryption) instead of FDE wording.
- **Documentation:** Russian OneinOne.md restored; HARDWARE/OneinOne synced across RU/EN/ZH/KO.

## Beta 4

- **LED lighting:**
  - Accent lines: addressable RGB strip SK6812 IP65, 60 LEDs/m, side-emitting, SMD 4020.
  - SMD button: addressable RGB SMD 4020, IP65.
  - Thermal Hue routed to rear panel lines, synchronized with the button.
- **Software:**
  - Work Profile (Geo-Stable) removed as excessive isolation.
  - Russian block rephrased: from “refusal” to “architectural incompatibility”.
  - App blacklist replaced with description of incompatibility with RTRCA and SORM.
- **Licenses:**
  - Hardware: CERN-OHL-P v2.
  - Software: GPLv3.
  - Documentation: CC BY 4.0.
- **Documentation:**
  - Added LEGAL.md (legal analysis).
  - Added DISCLAIMER.md.
  - Added Encryption-Notification-Date.md (BIS notification).
  - OneinOne.md — full Engineering Edition in one file.

## Beta 3

- Added SMD (Stop Meta Data) button with physical power cut-off for cameras, microphone and accelerometer.
- Added multi-mode LED lighting for the button:
  - Privacy Mode (red).
  - Charge Y-Fill.
  - Thermal Hue.
- Initial patent analysis performed:
  - SEP 5G (10–15% of retail).
  - Motorola US 12,308,512 B2 (telescopic antenna).
  - US 20250357560 A1 (5S1P).
- Described Anti-Burn thermal stabilization block (MEMS micropumps).

Earlier versions (Beta 1, Beta 2) are not published.
