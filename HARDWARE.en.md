# HARDWARE

## Main Specifications
- **SoC:** MediaTek Dimensity 9600 Pro, 2 nm. LPDDR6 + UFS 5.0.
- **Memory (internal only):** 16 GB LPDDR6 + **256 GB UFS 5.0** (no microSD).
- **Display:** 6.77" LTPS IPS QHD.
- **Battery:** 5S1P, 46.25 Wh. **X-Cross**. Active BMS. Cert = **ODM gate**.
- **Charging:** 80 W **wired**. No wireless. Path **18.5 V**. Times = calculated/estimate.
- **Protection:** IP69 / IP69K. **Chassis:** 7075-T6 glue-free; steel ring cooler.

## BMS
Per-cell V; NTC on each cell; pack shunt. **Active** balancing baseline.

## Power / PMIC
HV 18.5 V; filter choke **in the phone**; multiphase on SoC hot rails.

## Connectivity and storage
- No SIM/microSD slots. **eSIM only** (Privacy-First in userspace; does not prove absence of baseband-side behavior).
- Internal: **256 GB UFS 5.0**.
- **USB Host** + **USB → SATA with power** (2.5″; 3.5″ needs separate **12 V**).
- **Why No microSD?** reliability/IP, not mainboard repairability.

## DualBIOS (spare boot chip) *(engineering node)*
- **Non-UFS** device with its **own** boot firmware.
- Chain: **SoC Boot ROM** → normally UFS 5.0; on UFS failure → DualBIOS **notifies** and **offers** to boot Android from an external USB/SATA disk if an image was written.
- Not “unbrick from nothing”; secure-boot policy is ODM’s.

## SMD — split button
- **Left:** power cut to cameras/mic/accelerometer.
- **Right:** **RF path kill** (antenna path). Modem stays in SoC; kill = no TX/RX.

## Threat model (short)
**In scope:** FBE, SMD, RF kill, eSIM UX, DualBIOS fallback.  
**Not promised:** SoC/baseband audit; external boot without image/DualBIOS; battery cert as already done.

## Cameras / cooling / kit
IMX903 etc. Magnetic cooler; VC *(concept)*; XMC-2400. Finger cots; USB→SATA; frame case.
