# HARDWARE

## Main Specifications
- **SoC:** MediaTek Dimensity 9600 Pro, 2 nm. LPDDR6 + UFS 5.0.
- **Memory (internal only):** 16 GB LPDDR6 + **256 GB UFS 4.0** (no microSD).
- **Display:** 6.77" LTPS IPS QHD (conscious IPS choice).
- **Battery:** 5S1P, 5 × 2500 mAh, 18.5 V, 46.25 Wh. **X-Cross**. BMS + **active balancing**. Battery cert = **ODM gate**.
- **Charging:** 80 W **wired**, ≈95% efficiency. **No wireless charging**. Path for **18.5 V (5S1P)**. Charge times are **calculated / estimates** (CV).
- **Protection:** IP69 / IP69K (with case).
- **Chassis:** 7075-T6, glue-free. Steel ring — magnetic cooler.

## BMS and balancing (5S1P)
- Monitoring: per-cell V; **NTC on each** of 5 cells; pack **shunt**.
- **Active** balancing baseline. Passive bleed is not baseline.
- Protection OV/UV/OT/OC/short.

## Power / PMIC
HV front-end 18.5 V → intermediate bus; **filter choke in the phone**; multiphase on SoC hot rails; companions for other domains.

## Why no wireless charging
Lower efficiency; local heat undesirable for 5S1P; coil EMF hurts magnetometer.

## Connectivity and storage
- **SIM / SD:** no mechanical slots. **eSIM only**.
- **eSIM: Privacy-First** (userspace): activate/deactivate; no delete/modify/telemetry without explicit consent; local log. Does **not** prove absence of baseband-side behavior in the SoC.
- **Internal:** **256 GB UFS 4.0 only**.
- **USB Host:** any USB SSD/HDD. **USB → SATA with power:** 2.5″ from adapter/USB; **3.5″ needs separate 12 V** from the adapter (not the phone, not the 80 W charge path).
- **Why No microSD?** fewer failure points → **reliability/IP**; not “easier mainboard repair.”

## SMD (Stop Meta Data) — split button
- **Left half:** hardware power cut to cameras, microphones, accelerometer.
- **Right half:** hardware **RF path kill** (antenna path break). Not “modem removed from the SoC” — modem is integrated; kill limits transmit/receive.

## Threat model (short)
**In scope:** FBE, userspace, left SMD, right RF kill, eSIM UX.  
**Not promised:** SoC/baseband audit, modem DMA while RF is killed, auto-boot from SATA if UFS dies, battery cert as already done.

## Cameras
IMX903 50 MP; tele 50 MP; ultrawide IMX858; DoF 12 MP; selfie 50 MP. No generative AI.

## Cooling
Magnetic cooler; triple VC *(concept)*; ventilation texture *(concept)*; xMEMS Lab XMC-2400 (3 V, 30 mW / 70 mW with driver).

## Kit
Finger cots; **USB → SATA with power**; frame case + silicone camera caps.
