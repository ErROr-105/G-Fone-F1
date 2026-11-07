# HARDWARE

## Main Specifications
- **SoC:** MediaTek Dimensity 9600 Pro, 2 nm. LPDDR6 + UFS 5.0.
- **Memory (internal only):** 16 GB LPDDR6 + **256 GB UFS 5.0** (no microSD).
- **Display:** 6.77" LTPS IPS QHD.
- **Battery:** 5S1P, 46.25 Wh. Nominal **~18.5 V**, full **~21 V** (5×4.2). **X-Cross**. Active BMS. Cert = **ODM gate**.
- **Charging:** up to 80 W **wired**. Path to **~21 V** → **USB PD PPS**. ~80 W ≈ **1.6C** — aggressive; **gentle default 40–50 W**; cycle life TBD. No wireless. Times = calculated/estimate.
- **Protection:** IP69 / IP69K. **Chassis:** 7075-T6 glue-free; steel ring cooler.

## BMS
Per-cell V; NTC on each cell; pack shunt. **Active** balancing baseline.

## Power / PMIC
HV to ~21 V full; filter choke **in the phone**; multiphase on SoC hot rails.

## Connectivity and storage
- No SIM/microSD slots. **eSIM only** (Privacy-First userspace; **eUICC/modem firmware closed**; OS policy ≠ modem-side guarantee).
- Internal: **256 GB UFS 5.0**.
- **USB Host** + **USB → SATA with power** (2.5″; 3.5″ needs separate **12 V**).
- **Why No microSD?** reliability/IP, not mainboard repairability.

## DualBIOS (spare boot chip) *(engineering node)*
SoC Boot ROM → UFS 5.0; on UFS failure → DualBIOS notify + optional external Android (if image written).

## SMD = Stop Meta Data (not surface-mount) — split button
- **Left:** power cut to cameras/mic/accelerometer.
- **Right:** **RF path kill** (antenna path).

## Threat model (short)
**In scope:** FBE, SMD, RF kill, eSIM UX (userspace), DualBIOS.  
**Not promised:** baseband/eUICC/SoC audit; external boot without image; battery cert as done; crypto-immutable log without TEE/SE.

## Cameras / cooling / kit
IMX903 etc. Magnetic cooler; VC *(concept)*; XMC-2400. Finger cots = **7075 thermal**; USB→SATA; frame case.
