# HARDWARE

## Main Specifications
- **SoC:** MediaTek Dimensity 9600 Pro, 2 nm. LPDDR6 + UFS 5.0.
- **Memory:** 16 GB LPDDR6 + **256 GB UFS 5.0** (no microSD).
- **Display:** 6.77" LTPS IPS QHD.
- **Battery:** 5S1P, 46.25 Wh. Nominal **~18.5 V**, full **~21 V**. Active BMS. Cert = **ODM gate**.
- **Charging:** up to 80 W, **USB PD PPS** (~21 V). ~80 W ≈ **1.6C** → **gentle default 40–50 W**. No wireless.
- **Protection / chassis:** IP69 / IP69K; 7075-T6 glue-free; steel ring cooler.

## BMS / PMIC
Per-cell V; NTC; shunt; active balancing. HV ~21 V full; filter choke in phone; multiphase.

## Connectivity and storage
- **eSIM only** (userspace Privacy-First; **eUICC/modem closed**).
- **USB Host** + USB→SATA (2.5″; 3.5″ needs separate **12 V**).
- No microSD = reliability/IP.

## DualBIOS (spare boot chip) *(engineering node)*
- SoC Boot ROM **usually cannot** USB-boot alone → DualBIOS = **SPI NOR (typical) + secondary loader**, not “disk instead of UFS.”
- On UFS failure: notify (**LED / USB status**, not panel-only) → optional Android from USB **only** if image is **user-key signed (AVB)** or AVB is **explicitly** disabled with a warning.
- Otherwise DualBIOS is not privacy-safe recovery. ODM: MediaTek boot policy, fuses, UX.

## SMD = Stop Meta Data (not surface-mount) — split button
- **Left:** power cut to cameras/mic/accelerometer.
- **Right:** **RF path kill** (antenna path). Modem stays in SoC; domain power and **DMA to RAM** may remain while RF is killed.

## Threat model (short)
**In scope:** FBE, SMD, RF kill (RF only), DualBIOS with AVB policy.  
**Not promised:** no modem DMA while RF killed; external boot without signature/warning; eUICC/SoC audit.

## Cameras / cooling / kit
50 MP with **binning 50→~12.5**. Cooler; VC *(concept)*; XMC-2400. Finger cots = 7075 thermal.
