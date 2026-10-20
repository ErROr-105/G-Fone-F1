# CHANGELOG

History of changes to the G-Fone F1 concept. Early versions (before Beta 3) are not published: some decisions were revised, some removed as unfeasible.

## Beta 6.3.1.1

- **Filter choke** — inside the phone (not in the external PSU).
- **PSU / charge path** — for **18.5 V (5S1P) pack**, not classic **3.7 V** single-cell.

## Beta 6.3.1

- **Steel ring in chassis** — seat for **magnetic active cooling** (detachable cooler).

## Beta 6.3

- **BMS / 5S1P balancing:** passive balancing (bleed) as required baseline; active balancing as optional high-end revision.
- **Clarification:** pack-level PTC ≠ cell balancing; per-cell V/T monitoring; OV/UV/OT/OC/short.
- Docs: HARDWARE / OneinOne.

## Beta 6

- **X-Cross:** described — internal metal cross-shaped part retaining prismatic 5S1P cells.
- **Pack-level PTC film** for cold protection; cell-level PTC is pointless for 5S1P (series string = one electro-thermal pack).
- **Plain-fabric finger cots** in the kit: 7075 aluminum is extreme at heat transfer; safety when handling bare metal.
- **Case:** frame with grip; mid-price silicone camera caps included (scratch protection).

## Beta 5.1

- **Display:** 7" → **6.77"** LTPS IPS QHD.
- **Main camera:** Sony **IMX903** (was IMX907).
- **MEMS / Anti-Burn:** concrete model **xMEMS Lab XMC-2400** — 3 V, 30 mW (pump) / **70 mW with driver**; no longer a generic concept range.
- **Licensing:** Linux kernel changes **GPLv2-only** (GPLv3 incompatible with the kernel); project userspace GPLv3; LineageOS/AOSP base primarily **Apache 2.0** — compatible with GPLv3, but mixed licenses do not cancel the original Apache terms.
- **NOTICE.md:** full reproduction of LineageOS `android_frameworks_base` NOTICE (AOSP attribution / Apache 2.0 §4(d)).
- **Documentation:** SOFTWARE.md / LICENSE.md / OneinOne.* license sections updated for kernel vs userspace vs Lineage base.

## Beta 5

- **Easter egg — Mindustry load arrows:** when opening Mindustry, during the game’s load screen, SMD 4020 button + SK6812 accent lines replay the loading arrows from the middle of the horizontal **in the same light/color** as on screen (not tied to device boot).
- **Power / PMIC:** documented partial integration of an advanced multiphase digital buck controller for SoC hot rails (CPU/GPU/NPU) plus HV front-end for 5S1P 18.5 V; companions for other domains.
- **Concept markers:** revised (SoC/LPDDR6/UFS 5.0/MEMS as serial; triple VC, telescopic antenna, fins as concept/system integration).
- **MEMS:** driver power stated in the 0.1–0.3 W range (superseded in Beta 5.1 by XMC-2400 specs).
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
