# G-Fone F1 — Beta 6.3.8 (Engineering Edition)

> Concept. Not a product. Licenses: CERN-OHL-P v2 / kernel GPLv2-only / userspace GPLv3 / Lineage Apache 2.0 / CC BY 4.0.

## Main Specifications

- **SoC:** Dimensity 9600 Pro, 2 nm. LPDDR6 + UFS 5.0. (*projected / concept assumption — cite vendor when locking the BOM.*)
- **Memory (internal only):** 16 GB LPDDR6 + **256 GB UFS 4.0** (no microSD slot).
- **Display:** 6.77" LTPS IPS QHD (conscious IPS choice, not marketed as “AMOLED flagship class”).
- **Battery:** 5S1P, 46.25 Wh. **X-Cross**; active BMS; shunt + per-cell NTC. Certification (IEC 62133, UN38.3, etc.) = **ODM gate**.
- **Charging:** 80 W **wired**. 0–80% ≈ 29 min (**calculated target**); 0–100% ≈ 45–50 min (**estimate**, CV phase; not a lab measurement). **No wireless charging** — lower efficiency (~60–75% vs ~90–95% wired) and local heat undesirable for 5S1P; coil EMF also hurts the magnetometer.
- **Connectivity / slots:** **no mechanical SIM or microSD**. Cellular — **eSIM only**. BT to external satellite terminals.
- **Storage:** internal **256 GB UFS 4.0 only**; expansion via **USB Host**. **USB → SATA with power** in the box (2.5″ from adapter/USB; **3.5″ needs separate 12 V** from the adapter — not from the phone or the 80 W charge budget).
- **Chassis:** 7075-T6; steel ring magnetic cooler; **ventilation texture**.

### Why No microSD?
- **Fewer failure points** (tray, contacts, moisture path) → reliability / IP — **not** “easier mainboard repair.”
- Flexibility via **USB standards**; capacity outside is user-chosen.
- UFS failure does **not** auto-boot from SATA without a dedicated boot design.

### USB Host Storage: User-Chosen Flexibility
Any USB SSD/HDD; example Kingston 2 TB. USB 3.2 / open standards. Data independent of internal UFS. **G-Fone F1 is a tool, not a consumer appliance.** Mobile use → 2.5″ SSD; 3.5″ → desk/lab with external 12 V.

### eSIM: Privacy-First Control
Activate/deactivate only; delete/modify/telemetry blocked without explicit consent; local immutable OS log; ecosystem-independent (Apple/Google/OEM).

**Honest baseband note:** OS-side eSIM policy does **not** prove absence of modem-side behavior. The modem is integrated in the SoC — see **Threat model**.

### SMD (Stop Meta Data) — split button
One physical key, **two independent halves**:

| Half | Function | Hardware action |
|------|----------|-----------------|
| **Left (main)** | Stop Meta Data | **Cuts power** to cameras, microphones, accelerometer (not software mute) |
| **Right (separate)** | RF path kill | **Hardware break of the RF path** (antenna lines): no transmit/receive on cellular/Wi‑Fi/BT radio while engaged. **Not** “modem removed from the SoC” — modem is integrated; kill limits **radiation/reception**, not internal baseband logic |

RGB indication on SMD 4020 + SK6812 lines. Mindustry load-arrows LED easter egg unchanged.

## Threat model (honest bounds)

**In scope:** FBE; no GApps by default; **left SMD** sensor power cut; **right SMD** RF path kill; eSIM UX; open hardware intent (CERN-OHL); USB Host as a tool.

**Out of scope / not promised:** audit of SoC/baseband silicon (global limit); modem DMA/internal logic while RF is killed; auto-boot from SATA if UFS dies; battery certification as already done.

For a tech audience, honest threat bounds beat slogan-level “full privacy.”

## Support & software caveats
- Patch intent: community + ODM SLA (**years TBD** until ODM contract).
- Banking / Play Integrity: without GApps some apps may fail; workarounds are the user’s responsibility.
- **vs GrapheneOS + Pixel:** this concept is about **open hardware**, 5S1P, glue-free chassis, split SMD (sensors + RF path), USB Host tool-device — not another de-Googled Pixel.

## Beta 6.3.8 Status

Threat model; split SMD (left sensors / right RF path kill); honest baseband; USB→SATA 2.5″/3.5″ power; calculated charge times; microSD = reliability framing; support/banking caveats. (from 6.3.7)

> **Disclaimer.** Concept only. Not a product. See LEGAL.md / PATENTS.md.
