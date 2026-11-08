# G-Fone F1 — Beta 6.3.13 (Engineering Edition)

> Concept. Parts of the specification are design assumptions, not confirmed production parts.  
> Anything marked *(concept)* needs ODM and lab validation.  
> Licenses: CERN-OHL-P v2 (hardware); **kernel GPLv2-only**; **G-Fone userspace GPLv3**; Lineage/AOSP **Apache 2.0**. Components are distributed **separately**: Apache code is **not** combined with the GPLv2 kernel (Apache 2.0 and GPLv2 are **incompatible** if merged into one program; Apache 2.0 is compatible with GPLv3). Not relicensing. CC BY 4.0 (docs).  
> Commercial use requires attribution.

---

## What is this

G-Fone F1 is a privacy / repairability / no-compromise hardware **concept** for **tech users**. Not a product, not an offer, not a manufacturing guide. Open for critique and iteration. Not mass-market. Not enterprise.

---

## Main specifications

- **SoC:** MediaTek Dimensity 9600 Pro, 2 nm, TSMC N2P. 2+3+3: 2× C2-Ultra up to 4.55 GHz, 3× C2-Pro up to 4.35 GHz, 3× C2-Pro up to 3.1 GHz. 34.5 MB cache. LPDDR6 + UFS 5.0. (*projected / assumption — cite vendor when locking the BOM.*)
- **Memory (internal only):** 16 GB LPDDR6 + **256 GB UFS 5.0** (no microSD slot).
- **Display:** 6.77" LTPS IPS QHD (conscious IPS choice, not sold as an “AMOLED flagship”). Video up to 2K.
- **Battery:** 5S1P, 5 × 2500 mAh, pack **nominal ~18.5 V** (5×3.7), **full charge ~21 V** (5×4.2). Energy **46.25 Wh** (calculated). Prismatic Li-polymer. **X-Cross** = metal cross **mechanics** holding cells (not the BMS IC). **BMS:** active balancing, OV/UV/OT/OC/short; per-cell V; **NTC on each of 5 cells**; pack **shunt**. Prefer a **documented controller** (e.g. TI BQ-class / equivalent with datasheet + drivers; ODM choice). 5S1P is common in drones/RC, atypical in phones. Pack certification (IEC 62133, UN38.3, etc.) = **ODM gate**.
- **Charging:** up to 80 W **wired**, ≈95% efficiency. Path for **5S1P**: nominal ~18.5 V, top **~21 V** → **USB PD PPS** (or equivalent); fixed 20 V PD does **not** cover full CV. 0–80% ≈ 29 min; 0–100% ≈ 45–50 min screen-off = **calculated target / estimate**, not a lab measurement (CV phase matters). ~80 W into 46.25 Wh ≈ **1.6C** — **aggressive** for phone-class prismatic cells → **gentle default** (e.g. 40–50 W) and cycle-life target **TBD with ODM**. **No wireless charging.** Not a 3.7 V single-cell path.
- **Why no wireless:** (1) efficiency (~60–75% wall-to-battery vs ~90–95% wired); (2) local coil heat undesirable for 5S1P; (3) coil EMF hurts the magnetometer (7075 + X-Cross already a hard environment).
- **Connectivity / slots:** **no mechanical SIM or microSD**. Cellular = **eSIM only** (up to 2 profiles — ODM). BT to external satellite terminals. No onboard satellite modem claimed.
- **Storage:** internal **256 GB UFS 5.0 only**; expansion via **USB Host**. Kit includes **USB → SATA with power** (see USB Host).
- **Price:** €3200 (niche flagship / tool-device guide).

### Why no microSD?
Fewer failure points (tray, contacts, moisture path) → **reliability / IP**, not “easier mainboard repair.” Flexibility via **USB standards**. On UFS failure → **DualBIOS** (notify + external boot if image + AVB policy). Without that, UFS death is a service scenario.

### USB Host Storage: user-chosen flexibility
- User picks capacity (e.g. Kingston 2 TB USB SSD).
- USB 3.2 / open standards.
- Data not glued to internal UFS.
- **2.5″ SSD:** prefer **phone USB-C / PD** or kit adapter **without** a separate 12 V wall; else 5 V from kit PSU.
- **3.5″ HDD:** **separate 12 V** from the adapter — not from the phone, not from the 80 W charge budget (desk/lab).
- **Signed / authenticated storage *(policy, concept)*:** optional signature/access policy aligned with AVB external-boot.
- Kit: USB→SATA under those rules. **G-Fone F1 is a tool, not a consumer appliance.**

### DualBIOS *(engineering node)*

**Problem:** production **SoC Boot ROM** usually **cannot** boot from USB mass-storage alone. A spare medium does not hand control to the CPU without a **secondary loader** the SoC accepts.

**Design intent:**
1. **SoC Boot ROM** (immutable, fused in the processor) — always first.
2. Normal path: **UFS 5.0** (loader + AVB + OS).
3. **DualBIOS chip** — own firmware (typically **SPI NOR**), fallback boot source after UFS failure (mux/strap/order = ODM + SoC policy).
4. DualBIOS brings up a **minimal secondary loader** that **notifies** UFS failure and may continue from USB Host **only** under AVB policy — not “magic USB boot from Boot ROM.”

**Verified Boot / AVB:**
- **A:** external image signed with **user-owned keys** and verified; or
- **B:** verification disableable only with **explicit warning** (preferably physical confirm).
- Without A or B, DualBIOS is **not** privacy-safe recovery.

**Notify if the panel is dead:** **RGB SMD / SK6812** and/or **USB device-side status**.

**Status:** engineering node; needs MediaTek boot ROM / fuse policy, secure boot, and UX validation.

