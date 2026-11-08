# G-Fone F1 — Beta 6.3.13 (Engineering Edition)

> Concept. Not a product. Licenses: CERN-OHL-P v2 / kernel **GPLv2-only** / userspace **GPLv3** / Lineage·AOSP **Apache 2.0** (separate works) / CC BY 4.0.

## What is this
Privacy / repairability concept for **tech users**. Not a product.

## Main Specifications
- **SoC:** Dimensity 9600 Pro, 2 nm. LPDDR6 + UFS 5.0.
- **Memory:** 16 GB LPDDR6 + **256 GB UFS 5.0** (no microSD).
- **Battery:** 5S1P, ~18.5 V nominal / ~21 V full, 46.25 Wh. **X-Cross** = mechanics. **BMS** = documented IC preferred.
- **Charging:** up to 80 W, **USB PD PPS**. Gentle default 40–50 W. No wireless.
- **Storage:** UFS 5.0; **USB Host** (2.5″ prefer USB-C/PD; 3.5″ needs 12 V; optional signed storage).

### DualBIOS / eSIM / SMD
DualBIOS: SPI NOR + secondary loader; AVB user-keys or explicit warning. eSIM: userspace policy; eUICC/modem closed. SMD: left = sensors power cut; right = RF **L1 path** required, **L2 rail** only if separate rail exists.

### Cameras
50 MP with **quad-Bayer binning 50→~12.5 MP**; full 50 MP separate mode. **No generative AI** (no proprietary closed-weight “enhancers”).

### Open-source HDR Stacking *(userspace, GPLv3)*
- Capture a **burst / bracketed series** and **merge on-device**.
- Entirely in **userspace**, licensed **GPLv3** (fits G-Fone userspace; not mixed into the GPLv2 kernel).
- Open algorithms (alignment + merge / exposure fusion and peers) — **no** proprietary ISP-AI, **no** cloud.
- Goal: controllable dynamic range without shipping frames to a vendor.

## Software
LineageOS-based, no GApps. FBE. Kernel **GPLv2-only**; userspace **GPLv3** (incl. **HDR Stacking**); Lineage/AOSP **Apache 2.0** — separate components.

## Threat model
**In scope:** FBE; SMD; RF L1 (+ L2 if rail); eSIM UX; USB Host; DualBIOS+AVB; local HDR without cloud.  
**Out of scope:** SoC/baseband audit; no DMA on path-only kill; external boot without signature/warning.

## Beta 6.3.13 Status
**Open-source HDR Stacking** (userspace GPLv3, no proprietary AI). (from 6.3.12)

> **Disclaimer.** Concept only. Not a product.
