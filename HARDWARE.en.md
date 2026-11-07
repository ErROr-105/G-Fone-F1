# HARDWARE

## Main Specifications
- **SoC:** MediaTek Dimensity 9600 Pro, 2 nm. LPDDR6 + UFS 5.0.
- **Memory:** 16 GB LPDDR6 + **256 GB UFS 5.0** (no microSD).
- **Display:** 6.77" LTPS IPS QHD.
- **Battery:** 5S1P, 46.25 Wh. Nominal **~18.5 V**, full **~21 V**. **X-Cross** = mechanics. **BMS** = active + shunt + NTC on a **documented IC** (TI BQ-class / equiv., ODM). Cert = **ODM gate**.
- **Charging:** up to 80 W, **USB PD PPS** (~21 V). ~80 W ≈ **1.6C** → **gentle default 40–50 W**. No wireless.
- **Protection / chassis:** IP69 / IP69K; 7075-T6 glue-free; steel ring cooler.

## BMS / PMIC
Per-cell V; NTC; shunt; active balancing on a **verifiable** controller. HV ~21 V full; filter choke in phone; multiphase. **X-Cross ≠ BMS.**

## Connectivity and storage
- **eSIM only** (userspace Privacy-First; **eUICC/modem closed**).
- **USB Host** + USB→SATA: **2.5″** prefer **USB-C/PD**; **3.5″** needs separate **12 V**. Optional signed-storage policy.
- No microSD = reliability/IP.

## DualBIOS *(engineering node)*
SPI NOR + secondary loader; LED/USB notify; external Android only with AVB user-keys or explicit disable+warning.

## SMD = Stop Meta Data (not surface-mount) — split button
- **Left:** power cut to cameras/mic/accelerometer.
- **Right:**
  - **L1 (required):** RF **path** kill — no TX/RX; modem **DMA may remain**.
  - **L2 (ODM, if separate baseband/eUICC rail exists):** **rail** kill.
  - No separate rail → ship L1 only.

## Threat model (short)
**In scope:** FBE, SMD, RF L1 (+ L2 if rail), DualBIOS+AVB, optional signed storage.  
**Not promised:** no DMA on path-only; L2 without a real rail; external boot without signature/warning.

## Cameras / cooling / kit
50 MP with **binning 50→~12.5**. Cooler; VC *(concept)*; XMC-2400. Finger cots = 7075 thermal.
