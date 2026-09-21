# PATENTS

> This file is not legal advice. It describes risks and recommendations.  
> Commercialization requires a full FTO (Freedom to Operate) audit.

## SEP — Standards Essential Patents

**Scale.** More than 100,000 5G patent families are declared in the ETSI database. ~44.65% are actually implemented (for smartphones ~39.8% at 91.5% relevance).

**Players.** The top 20 rights holders control ~88% of declared families. Leaders: Huawei, Qualcomm, LG, Samsung, Ericsson — ~43%.

**Rates.** Aggregate 5G royalties reach $15–20 per device. With Wi-Fi, Bluetooth and codecs — 10–15% of retail price. Court decisions (ZTE v. Samsung) confirm 7.8–11.6% for 5G.

**FRAND.** Courts require good-faith negotiations. Avoidance may result in an injunction against sales.

**For G-Fone F1:** at a price of €3,200 the royalties are absorbed by margin, but require agreement with a pool of SEP licenses.

**SEP sources in the concept.** The concept assumes use of SEP licenses only from MediaTek (via Dimensity SoC), Nokia, Ericsson and Samsung. Qualcomm licenses are **not used** in the concept.

**Qualcomm risk.** Qualcomm actively defends its patent portfolio even when a device uses a SoC from another manufacturer (MediaTek etc.). There is a risk of claims under SEP and non-SEP patents related to 5G, RF front-end, modem and related technologies. This risk must be specifically addressed in the FTO audit. Risk reduction is possible through an ODM partner that has existing agreements or cross-licenses with Qualcomm.

## Hardware patents

- **Motorola US 12,308,512 B2** — reconfigurable antenna for expandable form factor (telescopic support). Direct risk for the telescopic antenna.
- **Huawei EP 4 020 705 B1** — antenna assembly for rollable displays. Lower but real risk.
- **US 20250357560 A1** (priority 2017) — 5S1P battery for power tools. Different field of use, but claim breadth creates risk.
- **MEMS cooling** — Murata, STMicroelectronics, Frore Systems.
- **LED button illumination** with charge and thermal indication — Samsung, LG, Motorola (“multi-mode button illumination”).
- **SK6812** — Worldsemi, APA Electronic, Shenzhen LED (addressable RGB strips).
- **Chassis fins** — FTO for thermal design of mobile devices.

## Trademarks

- **Zeiss** — only with a separate license.
- **IceLoop** — check rights holder and terms.
- **G-Fone** — check in Nice classes 9 and 38. In India a G-Fone brand existed 2010–2015 (Gee Pee Ess India). Possible dormant trademark.
- **Roblox, Sony, MediaTek, Micron** — check for conflicts.
- **DuckDuckGo Premium “forever”** — only with a separate license.
- **SK6812** — terms of use in a commercial product.

## Recommendations

1. **SEP FTO audit** before development starts: 5G, Wi-Fi, Bluetooth, codecs.
2. **Design-around or license** for US 12,308,512 B2 (antenna) and US 20250357560 A1 (5S1P).
3. **Budget 10–15%** of retail price for licensing in the business plan.
4. **Partnership with an ODM** that already has a pool of SEP licenses is the most realistic path.
5. **Repeat SAR/EMC tests** with antenna extended — include in certification plan.
6. **Patent search** on chassis fins and MEMS cooling — separate item.
7. **FTO search** on LED button illumination and SK6812 — separate item.
8. **Trademark check for G-Fone** in Nice classes 9 and 38 (India, Gee Pee Ess).
9. **Separate analysis of Qualcomm risk** when using MediaTek SoC (even without Qualcomm chips).

## Disclaimer

This file describes risks and does not provide legal guarantees. Publishing CAD under CERN-OHL-P v2 does not protect against patent suits. Open design can become evidence of use. An FTO audit is mandatory before commercialization.
