# G-Fone F1 — Beta 6.3.12 (Engineering Edition)

> Concept. Not a product. Licenses: CERN-OHL-P v2 / kernel **GPLv2-only** / userspace **GPLv3** / Lineage·AOSP **Apache 2.0** (separate works — Apache 2.0 **not** combinable with GPLv2 into one program; OK with GPLv3) / CC BY 4.0.

## What is this

Privacy / repairability / no-compromise hardware concept for **tech users**. Not a product. Not mass-market. Not enterprise.

## Main Specifications

- **SoC:** Dimensity 9600 Pro, 2 nm. LPDDR6 + UFS 5.0. (*projected.*)
- **Memory (internal only):** 16 GB LPDDR6 + **256 GB UFS 5.0** (no microSD).
- **Display:** 6.77" LTPS IPS QHD.
- **Battery:** 5S1P, 46.25 Wh. Nominal **~18.5 V**, full **~21 V**. **X-Cross** = mechanical cell hold-down only. **BMS** = active balancing + shunt + NTC on a **documented controller** preferred (e.g. TI BQ-class / equivalent with datasheet + drivers; ODM choice). Cert = **ODM gate**. 12,500 mAh @ 3.7 V = **equivalent calculation**.
- **Charging:** up to 80 W wired via **USB PD PPS** (~21 V). ~80 W ≈ **1.6C** → **gentle default 40–50 W**. No wireless.
- **Storage:** UFS 5.0 only; **USB Host**; USB→SATA in the kit (see below).

### USB Host Storage: User-Chosen Flexibility
Any USB SSD/HDD. Tool, not appliance.

- **2.5″ SSD:** prefer power from **phone USB-C / PD** or the kit adapter **without a separate 12 V wall** when the bridge allows; else external 5 V from the kit PSU.
- **3.5″ HDD:** still needs **separate 12 V** (desk/lab, not a pocket scenario).
- **Signed / authenticated storage *(policy, concept)*:** optional signature/access policy for sensitive volumes, aligned with AVB external-boot (not “any disk is trusted”). Design intent, not mandatory USB-IF branding.
- Kit: **USB → SATA with power** under these rules.

### DualBIOS *(engineering node)*
SoC Boot ROM usually cannot USB-boot alone → **SPI NOR + secondary loader**. Notify via **LED/USB**. External Android **only** with **AVB user-keys** or explicit disable+warning.

### eSIM: Privacy-First Control
Userspace policy. **eUICC/modem closed**. Log without TEE/SE is not crypto-immutable.

### SMD = **Stop Meta Data** (not surface-mount) — split button
| Half | Function |
|------|----------|
| **Left** | Power cut to cameras / mic / accelerometer |
| **Right** | **RF kill L1/L2** |

**Right half — RF kill levels:**
1. **Baseline (required):** hardware **RF path kill** (antenna break) → no over-the-air TX/RX. Modem **stays in the SoC**; domain power and **DMA to RAM may remain**.
2. **ODM target (only if SoC/PMIC exposes a separate baseband/eUICC rail):** hardware **rail kill**. Still not proof of silicon-idle, but stronger than path-only.
3. If no separate rail exists — ship **L1 only**; do not market L2.

### Cameras
50 MP with **quad-Bayer binning 50→~12.5 MP**; full 50 MP separate mode.

## Threat model

**In scope:** FBE; left SMD; RF kill **L1 always**, **L2 only if rail exists**; eSIM UX; USB Host + optional signed-storage policy; DualBIOS **only** with AVB user-keys or explicit disable+warning.

**Out of scope:** SoC/baseband/eUICC audit; **no DMA** on path-only kill; L2 without a real separate rail; external boot without signature/warning; battery cert as done; crypto-immutable log without TEE/SE.

## Support
Community + ODM SLA (**TBD**). microG etc. **optional by user**, not preinstalled. vs GrapheneOS+Pixel: open hardware, 5S1P, split SMD, DualBIOS, USB Host.

## Beta 6.3.12 Status

RF kill **L1 path / L2 rail-if-available**; USB 2.5″ **PD**; optional **signed storage**; **BMS = documented IC**, X-Cross = mechanics. (from 6.3.11)

> **Disclaimer.** Concept only. Not a product.
