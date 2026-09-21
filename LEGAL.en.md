# G-Fone F1 — Beta 4 (Legal Edition)

> This document is not legal advice. It describes risks and the positioning of the concept.  
> Commercialization requires: FTO audit, certification, export classification, and an ODM partner with SEP licenses.

---

## 1. Legal Status of the Document

This document describes a **device concept**, not a production product. It is not:

- an offer to sell or supply;
- a public offer;
- a manufacturing guide;
- a declaration of conformity with mandatory requirements;
- legal advice.

All characteristics, components and architectural decisions are described as **design assumptions**. No component is confirmed by a vendor. No certification has been obtained. No patent license agreement has been concluded.

The author does not encourage violation of any laws. All technical solutions are described as architectural assumptions of the concept. Users are responsible for compliance with the laws of their jurisdiction.

---

## 2. Device vs Service Distinction

This is the key distinction for assessing regulatory risks.

**G-Fone F1 is a device.** It is not a telecom operator, messenger, VoIP service or provider. Lawful intercept, SORM and communications licensing requirements **do not apply to the device**. They apply to operators and service providers.

**Push gateway is optional infrastructure.** If deployed, it may fall under lawful intercept requirements in certain jurisdictions (Russia, China, Australia, UK, etc.). In that case responsibility for compliance with local laws lies with the developers of apps that use the gateway and with the gateway operator, not with the G-Fone F1 device.

**E2EE is implemented in supported applications**, not in the device. G-Fone F1 provides architectural capabilities (TEE, FDE, hardware sensor kill-switch) but is not a communications service provider.

---

## 3. Export Control

**Encryption.** The project contains cryptographic technologies (AES-256-GCM, ChaCha20-Poly1305, X25519). This falls under US export control (EAR) and EU control (Regulation 2021/821, Category 5, Part 2).

**Mass-market exception.** For smartphones the exception ECCN 5A992.c (US) and Crypto Note (EU) usually applies. However:

- non-standard cryptography may not qualify for the exception;
- publication of encryption source code on GitHub is considered an export from the US perspective;
- License Exception TSU (EAR 740.13(e)) applies, but notification to BIS is required **only for non-standard cryptography**;
- EAR 734.7 exempts “publicly available” information, with specific exceptions for encryption.

**Satellite communications.** The concept has no direct satellite modem — only Bluetooth connection to external terminals. This does not require an FCC Earth Station License for G-Fone F1. The license is required for the terminal, not the smartphone. If an NTN modem appears in the future, separate authorization will be needed.

**Actions before publishing code with encryption:**
1. Notify BIS (US) of open-source encryption publication (only if non-standard cryptography is used).
2. Check applicability of exceptions in the EU.
3. State in the repository that the project contains cryptography and is subject to export control.

---

## 4. Patent Risks

**SEP (Standards Essential Patents).** More than 100,000 5G patent families are declared in ETSI. ~44.65% are actually implemented (for smartphones ~39.8% at 91.5% relevance). Aggregate 5G royalties reach $15–20 per device. With Wi-Fi, Bluetooth and codecs — 10–15% of retail price. Court decisions (ZTE v. Samsung) confirm 7.8–11.6% for 5G.

**SEP sources in the concept.** G-Fone F1 assumes use of SEP licenses only from MediaTek (via Dimensity SoC), Nokia, Ericsson and Samsung. Qualcomm licenses are **not used** in the concept.

**Qualcomm risk.** Qualcomm has historically actively defended its patent portfolio, including in cases where a device uses a SoC from another manufacturer (MediaTek, Unisoc, etc.). Even without direct use of Qualcomm chips there is a risk of patent claims under SEP and non-SEP patents related to 5G, RF, modem and related technologies. This is a separate risk that must be addressed in the FTO audit. Partnership with an ODM that has existing cross-licenses or agreements with Qualcomm significantly reduces this risk.

**Hardware patents:**
- Motorola **US 12,308,512 B2** — reconfigurable antenna for expandable form factor (telescopic support).
- Huawei **EP 4 020 705 B1** — antenna assembly for rollable displays.
- **US 20250357560 A1** — 5S1P battery for power tools.
- MEMS cooling — Murata, STMicroelectronics, Frore Systems.
- LED button illumination with charge and thermal indication — Samsung, LG, Motorola (“multi-mode button illumination”).
- SK6812 — Worldsemi, APA Electronic, Shenzhen LED (addressable RGB strips).
- Chassis fins — thermal design of mobile devices.

