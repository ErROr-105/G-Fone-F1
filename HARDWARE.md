# HARDWARE

## Основные характеристики
- **SoC:** MediaTek Dimensity 9600 Pro, 2 нм. LPDDR6 + UFS 5.0.
- **Память:** 16 ГБ LPDDR6 + **256 ГБ UFS 5.0** (без microSD).
- **Экран:** 6.77" LTPS IPS QHD.
- **АКБ:** 5S1P, 46.25 Вт·ч. Номинал **~18.5 В**, full **~21 В**. Active BMS. Cert — **ODM gate**.
- **Зарядка:** до 80 Вт, **USB PD PPS** (~21 В). ~80 Вт ≈ **1.6C** → **щадящий default 40–50 Вт**. Без wireless.
- **Защита / корпус:** IP69 / IP69K; 7075-T6 glue-free; стальное кольцо cooler.

## BMS / PMIC
Per-cell V; NTC; шунт; active balancing. HV ~21 В full; дроссель фильтра в телефоне; multiphase.

## Связь и накопители
- **eSIM only** (userspace Privacy-First; **eUICC/модем закрыты**).
- **USB Host** + USB→SATA (2.5″; 3.5″ — **12 В** отдельно).
- microSD нет = надёжность/IP.

## DualBIOS (запасной boot-чип) *(инженерный узел)*
- Boot ROM SoC **обычно не** грузит USB сам → DualBIOS = **SPI NOR (типично) + secondary loader**, не «диск вместо UFS».
- При отказе UFS: notify (**LED / USB status**, не только экран) → optional Android с USB **только** если образ **подписан user key (AVB)** или AVB **явно** отключён с предупреждением.
- Иначе DualBIOS не privacy-safe recovery. ODM: boot policy MediaTek, fuses, UX.

## SMD = Stop Meta Data (не surface-mount) — сдвоенная кнопка
- **Левый:** питание камер/мик/акселерометра.
- **Правый:** **RF path kill** (антенный тракт). Модем в SoC остаётся; при kill возможны питание домена и **DMA к RAM**.

## Threat model (кратко)
**Защищаем:** FBE, SMD, RF kill (эфир), DualBIOS с AVB-политикой.  
**Не обещаем:** нет DMA модема при RF kill; external boot без подписи/warning; аудит eUICC/SoC.

## Камеры / охлаждение / комплект
50 МП с **binning 50→~12.5**. Cooler; VC *(концепт)*; XMC-2400. Напальчники = тепло 7075.
