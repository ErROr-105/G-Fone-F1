# CHANGELOG

История изменений концепта G-Fone F1. Ранние версии (до Beta 3) не публикуются.

## Beta 6.3.12

- **RF kill L1/L2:** L1 = path (обязательно); L2 = rail **если** SoC/PMIC даёт отдельный baseband/eUICC rail; иначе только L1.
- **USB Host:** 2.5″ — предпочтительно **USB-C/PD**; 3.5″ — 12 В; optional **signed storage** policy (с AVB external boot).
- **BMS:** документируемый IC (TI BQ-класс / аналог); **X-Cross** = только механика ячеек.

## Beta 6.3.11

- DualBIOS secondary loader + AVB; RF DMA caveat; binning 50→12.5.

## Beta 6.3.10

- PPS ~21 В; 1.6C + щадящий default; eUICC honesty; Apache↔GPLv2.

## Ранее

См. репозиторий.
