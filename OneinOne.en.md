# G-Fone F1 — Beta 6.3.11 (Engineering Edition)

> Concept. Not a product. Licenses: CERN-OHL-P v2 / kernel **GPLv2-only** / userspace **GPLv3** / Lineage·AOSP **Apache 2.0** (distributed **separately** — Apache 2.0 is **not** combinable with GPLv2 into one program; OK with GPLv3) / CC BY 4.0.

## What is this

G-Fone F1 is a privacy / repairability / no-compromise hardware concept for **tech users**. Not a product, not an offer, not a manufacturing guide. Not mass-market. Not enterprise.

## Main Specifications

- **SoC:** Dimensity 9600 Pro, 2 nm. LPDDR6 + UFS 5.0. (*projected.*)
- **Memory (internal only):** 16 GB LPDDR6 + **256 GB UFS 5.0** (no microSD).
- **Display:** 6.77" LTPS IPS QHD.
- **Battery:** 5S1P, 46.25 Wh. Nominal **~18.5 V**, full **~21 V**. Active BMS. Cert = **ODM gate**. 12,500 mAh @ 3.7 V = **equivalent calculation**.
- **Charging:** up to 80 W wired via **USB PD PPS** (~21 V). ~80 W ≈ **1.6C** → **gentle default 40–50 W**. No wireless.
- **Storage:** UFS 5.0 only; **USB Host**; USB→SATA (2.5″; 3.5″ needs **12 V**).

### DualBIOS *(engineering node)*

**Problem:** production **SoC Boot ROM** usually **cannot** boot from USB mass-storage alone. A “spare medium” does not hand control to the CPU unless a **secondary loader** is in a path the SoC **accepts**.

**Design intent:**
1. **SoC Boot ROM** — always first.
2. Normal path: **UFS 5.0** (loader + AVB + OS).
3. **DualBIOS chip** — own firmware (typically **SPI NOR**), fallback boot source after UFS failure (mux/strap/order = ODM + SoC policy).
4. DualBIOS brings up a **minimal secondary loader** that **notifies** UFS failure and may continue from USB Host **only** under AVB policy below — not “magic USB boot from Boot ROM.”

**Verified Boot / AVB:**
- **A:** external image signed with **user-owned keys** and verified; or
- **B:** verification disableable only with **explicit warning** (preferably physical confirm).
- Without A or B, DualBIOS is **not** privacy-safe recovery.

**Notify if panel is dead:** **RGB SMD / SK6812** and/or **USB device-side status** — do not rely on the display alone.

### eSIM: Privacy-First Control
Userspace policy only. **eUICC/modem firmware closed**. Log without TEE/SE is not crypto-immutable.

### SMD = **Stop Meta Data** (not surface-mount) — split button
| Half | Function |
|------|----------|
| **Left** | Power cut to cameras / mic / accelerometer |
| **Right** | **RF path kill** (no TX/RX). Modem **stays in the SoC** and may still be **powered** with **DMA to RAM** — kill ≠ memory isolation |

Left/right relative to normal orientation (screen toward user, antenna top); final CAD owns placement.

### Cameras
50 MP sensors; normal mode **quad-Bayer binning 50→~12.5 MP**; full 50 MP is a separate mode.

## Threat model

**In scope:** FBE; left SMD; right RF path kill (RF only, not DMA); eSIM UX; USB Host; DualBIOS **only** with AVB user-keys or explicit disable+warning.

**Out of scope:** SoC/baseband/eUICC audit; **no modem DMA** while RF killed; external boot without signed image / without explicit AVB disable; battery cert as done; crypto-immutable log without TEE/SE.

## Beta 6.3.11 Status

DualBIOS secondary loader + **AVB/user keys or explicit warning** + LED/USB notify; RF kill **DMA caveat**; binning 50→12.5. (from 6.3.10)

> **Disclaimer.** Concept only. Not a product. Not an offer for any specific market.