### eSIM: Privacy-First Control
Userspace: activate/deactivate only; delete/modify/telemetry blocked without **explicit** consent; local OS log; independent of Apple/Google/OEM store lock-in.

**Honest baseband / eUICC:** profiles use eUICC / SM-DP+ / OTA; **modem and eUICC firmware are closed**. OS policy ≠ modem-side guarantee. “Immutable” userspace log without **TEE/SE + hash-chain** is not cryptographic immutability. See **Threat model**.

### Why 2500 mAh is not a typo
5S1P → 46.25 Wh ≈ **3×** Galaxy S24 (15.52 Wh); exact ratio **2.9800257731958×**. Equivalent at 3.7 V = **12,500 mAh** — an **equivalent calculation**, not a single-cell rating.

### X-Cross / BMS / PMIC
**X-Cross** = mechanical cell retention only. **BMS** = active balancing + shunt + per-cell NTC on a **documented** IC preferred. PMIC: HV front-end ~18.5 V nominal / ~21 V full; **filter choke in the phone**; multiphase on SoC hot rails; companions for other domains. Partial PMIC *(concept / ODM)*.

### Kit
Fabric **finger cots** (7075 thermal protection for bare metal — not “cut protection”); **USB → SATA with power**; frame case + silicone camera caps.

---

## Cameras

Main 50 MP Sony **IMX903**; tele 50 MP; ultrawide 50 MP **IMX858**; DoF 12 MP; selfie 50 MP. **No generative AI.**

Typical mode: **quad-Bayer binning 50 → ~12.5 MP** (noise/DR); full 50 MP is a separate mode.

### Open-source HDR Stacking *(userspace, GPLv3)*
- Capture a **burst / bracketed series** and **merge on-device**.
- Entirely in **userspace**, **GPLv3** (not mixed into the GPLv2 kernel).
- Open algorithms (alignment + merge / exposure fusion) — **no** proprietary ISP-AI, **no** cloud.
- Goal: controllable dynamic range without shipping frames to a vendor.

---

## Chassis and cooling

7075-T6, glue-free; steel ring for **magnetic cooler**; **IP69 / IP69K**. Triple VC *(concept)*. **Ventilation texture** *(concept)*: directional micro-channels (**not** through-holes). **xMEMS Lab XMC-2400**: 3 V, 30 mW; 70 mW with driver. Telescopic antenna *(concept)*; no onboard satellite modem claimed.

---

## Unique hardware

### SMD = **Stop Meta Data** (not surface-mount device) — split button

| Half | Function | Hardware |
|------|----------|----------|
| **Left** | Stop Meta Data | **Cuts power** to cameras, mics, accelerometer (not software mute) |
| **Right** | RF kill L1 / L2 | See levels below |

**RF kill levels:**
1. **Baseline (required):** hardware **RF path kill** (antenna break) → no OTA TX/RX. Modem **stays in the SoC**; domain power and **DMA to RAM may remain**. Kill ≠ memory isolation ≠ “modem excised from the SoC.”
2. **ODM target (only if a separate baseband/eUICC rail exists):** hardware **rail kill**. Still not silicon-idle proof, stronger than path-only.
3. No separate rail → ship **L1 only**; do not market L2.

RGB indication (Privacy / Charge / Thermal Hue) on SMD 4020 + SK6812. Left/right vs normal orientation (screen to user, antenna top); final CAD owns placement.

### Easter egg: Mindustry load arrows
While **Mindustry** is on its load screen, SMD + SK6812 repeat the in-game load-arrow animation in the same light/color. Not tied to device boot.

---

## Software

LineageOS/AOSP-based, **no GApps** by default. **FBE**. Kernel **GPLv2-only**. G-Fone userspace (incl. **HDR Stacking**) **GPLv3**. Lineage/AOSP **Apache 2.0**. Separate works — Apache 2.0 not merged with GPLv2 kernel; Apache OK with GPLv3. microG etc. **optional by user**, not preinstalled.

---

## Threat model (honest bounds)

**In scope:** FBE; left SMD sensor power cut; RF kill **L1 always**, **L2 only if rail exists**; eSIM UX (userspace); USB Host + optional signed-storage; DualBIOS **only** with AVB user-keys or explicit disable+warning; **local HDR Stacking** without cloud; open-hardware intent (CERN-OHL).

**Out of scope:** SoC/baseband/eUICC silicon audit; **no modem DMA** on path-only kill; L2 without a real rail; modem/eUICC actions outside the OS; external boot without image/AVB policy; battery cert as already done; crypto-immutable log without TEE/SE.

---

## Support caveats

Patch intent: community + ODM SLA (**years TBD**). Banking / Play Integrity may fail without GApps. **vs GrapheneOS + Pixel:** open hardware, 5S1P, glue-free 7075, split SMD, DualBIOS, USB Host tool-device, local HDR — not another de-Googled Pixel.

---

## Beta 6.3.13 status

**Implementable (with ODM/cert gates):** Dimensity 9600 Pro (projected), UFS 5.0, 5S1P, PPS ~21 V, documented-class BMS + X-Cross, eSIM Privacy-First (userspace), USB Host, split SMD (**RF L1**), DualBIOS+AVB, **HDR Stacking (userspace GPLv3)**.

**Concept:** triple VC, telescopic antenna, ventilation texture, partial PMIC, LED modes, Mindustry easter egg, signed-storage policy, L2 rail kill.

**6.3.13 changes:** open-source HDR Stacking; **full OneinOne text restored** (no section truncation). From 6.3.12: RF L1/L2, USB 2.5″ PD, signed storage, BMS vs X-Cross split.

---

> **Disclaimer.** Concept only. Not a product. Not an offer for any specific market. See LEGAL.md and PATENTS.md.
