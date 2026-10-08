# G-Fone F1 — Beta 4 (Engineering Edition)

> Concept. Some specifications are design assumptions or non-standard combinations of existing technologies.  
> Everything marked *(concept)* requires additional verification with ODM and certification labs.  
> Licenses: CERN-OHL-P v2 (hardware), GPLv3 (software), CC BY 4.0 (documentation).  
> Commercial use requires attribution.

---

## What is this

G-Fone F1 is a concept for a privacy-focused smartphone for people who are tired of everyone reading their data. Not a product, not an offer for sale, not a manufacturing guide. Just an engineering idea published for discussion, critique and improvement.

Target audience — privacy, repairability and “no-compromise hardware” enthusiasts. Not mass-market. Not enterprise. Not the Russian market.

---

## Main Specifications

- **SoC:** MediaTek Dimensity 9600 Pro, 2 nm, TSMC N2P. 2+3+3: 2× C2-Ultra up to 4.55 GHz, 3× C2-Pro up to 4.35 GHz, 3× C2-Pro up to 3.1 GHz. 34.5 MB cache. LPDDR6 + UFS 5.0. Announced 15.09.2026, devices by end of 2026.
- **Memory:** 16 GB LPDDR6 + 256 GB UFS 4.0. UFS 5.0 as availability allows.
- **Display:** 7" LTPS IPS QHD, high-end. Video up to 2K.
- **Battery:** 5S1P, 5 × 2500 mAh, 18.5 V, **46.25 Wh**. Prismatic Li-polymer. Battery Board with BMS, balancing, protection. X-Cross mounting. (5S1P is serial in drones/RC; unusual for smartphones)
- **Charging:** 80 W PSU, efficiency ≈ 95% (~76 W to battery). 0–80% ≈ 29 min; 0–100% ≈ 45–50 min with screen off.
- **Connectivity:** 1× nanoSIM + 1× microSD up to 1 TB + eSIM + BT connection to external satellite terminals. Direct satellite modem not claimed.
- **Price:** €3,200 (indicative for a niche flagship).

### Why 2500 mAh is not a typo

5S1P means 5 series cells of 2500 mAh each. Pack voltage 18.5 V. Energy 46.25 Wh. This is **2.4× more** than Galaxy S24 Ultra (19.25 Wh) or Xiaomi 14 Pro (18.8 Wh). Equivalent at 3.7 V is **12,500 mAh**.

Marketing trap: writing “2500 mAh” in large font is suicide. Writing “46.25 Wh / 12,500 mAh eq.” is honest and strong. Prismatic cells give simple isolation, flat thermal contact and mature BMS.

### Power / PMIC — partial integration of an advanced controller

A classic single-cell phone PMIC does not fit **18.5 V (5S1P)** plus a 2 nm flagship’s hot rails well. Hence a **hybrid**:

- **HV front-end:** step-down 18.5 V → intermediate bus (~5–9 V); separate path for 80 W charging and BMS.
- **SoC core rails (CPU / GPU / NPU):** partial integration of an **advanced multiphase digital buck controller** + power stages on Vcore / GPU / NPU; AVS/DVS tied to MediaTek DVFS; fast transient response for 2 nm loads.
- **Other domains:** companion PMIC / discrete regulators (LPDDR6, RF, ISP/cameras, display, always-on).
- **Why:** efficiency and thermal headroom on hot rails; simpler sourcing, FTO and repair via companions.
- **Status:** multiphase and HV bucks are serial tech; **the 18.5 V + Dimensity 9600 Pro system build is an engineering choice** (ODM, layout, thermal, EMC).

---

## Cameras

- **Main:** 50 MP Sony IMX907, f/1.4, OIS.
- **Telephoto:** 50 MP IMX890 or smaller, f/1.4, OIS.
- **Ultrawide:** 50 MP IMX858, f/1.4.
- **DoF:** 12 MP, f/2.0, RGB + B&W, no generative AI.
- **Additional:** ToF + IR laser (Class 1) + flash.
- **Stabilization:** OIS on main modules.
- **Selfie:** 50 MP.
- **Glass:** Zeiss — only with a license.
- **AI:** no generative fill. Only HDR, noise reduction, stabilization.
- **Layout:** top-left main; top-right IR laser; mid-right telephoto; bottom-left flash; bottom-center DoF; bottom-right ultrawide.
- **Keep-out zone:** ≥ 7 mm around camera block. Fins outside lens area — otherwise glare, flare, thermal load on OIS and adhesive.

---

## Chassis and Cooling

- **Aluminum 7075-T6**, glue-free, all bolts removable.
- **Protection:** IP69 without case; IP69K with supplied case. Pressure equalization valve with membrane.
- Triple VC (IceLoop) *(concept)* in rear cover.
- 1.3 mm thermal pad. Graphite on SoC — screw-mounted.
- **Seals:** VMQ/LSR Shore A40 (main, spring-damped) + EPDM Shore A50–60. Multi-contour + mechanical clamp. 2 spare sets included.
- **Telescopic antenna *(concept)*:** polycarbonate shaft, antenna cap. Requires: IP69 extended/retracted, drainage, seal replacement schedule, separate SAR/EMC tests. In series — either separate chassis revision or accessory.

