# Licenses

This project uses multiple licenses depending on the component:

## Hardware (CAD, schematics, mechanical design)
**CERN Open Hardware Licence Version 2 - Permissive (CERN-OHL-P v2)**

Full text: https://ohwr.org/cern_ohl_p_v2.txt

## Software

### Linux kernel (device changes / patches)
**GPLv2-only**

The upstream Linux kernel is licensed **GPLv2-only**. **GPLv3 is incompatible** with GPLv2-only kernel code. All kernel modifications for this device are therefore **GPLv2-only**.

### Project userspace code (scripts, apps, firmware where project-owned)
**GNU General Public License v3.0 (GPLv3)**

Full text: https://www.gnu.org/licenses/gpl-3.0.en.html

### LineageOS / AOSP base
Primarily **Apache License 2.0**.

Apache 2.0 is **compatible with GPLv3** (they may coexist in one product). **Mixed licenses do not cancel the original:** code that arrived under Apache 2.0 remains under Apache 2.0; applying or linking GPLv3 components does not relicense that Apache-licensed code.

## Documentation (all .md files, texts, guides)
**Creative Commons Attribution 4.0 International (CC BY 4.0)**

Full text: https://creativecommons.org/licenses/by/4.0/legalcode

**Attribution required:** "Engineering Idea by ErROr_105Unknown"

---

See also:
- [LICENSE-GPLv3.md](LICENSE-GPLv3.md)
- [LICENSE-CC-BY-4.0.md](LICENSE-CC-BY-4.0.md)
