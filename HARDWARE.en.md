# HARDWARE

## Main Specifications
- **SoC:** MediaTek Dimensity 9600 Pro, 2 nm, TSMC N2P. 2+3+3. LPDDR6 + UFS 5.0. (announced September 2026)
- **Memory:** 16 GB LPDDR6 + 256 GB UFS 4.0 (UFS 5.0 as availability allows).
- **Display:** 7" LTPS IPS QHD, high-end.
- **Battery:** 5S1P, 5 × 2500 mAh, 18.5 V, 46.25 Wh. Prismatic Li-polymer. (5S1P is serial in drones/RC; unusual for smartphones)
- **Charging:** 80 W, efficiency ≈ 95%.
- **Protection:** IP69 / IP69K (with case).
- **Chassis:** 7075-T6 aluminum, glue-free.

## Why 2500 mAh is not a typo?
5S1P delivers 46.25 Wh. This is 2.4× more than Galaxy S24 Ultra and more than Galaxy S26. Equivalent at 3.7 V is 12,500 mAh. Prismatic cells: simple isolation, flat thermal contact, mature BMS.

## Power / PMIC (partial integration)
- **Architecture:** hybrid — not one monolithic PMIC for everything; domain split.
- **High-voltage front end (5S1P → bus):** step-down from 18.5 V to an intermediate bus (~5–9 V) at high efficiency; separate path for 80 W charging and BMS balancing.
- **SoC core rails (CPU / GPU / NPU):** partial integration of an **advanced multiphase digital buck controller** + power stages on the main rails (Vcore / GPU / NPU). AVS/DVS coordinated with MediaTek DVFS; fast transient response for 2 nm loads.
- **Other rails:** companion PMIC / discrete regulators (LPDDR6, RF, ISP/cameras, display, always-on domains).
- **Rationale:** 5S1P plus a flagship 2 nm SoC do not fit a classic single-cell phone PMIC well; multiphase on hot rails improves efficiency and thermal headroom; companions simplify sourcing, FTO and repair.
- **Status:** multiphase controllers and HV bucks are serial technologies; **the system build for 18.5 V + Dimensity 9600 Pro is an engineering choice** (needs ODM validation, layout, thermal and EMC).

## Cameras
- Main: 50 MP Sony IMX907, f/1.4, OIS.
- Telephoto: 50 MP, f/1.4, OIS.
- Ultrawide: 50 MP IMX858, f/1.4.
- DoF: 12 MP.
- Selfie: 50 MP.
- No generative AI.

## Cooling
- Triple vapor chamber *(concept)*, fins (12 ribs) *(concept)*, graphene coating.
- MEMS micropumps (real technology, suppliers such as Goertek) for gradient equalization. **Driver power: 0.1–0.3 W** (critical for energy efficiency; silent, no moving parts).
