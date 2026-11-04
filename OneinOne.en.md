# G-Fone F1 — Beta 6.3.5 (Engineering Edition)

> Concept. Some specifications are design assumptions or non-standard combinations of existing technologies.  
> Everything marked *(concept)* requires additional verification with ODM and certification labs.  
> Licenses: CERN-OHL-P v2 (hardware); kernel GPLv2-only / G-Fone F1 userspace mods GPLv3 / Lineage·AOSP Apache 2.0 (compatible, not relicenseable); CC BY 4.0 (documentation).  
> Commercial use requires attribution.

---

## What is this

G-Fone F1 is a concept for a privacy-focused smartphone for people who are tired of everyone reading their data. Not a product, not an offer for sale, not a manufacturing guide. Just an engineering idea published for discussion, critique and improvement.

Target audience — privacy, repairability and “no-compromise hardware” enthusiasts. Not mass-market. Not enterprise. Not the Russian market.

---

## Main Specifications

- **SoC:** MediaTek Dimensity 9600 Pro, 2 nm, TSMC N2P. 2+3+3: 2× C2-Ultra up to 4.55 GHz, 3× C2-Pro up to 4.35 GHz, 3× C2-Pro up to 3.1 GHz. 34.5 MB cache. LPDDR6 + UFS 5.0. Announced 15.09.2026, devices by end of 2026.
- **Memory:** 16 GB LPDDR6 + 256 GB UFS 4.0. UFS 5.0 as availability allows.
- **Display:** 6.77" LTPS IPS QHD, high-end. Video up to 2K.
- **Battery:** 5S1P, 5 × 2500 mAh, 18.5 V, **46.25 Wh**. Prismatic Li-polymer. Battery Board with BMS (**active** 5S balancing), protection. **X-Cross** mounting (metal cross retaining prismatic cells). (5S1P is serial in drones/RC; unusual for smartphones)
- **Charging / PSU path:** 80 W, efficiency ≈ 95% (~76 W to battery). 0–80% ≈ 29 min; 0–100% ≈ 45–50 min with screen off. Charge path designed for **18.5 V (5S1P)**, **not** classic **3.7 V** single-cell.
- **Connectivity / slots:** **no mechanical SIM or microSD slots**. Cellular — **eSIM only** (up to 2 profiles — per ODM). BT to external satellite terminals. Direct satellite modem not claimed.
- **External storage:** full compatibility with external drives of **any size** (HDD/SSD/flash) via USB host (USB-C).
- **In the box:** **USB → SATA** adapter with **power** — 2.5″/3.5″ SATA without relying only on phone port current.
- **Price:** €3,200 (indicative for a niche flagship).

### Why 2500 mAh is not a typo

5S1P means 5 series cells of 2500 mAh each. Pack voltage 18.5 V. Energy 46.25 Wh. This is **≈3× more** (exact **2.9800257731958×**) than Galaxy S24 (typical capacity **4000 mAh**, official **15.52 Wh**). Equivalent at 3.7 V is **12,500 mAh**.

### X-Cross
Internal **metal cross-shaped part** that retains and clamps the prismatic 5S1P cells on the Battery Board.

### BMS and cell balancing (5S1P)
**Active balancing** is the required baseline. **Why not passive (bleed):** local overheating and lower efficiency. Monitoring: per-cell V; **battery temperature sensors** (NTC) on each of 5 cells; **shunt** for pack current (coulomb counting, OC/SC, SOC). OV/UV/OT/OC/short.

### Kit
- Plain-fabric finger cots (safety on 7075-T6).
- **USB → SATA adapter with power** in the box.
- Frame case with grip + silicone camera caps.

### Power / PMIC
Hybrid: HV front-end 18.5 V → intermediate bus; **filter choke in the phone**; multiphase digital buck on SoC hot rails; companion PMICs for other domains.

---

## Cameras
Main 50 MP Sony IMX903; tele 50 MP; ultrawide 50 MP IMX858; DoF 12 MP; selfie 50 MP. No generative AI. Keep-out ≥ 7 mm; ventilation texture outside lens area.

---

## Chassis and Cooling
7075-T6 glue-free; steel ring for magnetic active cooler; IP69 / IP69K with case. Triple VC *(concept)*. **Ventilation texture** *(concept)*: directional micro-channels for natural convection (not Junon-style through-holes). xMEMS Lab XMC-2400 (3 V, 30 mW / 70 mW with driver).

---

## Unique hardware
SMD (Stop Meta Data) physical cut-off for cameras/mic/accelerometer. Multi-mode RGB. Mindustry load-arrows LED easter egg.

---

## Software
LineageOS-based, no GApps. F-Droid, DuckDuckGo, Proton Mail. FBE. Kernel **GPLv2-only**; G-Fone userspace **GPLv3**; Lineage/AOSP Apache 2.0 (compatible, not relicenseable).

---

## Beta 6.3.5 Status

- **Feasible:** Dimensity 9600 Pro, LPDDR6, UFS 5.0, 5S1P, 80 W, XMC-2400, 7075-T6, steel ring cooler, active BMS (shunt + NTC), choke in phone, 18.5 V charge path, **eSIM only**, USB host + boxed USB→SATA with power.
- **Concept:** triple VC, telescopic antenna, **ventilation texture**, partial advanced PMIC, LED modes, Mindustry easter egg.
- **Beta 6.3.5 changes:** no mechanical SIM/SD; eSIM only; external drives any size; USB→SATA+power in box; (from 6.3.4: shunt + NTC).

> **Disclaimer.** Concept only. Not a product. Not certified. See LEGAL.md / PATENTS.md.
