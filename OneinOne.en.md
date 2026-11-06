# G-Fone F1 — Beta 6.3.9 (Engineering Edition)

> Concept. Not a product. Licenses: CERN-OHL-P v2 / kernel GPLv2-only / userspace GPLv3 / Lineage Apache 2.0 / CC BY 4.0.

## Main Specifications

- **SoC:** Dimensity 9600 Pro, 2 nm. LPDDR6 + UFS 5.0. (*projected / concept assumption.*)
- **Memory (internal only):** 16 GB LPDDR6 + **256 GB UFS 5.0** (no microSD).
- **Display:** 6.77" LTPS IPS QHD (conscious IPS choice).
- **Battery:** 5S1P, 46.25 Wh. **X-Cross**; active BMS; shunt + per-cell NTC. Cert = **ODM gate**.
- **Charging:** 80 W **wired**. 0–80% ≈ 29 min (**calculated**); 0–100% ≈ 45–50 min (**estimate**, CV). **No wireless charging**.
- **Connectivity:** no mechanical SIM/microSD; **eSIM only**.
- **Storage:** **256 GB UFS 5.0 only**; **USB Host** expansion; **USB → SATA with power** in the box (2.5″ from adapter; **3.5″ needs separate 12 V**).

### Why No microSD?
Fewer failure points → reliability/IP. On UFS failure → **DualBIOS** (notify + offer external Android boot if an image was written).

### USB Host Storage: User-Chosen Flexibility
Any USB SSD/HDD. Tool, not appliance. Mobile → 2.5″; 3.5″ → desk/lab with external 12 V.

### DualBIOS (spare boot chip) *(engineering node)*
Separate **non-UFS** device with its own boot firmware (PC DualBIOS analogy — not AMI/Award).

**Boot chain (simplified):**
1. **SoC Boot ROM** (fused in the processor) — first immutable stage.
2. Normal path: bootloader / OS from **internal UFS 5.0**.
3. On **UFS failure or unreadability**: **DualBIOS chip** (firmware in the chip’s own memory) → **notifies** the user and **offers to boot Android from an external drive** if a compatible image was written via USB Host.

**Notes:** Not “unbrick from nothing” — external disk must already hold a bootable Android/recovery. SoC Boot ROM stays primary; DualBIOS is fallback **off UFS**. ODM validation required.

### eSIM: Privacy-First Control
Activate/deactivate only; explicit consent for delete/modify/telemetry; local OS log; ecosystem-independent. Does **not** prove absence of baseband-side behavior — see Threat model.

### SMD (Stop Meta Data) — split button
| Half | Function |
|------|----------|
| **Left** | Power cut to cameras / mic / accelerometer |
| **Right** | **RF path kill** (antenna path). Not “modem removed from SoC” |

## Threat model (honest bounds)

**In scope:** FBE; left SMD; right RF path kill; eSIM UX; USB Host; **DualBIOS** fallback boot path.

**Out of scope:** SoC/baseband audit; modem DMA while RF killed; external boot **without** a pre-written image / **without** DualBIOS; battery cert as already done.

## Support & software caveats
Patch intent: community + ODM SLA (**TBD**). Banking/Play Integrity may fail without GApps. vs GrapheneOS+Pixel: open hardware, 5S1P, split SMD, DualBIOS, USB Host tool-device.

## Beta 6.3.9 Status

**UFS 5.0** internal (UFS 4.0 removed); **DualBIOS** spare boot chip — notify + offer external Android boot on UFS failure. (from 6.3.8)

> **Disclaimer.** Concept only. Not a product.
