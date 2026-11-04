# G-Fone F1 — Beta 6.3.7 (Engineering Edition)

> Concept. Not a product. Licenses: CERN-OHL-P v2 / kernel GPLv2-only / userspace GPLv3 / Lineage Apache 2.0 / CC BY 4.0.

## Main Specifications

- **SoC:** Dimensity 9600 Pro, 2 nm. LPDDR6 + UFS 5.0.
- **Memory (internal only):** 16 GB LPDDR6 + **256 GB UFS 4.0** (no microSD slot).
- **Display:** 6.77" LTPS IPS QHD.
- **Battery:** 5S1P, 46.25 Wh. **X-Cross**; active BMS; shunt + per-cell NTC.
- **Charging:** 80 W **wired**. **No wireless charging** — efficiency many times worse; coil EMF ruins the compass; strong local heat is unsafe for the 5S1P pack. Half-joke: *under a burner, nothing living remains*.
- **Connectivity / slots:** **no mechanical SIM or microSD slots**. Cellular — **eSIM only** (up to 2 profiles — per ODM). BT to external satellite terminals.
- **Storage:** internal **256 GB UFS 4.0 only**; expansion via **USB Host** (any size). **USB → SATA with power** in the box.
- **Chassis:** 7075-T6; steel ring magnetic cooler; **ventilation texture** (directional micro-channels, not through-holes).

### Why No microSD?
- Modern design philosophy: **flexibility through standards (USB)**, not proprietary slots.
- **Repairability:** external storage remains independent of internal UFS.
- **Cost efficiency without compromising capability:** 256 GB UFS 4.0 inside; capacity outside is the user’s choice.

### USB Host Storage: User-Chosen Flexibility
There is **no microSD slot** — users select their own external SSD via USB adapter instead.

- **User controls storage capacity** (example: Kingston 2 TB, or any USB SSD).
- **Future-proof:** USB 3.2 / open standards, not a proprietary card slot.
- **Repairability:** data is independent from internal storage.
- **Included:** **USB → SATA adapter with power** (2.5″/3.5″).
- Connect any USB SSD; **G-Fone F1 operates as a tool, not a consumer appliance.**

### eSIM: Privacy-First Control
Custom eSIM implementation with **user-controlled** restrictions:

- Users can **activate/deactivate profiles only**.
- Profile deletion, modification, and telemetry are **blocked** without **explicit** user consent.
- All operations are **logged locally** (immutable log).
- **No hidden operator actions.**
- **eSIM is fully independent of ecosystems** (Apple/Google/OEM).

*G-Fone F1 respects user agency — the device serves the user, not carriers.*

## Beta 6.3.7 Status

**USB Host Storage** (user-chosen flexibility); **eSIM: Privacy-First Control**; **Why No microSD?**. (from 6.3.6: no wireless; eSIM outside ecosystems).

> **Disclaimer.** Concept only. Not a product.