### Fins *(concept)*

- 12 trapezoidal fins. Height 2 mm, gap 2 mm, base thickness 1.2 mm, tip 0.6 mm, radius 0.2–0.3 mm.
- Location: lower 2/3 + side zones. Camera zone and engraving strip remain smooth.
- Effect: +30–35% dissipation area; forced convection when air moves; bending stiffness; tactile grip.
- Finish: Type III Class 2 Matte black anodizing (20–50 µm, no paint) + graphene (hydrophobicity, +5–10% radiation).
- Link to VC: copper foil or heat pipe over full area, not only through screws.

### Anti-Burn thermal stabilization

- Piezoelectric MEMS micropumps (20–30 kHz) for internal convection. (real technology; suppliers include Goertek and others)
- Redistribute heat, equalize gradient, remove local hotspots (SoC, Battery Board). Surface peak −5…8 °C. IEC 62368-1 compliant.
- **Driver power: 0.1–0.3 W** (important for energy efficiency). Silent, no moving parts, closed loop — IP69 preserved.
- Integration: between Main Board and Sub Board, above Battery Board copper tube.

---

## Unique Hardware Solutions

### SMD Button (Stop Meta Data)
Physical power cut-off for cameras, microphone and accelerometer. Multi-mode RGB indication:
- Privacy Mode: red.
- Charge Y-Fill: white → yellow → green.
- Thermal Hue: turquoise → yellow → orange → red (also routed to rear accent lines).

Addressable RGB SMD 4020, IP65. Accent lines: SK6812 IP65, 60 LEDs/m, side-emitting.

---

## Software

- **OS:** LineageOS-based, no GApps.
- **Pre-installed:** F-Droid, DuckDuckGo, Proton Mail.
- **Aurora Store:** not pre-installed. User installs. Responsibility on user.
- **Push:** optional gateway (UnifiedPush/WebSocket). Lawful intercept responsibility on app developers.
- **Russia compatibility:** officially not supplied. RTRCA and SORM requirements do not apply. Technical incompatibility, not a political statement.
- **E2EE:** X25519, AES-256-GCM / ChaCha20-Poly1305. Keys in TEE.
- **eBPF filter:** user privacy tool for tracker blocking.
- **FBE:** file-based encryption.

---

## Patent Risks (summary)

- **SEP 5G:** 10–15% of retail. FTO audit before start. ODM with SEP pool is realistic path.
- **Motorola US 12,308,512 B2:** telescopic antenna. Design-around or license.
- **US 20250357560 A1:** 5S1P for power tools. Different field, but broad claims.
- **MEMS cooling:** Murata, ST, Frore Systems, Goertek. FTO.
- **LED button illumination:** Samsung, LG, Motorola. FTO.
- **SK6812:** Worldsemi, APA Electronic. FTO.
- **Chassis fins:** thermal design FTO.
- **G-Fone trademark:** check Nice classes 9 and 38 (India, Gee Pee Ess).
- **Qualcomm risk:** even with MediaTek SoC — address in FTO.
- **PMIC / multiphase:** FTO on controllers and power stages (TI, Infineon, MPS, Richtek, etc. — ODM choice).

Details in LEGAL.md and PATENTS.md.

---

## Beta 4 Status

- **Feasible / serial technologies:** 2 nm SoC (Dimensity 9600 Pro), LPDDR6, UFS 5.0, 5S1P (unusual for phones), 80 W, multiphase buck + HV step-down (as components), MEMS micropumps (driver 0.1–0.3 W), 7075-T6 glue-free chassis, LineageOS-based, eBPF, UnifiedPush, FBE, SK6812 IP65, SMD 4020 RGB IP65.
- **Concept / rare solutions / system integration:** triple VC, telescopic antenna, ribs (12 fins), **partial advanced PMIC integration for 18.5 V + SoC hot rails**, multi-mode LED button + RGB Thermal Hue lines.
- **Legal risk:** SEP 5G, US 12,308,512 B2, US 20250357560 A1, MEMS cooling, LED illumination, SK6812, PMIC/multiphase FTO, RTRCA/SORM framing, Zeiss, trademarks, fins.
- **Licenses:** CERN-OHL-P v2 (hardware), GPLv3 (software), CC BY 4.0 (documentation).
- **Updates:** *(concept)* markers; FBE; MEMS driver power; **PMIC partial multiphase integration**; Work Profile removed; Russia block as technical incompatibility.

---

## How to Contribute

- **Allowed:** CAD, thermal simulations, software, BMS, **power/PMIC layout**, documentation, tests, translations.
- **Not allowed:** patent circumvention suggestions, calls to violate laws, specific blacklists, political statements.
- **Contribution license:** CERN-OHL-P v2 / GPLv3 / CC BY 4.0 depending on type.
- **Code of conduct:** respect, no politics, no toxicity.

---

> **Disclaimer.** This is a concept. Not a product. Not an offer for sale. Not a manufacturing guide. Specifications are design assumptions or combinations of existing technologies. The device is not certified. Patent risks are described in LEGAL.md and PATENTS.md. No FTO audit has been performed. The author is not liable for any consequences of using these materials. Users are responsible for compliance with the laws of their jurisdiction.