**FRAND obligations.** Courts require good-faith negotiations. Avoidance may result in an injunction against sales.

**FTO audit is mandatory before commercialization.** Publishing CAD under CERN-OHL-P does not protect against patent suits. Open design can become evidence of use.

---

## 5. Certification and Regulation

**USA:**
- FCC ID Certification (EMC, RF, SAR) for Wi-Fi/Bluetooth/5G.
- Separate authorization for satellite earth stations — only if an NTN modem appears.

**EU:**
- RED (Radio Equipment Directive).
- **EN 18031** — cybersecurity requirements from 1 August 2025.
- USB-C, Battery Regulation, Right to Repair.
- EU 2023/1670 — energy label.
- GDPR — if the push gateway processes personal data.

**Battery:**
- UN38.3, IEC 62133, lithium battery transport rules.

**Russia:**
- The device is not officially supplied to Russia.
- Mandatory pre-installation and certification requirements (RTRCA, SORM) do not apply because the product does not enter the Russian market through official channels.
- This is a technical decision (architectural incompatibility), not a political statement.
- Users in Russia act at their own risk.

**Sale on the US and EU markets without certification is illegal.**

---

## 6. Cybersecurity and Privacy

**CFAA (USA).** The law prohibits unauthorized access to “protected computers”. Blocking trackers on one’s own device is not unauthorized access. Risk arises if the filter interferes with carrier traffic or modifies third-party apps without consent. Positioning the eBPF filter as a **user privacy tool** removes most of the risk.

**GDPR (EU).** If the push gateway processes personal data (eSIM, push tokens, telemetry), it becomes a controller or processor. Required:
- legal basis for processing;
- privacy policy;
- DPA (Data Processing Agreement) with app developers;
- data minimization.

There are precedents of fines related to eSIM (e.g. €30 million for Vodafone).

**Anti-forensics.** Clearing temporary keys based on voltage/temperature is an industry standard (Apple Secure Enclave, Google Titan M, Samsung Knox). This is privacy protection, not obstruction of lawful access. Risk arises only if the device is positioned as a “tool to counteract investigations” — the current text does not do so.

**Anti-IMSI and radio silence.** Legal for the user in most countries. Legal for the manufacturer as well, provided it is not positioned as “circumvention of SORM”. The wording “anomaly check + notification” is protection, not counteraction.

---

## 7. Trademarks and Licenses

**Hardware:** CERN-OHL-P v2 — permissive, commercial use allowed, attribution required, derivatives need not be open.

**Software:** GPLv3 — strong copyleft, source must be available.

**Documentation:** CC BY 4.0 — attribution required.

**Trademarks:**
- Zeiss — only with a license.
- IceLoop — check rights holder.
- G-Fone — check in Nice classes 9 and 38 (India, Gee Pee Ess).
- Roblox, Sony, MediaTek, Micron — check for conflicts.
- DuckDuckGo Premium “forever” — only with a license.
- SK6812 — terms of use in a commercial product.

---

## 8. Recommendations Before Commercialization

1. SEP FTO audit: 5G, Wi-Fi, Bluetooth, codecs.
2. Design-around or license for US 12,308,512 B2 and US 20250357560 A1.
3. Budget 10–15% of retail price for licensing.
4. Partnership with an ODM that has a pool of SEP licenses.
5. Repeat SAR/EMC tests with antenna extended.
6. Patent search on chassis fins and MEMS cooling.
7. FTO on LED button illumination and SK6812.
8. Trademark check for G-Fone in Nice classes 9 and 38.
9. BIS notification of open-source encryption publication (if non-standard cryptography is used).
10. Certification: FCC, RED, EN 18031, UN38.3, IEC 62133.
11. GDPR documentation for the push gateway (if deployed).
12. Position the eBPF filter as a user privacy tool.

---

## 9. Disclaimer

This document describes a concept. It is not legal advice, a public offer, a declaration of conformity or a manufacturing guide. The author does not encourage violation of any laws. All technical solutions are described as architectural assumptions. Patent, regulatory and export risks are described in sections 3–8. No FTO audit has been performed. No certification has been obtained. Users are responsible for compliance with the laws of their jurisdiction. The author is not liable for any consequences of using these materials.

---

## 10. Licenses

- **Hardware:** CERN-OHL-P v2.
- **Software:** GPLv3.
- **Documentation:** CC BY 4.0.

Full license texts are in the files LICENSE, LICENSE-GPLv3, LICENSE-CC-BY-4.0.
