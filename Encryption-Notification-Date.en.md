# Encryption Notification Date

The project mentions cryptographic technologies:

- AES-256-GCM
- ChaCha20-Poly1305
- X25519

All listed algorithms are **standard** (published in RFCs / adopted by international standards).

## Status under EAR (after 2021 changes)

According to 15 CFR § 742.15(b), notification to BIS and NSA is required **only** for publicly available encryption source code that implements **non-standard cryptography**.

Since only standard algorithms are used, formal notification under License Exception TSU / § 742.15(b) **is not required**.

---

### If non-standard cryptography appears in the future

Notification must be sent **before** publishing the source code:

- **To:** crypt@bis.doc.gov and enc@nsa.gov
- **Subject:** Section 742.15 NOTIFICATION - Encryption / TSU NOTIFICATION
- **Content:** Repository URL + brief description

- **Date sent:** [date]
- **Link / copy of email:** [insert]
- **License Exception / section:** 15 CFR § 742.15(b) (formerly TSU 740.13(e))

*To be filled only if non-standard cryptography is present and before public release of the code.*
