# G-Fone F1 — Beta 6.3.10 (Engineering Edition)

> Concept. Not a product. Licenses: CERN-OHL-P v2 / kernel **GPLv2-only** / userspace **GPLv3** / Lineage·AOSP **Apache 2.0** (distributed **separately** — Apache 2.0 is **not** combinable with GPLv2 into one program; OK with GPLv3) / CC BY 4.0.

## Main Specifications

- **SoC:** Dimensity 9600 Pro, 2 nm. LPDDR6 + UFS 5.0. (*projected.*)
- **Memory (internal only):** 16 GB LPDDR6 + **256 GB UFS 5.0** (no microSD).
- **Display:** 6.77" LTPS IPS QHD (conscious IPS choice).
- **Battery:** 5S1P, 46.25 Wh. Pack **nominal ~18.5 V** (5×3.7), **full charge ~21 V** (5×4.2). **X-Cross**; active BMS; shunt + per-cell NTC. Cert = **ODM gate**. **12,500 mAh @ 3.7 V** is an **equivalent calculation**, not a cell rating.
- **Charging:** up to 80 W **wired**. Path must support **~21 V** at end of charge → **USB PD PPS** (or equivalent); fixed 20 V PD is not enough for full CV. 0–80% ≈ 29 min / 0–100% ≈ 45–50 min = **calculated targets** at ~80 W (~**1.6C** into 46.25 Wh) — **aggressive** for phone-class prismatic cells: **gentle charge default** (e.g. 40–50 W) and cycle-life target (e.g. 80% capacity after N cycles) = **TBD with ODM**. **No wireless charging**.
- **Connectivity:** no mechanical SIM/microSD; **eSIM only**.
- **Storage:** **256 GB UFS 5.0 only**; **USB Host**; **USB → SATA with power** (2.5″; **3.5″ needs separate 12 V**).

### Why No microSD?
Fewer failure points → reliability/IP. On UFS failure → **DualBIOS** (notify + external Android if image written).

### USB Host Storage: User-Chosen Flexibility
Any USB SSD/HDD. Tool, not appliance. Mobile → 2.5″; 3.5″ → desk + external 12 V.

### DualBIOS (spare boot chip) *(engineering node)*
**SoC Boot ROM** → normally **UFS 5.0** → on UFS failure: DualBIOS (own firmware) **notifies** and **offers** to boot Android from an external disk if an image was written. Not unbrick from nothing.

### eSIM: Privacy-First Control
Userspace: activate/deactivate only; explicit consent for delete/modify/telemetry; local log. **Caveat:** profiles go through eUICC / SM-DP+ / OTA; **modem and eUICC firmware are closed**. OS policy ≠ guarantee of no modem/eUICC-side actions. “Immutable” userspace log without a **hardware anchor** (TEE / SE + hash-chain) is a hardened log, not cryptographic immutability.

### SMD = **Stop Meta Data** (not “surface-mount device”) — split button
| Half | Function |
|------|----------|
| **Left** | Power cut to cameras / mic / accelerometer |
| **Right** | **RF path kill** (antenna path). Modem stays in SoC |

Finger cots: 7075 thermal protection for bare-metal handling (cold/hot), not cut protection.

## Threat model (honest bounds)

**In scope:** FBE; left SMD; right RF path kill; eSIM UX (userspace); USB Host; DualBIOS fallback.

**Out of scope:** SoC/baseband/eUICC audit; modem DMA while RF killed; external boot without image; battery cert as done; crypto-immutable log without TEE/SE.

## Support & software caveats
Patch intent: community + ODM SLA (**TBD**). Banking/Play Integrity may fail without GApps. vs GrapheneOS+Pixel: open hardware, 5S1P, split SMD, DualBIOS, USB Host tool-device.

## Beta 6.3.10 Status

Charge path **~21 V / PPS**; **~1.6C** + gentle default; eUICC/modem honesty; Apache↔GPLv2 wording; SMD name disambiguation. (from 6.3.9: UFS 5.0, DualBIOS)

> **Disclaimer.** Concept only. Not a product.
