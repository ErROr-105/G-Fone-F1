# G-Fone F1 — Beta 4 (Engineering Edition)

> Concept. Some specifications are design assumptions, not confirmed production components.  
> Everything marked *(concept)* requires verification with ODM, SoC vendor and certification labs.  
> Licenses: CERN-OHL-P v2 (hardware), GPLv3 (software), CC BY 4.0 (documentation).  
> Commercial use requires attribution.

---

## What is this

G-Fone F1 is a concept for a privacy-focused smartphone for people who are tired of everyone reading their data. Not a product, not an offer for sale, not a manufacturing guide. Just an engineering idea published for discussion, critique and improvement.

Target audience — privacy, repairability and “no-compromise hardware” enthusiasts. Not mass-market. Not enterprise. Not the Russian market.

---

## Main Specifications

- **SoC *(concept)*:** MediaTek Dimensity 9600 Pro, 2 nm, TSMC N2P. 2+3+3: 2× C2-Ultra up to 4.55 GHz, 3× C2-Pro up to 4.35 GHz, 3× C2-Pro up to 3.1 GHz. 34.5 MB cache. LPDDR6 + UFS 5.0. Announced 15.09.2026, devices by end of 2026.
- **Memory *(concept)*:** 16 GB LPDDR6 + 256 GB UFS 4.0. UFS 5.0 pending SoC and supplier confirmation.
- **Display:** 7" LTPS IPS QHD, high-end. Video up to 2K.
- **Battery:** 5S1P, 5 × 2500 mAh, 18.5 V, **46.25 Wh**. Prismatic Li-polymer. Battery Board with BMS, balancing, protection. X-Cross mounting.
- **Charging:** 80 W PSU, efficiency ≈ 95% (~76 W to battery). 0–80% ≈ 29 min; 0–100% ≈ 45–50 min with screen off.
- **Connectivity:** 1× nanoSIM + 1× microSD up to 1 TB + eSIM + BT connection to external satellite terminals. Direct satellite modem not claimed.
- **Price:** €3,200 (indicative for a niche flagship).

### Why 2500 mAh is not a typo

5S1P means 5 series cells of 2500 mAh each. Pack voltage 18.5 V. Energy 46.25 Wh. This is **2.4× more** than Galaxy S24 Ultra (19.25 Wh) or Xiaomi 14 Pro (18.8 Wh). Equivalent at 3.7 V is **12,500 mAh**.

Marketing trap: writing “2500 mAh” in large font is suicide. Writing “46.25 Wh / 12,500 mAh eq.” is honest and strong. Prismatic cells give simple isolation, flat thermal contact and mature BMS.

---

## Cameras

- **Main *(concept)*:** 50 MP Sony IMX907, f/1.4, OIS.
- **Telephoto *(concept)*:** 50 MP IMX890 or smaller, f/1.4, OIS.
- **Ultrawide *(concept)*:** 50 MP IMX858, f/1.4.
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
- Triple VC (IceLoop) in rear cover.
- 1.3 mm thermal pad. Graphite on SoC — screw-mounted.
- **Seals:** VMQ/LSR Shore A40 (main, spring-damped) + EPDM Shore A50–60. Multi-contour + mechanical clamp. 2 spare sets included.
- **Telescopic antenna *(concept)*:** polycarbonate shaft, antenna cap. Requires: IP69 extended/retracted, drainage, seal replacement schedule, separate SAR/EMC tests. In series — either separate chassis revision or accessory.

### Fins *(concept)*

- 12 trapezoidal fins. Height 2 mm, gap 2 mm, base thickness 1.2 mm, tip 0.6 mm, radius 0.2–0.3 mm.
- Location: lower 2/3 + side zones. Camera zone and engraving strip remain smooth.
- Effect: +30–35% dissipation area; forced convection when air moves; bending stiffness; tactile grip.
- Finish: Type III Class 2 Matte black anodizing (20–50 µm, no paint) + graphene (hydrophobicity, +5–10% radiation).
- Link to VC: copper foil or heat pipe over full area, not only through screws.

### Anti-Burn thermal stabilization *(concept)*

- Piezoelectric MEMS micropumps (20–30 kHz) for internal convection.
- Redistribute heat, equalize gradient, remove local hotspots (SoC, Battery Board). Surface peak −5…8 °C. IEC 62368-1 compliant.
- 0.1–0.3 W, silent, no moving parts, closed loop — IP69 preserved.
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
- **FDE:** full disk encryption.

---

## Patent Risks (summary)

- **SEP 5G:** 10–15% of retail. FTO audit before start. ODM with SEP pool is realistic path.
- **Motorola US 12,308,512 B2:** telescopic antenna. Design-around or license.
- **US 20250357560 A1:** 5S1P for power tools. Different field, but broad claims.
- **MEMS cooling:** Murata, ST, Frore Systems. FTO.
- **LED button illumination:** Samsung, LG, Motorola. FTO.
- **SK6812:** Worldsemi, APA Electronic. FTO.
- **Chassis fins:** thermal design FTO.
- **G-Fone trademark:** check Nice classes 9 and 38 (India, Gee Pee Ess).
- **Qualcomm risk:** even with MediaTek SoC — address in FTO.

Details in LEGAL.md and PATENTS.md.

---

## Beta 4 Status

- **Feasible:** chassis, removable cover, VC, fins, Type III anodizing + graphene, LineageOS-based, eBPF filter, UnifiedPush, FDE, SK6812 IP65 (lines), SMD 4020 RGB IP65 (button).
- **Concept:** 2 nm SoC, LPDDR6, UFS 5.0, 5S1P 18.5 V, 80 W, triple VC, telescopic antenna, series fins, MEMS micropumps, multi-mode LED button, RGB Thermal Hue lines.
- **Legal risk:** SEP 5G, US 12,308,512 B2, US 20250357560 A1, MEMS cooling, LED illumination, SK6812, RTRCA/SORM incompatibility framing, Zeiss, trademarks, fins.
- **Licenses:** CERN-OHL-P v2 (hardware), GPLv3 (software), CC BY 4.0 (documentation).
- **Beta 4 changes:** SK6812 IP65 for lines; SMD 4020 RGB IP65 for button; Work Profile removed; Russian block rephrased as incompatibility; licenses section and patent analysis updated.

---

## How to Contribute

- **Allowed:** CAD, thermal simulations, software, BMS, documentation, tests, translations.
- **Not allowed:** patent circumvention suggestions, calls to violate laws, specific blacklists, political statements.
- **Contribution license:** CERN-OHL-P v2 / GPLv3 / CC BY 4.0 depending on type.
- **Code of conduct:** respect, no politics, no toxicity.

---

> **Disclaimer.** This is a concept. Not a product. Not an offer for sale. Not a manufacturing guide. All specifications are design assumptions. The device is not certified. Patent risks are described in LEGAL.md and PATENTS.md. No FTO audit has been performed. The author is not liable for any consequences of using these materials. Users are responsible for compliance with the laws of their jurisdiction.
