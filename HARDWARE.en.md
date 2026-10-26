# HARDWARE

## Main Specifications
- **SoC:** MediaTek Dimensity 9600 Pro, 2 nm, TSMC N2P. 2+3+3. LPDDR6 + UFS 5.0. (announced September 2026)
- **Memory:** 16 GB LPDDR6 + 256 GB UFS 4.0 (UFS 5.0 as availability allows).
- **Display:** 6.77" LTPS IPS QHD, high-end.
- **Battery:** 5S1P, 5 × 2500 mAh, 18.5 V, 46.25 Wh. Prismatic Li-polymer. **X-Cross** mounting. Battery Board: BMS + **active balancing** (charge transfer between cells). (5S1P is serial in drones/RC; unusual for smartphones)
- **Charging / PSU path:** 80 W, efficiency ≈ 95%. Charge path and power path are designed for the **18.5 V (5S1P) pack**, not classic **3.7 V** single-cell.
- **Protection:** IP69 / IP69K (with case).
- **Chassis:** 7075-T6 aluminum, glue-free. Small **steel ring** in the chassis — seat for **magnetic active cooling** (detachable cooler).

## Why 2500 mAh is not a typo?
5S1P delivers 46.25 Wh. This is ≈3× more (exact 2.9800257731958×) than Galaxy S24 (typical capacity 4000 mAh, official 15.52 Wh). Equivalent at 3.7 V is 12,500 mAh. Prismatic cells: simple isolation, flat thermal contact, mature BMS.

## X-Cross
**X-Cross** is an internal metal cross-shaped part that retains and clamps the prismatic cells of the 5S1P pack on the Battery Board: pack stiffness, even pressure, less play under impact/flex. Not decoration — a structural battery hold-down.

## BMS and cell balancing (5S1P)
In a series string, pack capacity is limited by the **weakest cell**. Without balancing, SOC/voltage spread grows and one cell hits limits first.

- **Monitoring:** voltage and temperature of **each** of the 5 cells; pack current.
- **Balancing (baseline):** **active** (charge transfer between cells) — required for 5S in this concept.
- **Why not passive:** bleed burns excess energy in resistors → **local cell/board overheating** and **lower efficiency**. Active charge transfer equalizes SOC **without** dissipating heat into the pack, cuts local hotspots, and yields **higher balancing and pack-charge efficiency**.
- **Passive** (bleed) — not the concept baseline.
- **Protection:** per-cell OV/UV, OT, OC, short.

Battery Board: BMS + balancing + protection; 80 W charge path and HV front-end are separate.

## Power / PMIC (partial integration)
- **Architecture:** hybrid — not one monolithic PMIC for everything; domain split.
- **High-voltage front end (5S1P → bus):** step-down from 18.5 V to an intermediate bus (~5–9 V) at high efficiency; separate path for 80 W charging and BMS balancing.
- **Filter choke:** located **in the phone** (not in the external PSU) — LC/filter on the charge-path input and/or after the HV step-down; the wall adapter is the 80 W source; filtering inductance sits on the device boards.
- **SoC core rails (CPU / GPU / NPU):** partial integration of an **advanced multiphase digital buck controller** + power stages on the main rails (Vcore / GPU / NPU). AVS/DVS coordinated with MediaTek DVFS; fast transient response for 2 nm loads.
- **Other rails:** companion PMIC / discrete regulators (LPDDR6, RF, ISP/cameras, display, always-on domains).
- **Rationale:** 5S1P plus a flagship 2 nm SoC do not fit a classic single-cell phone PMIC well; multiphase on hot rails improves efficiency and thermal headroom; companions simplify sourcing, FTO and repair.
- **Status:** multiphase controllers and HV bucks are serial technologies; **the system build for 18.5 V + Dimensity 9600 Pro is an engineering choice** (needs ODM validation, layout, thermal and EMC).

## Cameras
- Main: 50 MP Sony IMX903, f/1.4, OIS.
- Telephoto: 50 MP, f/1.4, OIS.
- Ultrawide: 50 MP IMX858, f/1.4.
- DoF: 12 MP.
- Selfie: 50 MP.
- No generative AI.

## Cooling
- **Magnetic active cooling:** small **steel ring** in the chassis (ferromagnetic seat). Detachable active cooler attaches **via magnets**, no glue or screws at the ring.
- Triple vapor chamber *(concept)*, **bridges (перемычки)** on the rear panel *(concept)* — short metal segments (same look as the one just below SMD), diamond lattice without crossings; roughly **~+25–35%** more air-contact area on the panel vs a flat surface (estimate), graphene coating.
- **xMEMS Lab XMC-2400** — piezo MEMS micropump: **3 V**, **30 mW** (pump); with driver — **70 mW**. Serial component (not a concept). Thermal gradient equalization; silent, no moving parts.

## Kit and case
- **Plain-fabric finger cots** in the box. 7075-T6 aluminum is extreme at heat transfer — the chassis can feel ice-cold or burning hot. Finger cots are **safety** for bare-metal handling, not a fashion accessory.
- **Case** is a **frame with grip** (not a full soft sleeve). The case kit includes **mid-price silicone camera caps** — scratch protection for the lens modules.
