# Licenses

This project uses multiple licenses depending on the component:

## Hardware (CAD, schematics, mechanical design)
**CERN Open Hardware Licence Version 2 - Permissive (CERN-OHL-P v2)**

Full text: https://ohwr.org/cern_ohl_p_v2.txt

## Software

### Linux kernel (device changes / patches)
**GPLv2-only**

The upstream Linux kernel is licensed **GPLv2-only**. **GPLv3 is incompatible** with GPLv2-only kernel code. All kernel modifications for G-Fone F1 are therefore **strictly GPLv2-only**.

### G-Fone F1 project modifications and own code (userspace)
**GNU General Public License v3.0 (GPLv3)**

Device/stack code and project-owned userspace modifications for G-Fone F1 are under **GPLv3** (not the kernel).

Full text: https://www.gnu.org/licenses/gpl-3.0.en.html

### LineageOS / AOSP base
Primarily **Apache License 2.0**.

**GPLv3 and Apache 2.0 are compatible** (they may coexist in one product) but **not relicenseable**: Apache-licensed code **cannot** be converted to GPLv3. **Mixed licenses do not cancel the original.** When distributing or modifying Apache 2.0 code you **must fulfill Apache 2.0 requirements** (NOTICE, attribution, preserve license and change notices). See NOTICE.md.

## Documentation (all .md files, texts, guides)
**Creative Commons Attribution 4.0 International (CC BY 4.0)**

Full text: https://creativecommons.org/licenses/by/4.0/legalcode

**Attribution required:** "Engineering Idea by ErROr_105Unknown"

---

See also:
- [LICENSE-GPLv3.md](LICENSE-GPLv3.md)
- [LICENSE-CC-BY-4.0.md](LICENSE-CC-BY-4.0.md)
