# G-Fone F1 — Beta 6.3.16 (Engineering Edition)

> Concept. Not a product. Licenses: CERN-OHL-P v2 / kernel **GPLv2-only** / userspace **GPLv3** / Lineage·AOSP **Apache 2.0** (distributed **separately** — Apache 2.0 is **not** combinable with GPLv2 into one program; OK with GPLv3) / CC BY 4.0.

## What is this

Privacy / repairability / no-compromise hardware concept for **tech users**. Not a product, not an offer, not a manufacturing guide. Not mass-market. Not enterprise.

## Main Specifications

- **SoC:** Dimensity 9600 Pro, 2 nm. LPDDR6 + UFS 5.0. (*projected.*)
- **Memory (internal only):** 16 GB LPDDR6 + **256 GB UFS 5.0** (no microSD).
- **Display:** 6.77" LTPS IPS QHD (conscious IPS choice).
- **Battery:** 5S1P, 46.25 Wh. Nominal **~18.5 V** (5×3.7), full **~21 V** (5×4.2). **X-Cross** = mechanical cell hold-down only. **BMS** = active balancing + shunt + NTC on a **documented controller** preferred (e.g. TI BQ-class / equivalent with datasheet + drivers; ODM choice). Cert = **ODM gate**. 12,500 mAh @ 3.7 V = **equivalent calculation**.
- **Charging:** up to 80 W **wired**. Path must support **~21 V** at end of charge → **USB PD PPS**; fixed 20 V PD is not enough for full CV. 0–80% ≈ 29 min / 0–100% ≈ 45–50 min = **calculated targets** at ~80 W (~**1.6C**) — **aggressive** for phone-class prismatic cells: **gentle charge default** (e.g. 40–50 W); cycle-life target **TBD with ODM**. **No wireless charging**.
- **Connectivity:** no mechanical SIM/microSD; **eSIM only**.
- **Storage:** UFS 5.0 only; **USB Host**; USB→SATA in the kit (see below).
- **Price:** €3200.

### Why No microSD?
Fewer failure points → reliability/IP. On UFS failure → **DualBIOS**.

### USB Host Storage: User-Chosen Flexibility
Any USB SSD/HDD. Tool, not appliance.

- **2.5″ SSD:** prefer power from **phone USB-C / PD** or the kit adapter **without a separate 12 V wall** when the bridge allows; else external 5 V from the kit PSU.
- **3.5″ HDD:** still needs **separate 12 V** (desk/lab, not a pocket scenario).
- **Signed / authenticated storage *(policy, concept)*:** optional signature/access policy for sensitive volumes, aligned with AVB external-boot (not “any disk is trusted”).
- Kit: **USB → SATA with power** under these rules.

### DualBIOS *(engineering node)*

**Problem:** production **SoC Boot ROM** usually **cannot** boot from USB mass-storage alone. A “spare medium” does not hand control to the CPU unless a **secondary loader** is in a path the SoC **accepts**.

**Design intent:**
1. **SoC Boot ROM** — always first.
2. Normal path: **UFS 5.0** (loader + AVB + OS).
3. **DualBIOS chip** — own firmware (typically **SPI NOR**), fallback after UFS failure (mux/strap/order = ODM + SoC policy).
4. DualBIOS brings up a **minimal secondary loader** that **notifies** UFS failure and may continue from USB Host **only** under AVB policy — not “magic USB boot from Boot ROM.”

**Verified Boot / AVB:**
- **A:** external image signed with **user-owned keys** and verified; or
- **B:** verification disableable only with **explicit warning** (preferably physical confirm).
- Without A or B, DualBIOS is **not** privacy-safe recovery.

**Notify if panel is dead:** **RGB SMD / SK6812** and/or **USB device-side status**.

### eSIM: Privacy-First Control
Userspace: activate/deactivate only; explicit consent for delete/modify/telemetry; local log. **Caveat:** eUICC / SM-DP+ / OTA; **modem and eUICC firmware are closed**. OS policy ≠ modem-side guarantee. “Immutable” log without **TEE/SE + hash-chain** is not cryptographic immutability.

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

| Module | Concept spec | Public reference / note |
|--------|--------------|-------------------------|
| **Main** | **Sony LYTIA 720** (confirmed BOM choice) | **IMX903** has public tests (DXOMARK / iPhone 17 Pro) but is **Apple-oriented** design-in — **not** used here (same for IMX907). LYTIA 720 is the non-Apple path. |
| **Tele** | **~70 mm eq., 50 MP, f/1.8, OIS**, **IMX858-class** (or ODM equivalent) | No shipping **f/1.4** tele at ~70–100 mm (entrance pupil unrealistic). Closest tests: Xiaomi 15 Ultra tele/zoom; iPhone 17 Pro tele ~100 mm f/2.8. |
| **Ultrawide** | **Sony IMX858**, ~14 mm, **f/2.2**, 50 MP | Direct Android design-in: Xiaomi 14/15 Ultra (DXOMARK UW sub-score **158** on 15 Ultra). **No f/1.4 UW** — analogue is f/2.2. |
| **DoF / selfie** | DoF 12 MP; selfie 50 MP | ODM BOM; no generative AI. |

**Default:** quad-Bayer **binning 50→~12.5 MP**; full-res is a separate mode.

**Evidence (external):** DXOMARK iPhone 17 Pro; DXOMARK / GSMArena / sampleshots Xiaomi 15 Ultra. Crops/EXIF on those reviews — not hosted in-repo.

### Open-source HDR Stacking *(userspace, GPLv3)*
- Capture a **burst / bracketed series** and **merge on-device**.
- Entirely in **userspace**, licensed **GPLv3** (fits G-Fone userspace; **not** mixed into the GPLv2 kernel).
- Open algorithms (alignment + merge / exposure fusion and peers) — **no** proprietary ISP-AI, **no** cloud.
- Goal: controllable dynamic range without shipping frames to a vendor.

### Mindustry load-arrows (feature; open-source game)
While **Mindustry** (open-source) is on its load screen, SMD + SK6812 repeat the in-game load-arrow animation in the same color/light. UI sync with an open-source game — not a gag. Not tied to device boot.

## Software
LineageOS-based, no GApps. FBE. Kernel **GPLv2-only**; userspace **GPLv3** (incl. **HDR Stacking**); Lineage/AOSP **Apache 2.0** — separate components.

## Threat model

**In scope:** FBE; left SMD; RF kill **L1 always**, **L2 only if rail exists**; eSIM UX; USB Host + optional signed-storage policy; local HDR Stacking without cloud; DualBIOS **only** with AVB user-keys or explicit disable+warning.

**Out of scope:** SoC/baseband/eUICC audit; **no DMA** on path-only kill; L2 without a real separate rail; external boot without signature/warning; battery cert as done; crypto-immutable log without TEE/SE.

## Support
Community + ODM SLA (**TBD**). microG etc. **optional by user**, not preinstalled. vs GrapheneOS+Pixel: open hardware, 5S1P, split SMD, DualBIOS, USB Host.

## Beta 6.3.16 Status

Cameras: **LYTIA 720** main; tele **70 mm f/1.8 OIS** (not f/1.4); UW **IMX858 f/2.2**. **Open-source HDR Stacking**. (from 6.3.12–6.3.15)

> **Disclaimer.** Concept only. Not a product. Not an offer for any specific market.
