# HARDWARE

## Основные характеристики
- **SoC:** MediaTek Dimensity 9600 Pro, 2 нм. LPDDR6 + UFS 5.0.
- **Память:** 16 ГБ LPDDR6 + **256 ГБ UFS 5.0** (без microSD).
- **Экран:** 6.77" LTPS IPS QHD.
- **АКБ:** 5S1P, 46.25 Вт·ч. Номинал **~18.5 В**, full **~21 В**. **X-Cross** = механика. **BMS** = active + шунт + NTC на **документируемом IC** (TI BQ-класс / аналог, ODM). Cert — **ODM gate**.
- **Зарядка:** до 80 Вт, **USB PD PPS** (~21 В). ~80 Вт ≈ **1.6C** → **щадящий default 40–50 Вт**. Без wireless.
- **Защита / корпус:** IP69 / IP69K; 7075-T6 glue-free; стальное кольцо cooler.

## BMS / PMIC
Per-cell V; NTC; шунт; active balancing на **проверяемом** контроллере. HV ~21 В full; дроссель фильтра в телефоне; multiphase. **X-Cross ≠ BMS.**

## Связь и накопители
- **eSIM only** (userspace Privacy-First; **eUICC/модем закрыты**).
- **USB Host** + USB→SATA: **2.5″** предпочтительно с **USB-C/PD**; **3.5″** — **12 В** отдельно. Optional signed-storage policy.
- microSD нет = надёжность/IP.

## DualBIOS *(инженерный узел)*
SPI NOR + secondary loader; LED/USB notify; external Android only with AVB user-keys or explicit disable+warning.

## SMD = Stop Meta Data (не surface-mount) — сдвоенная кнопка
- **Левый:** питание камер/мик/акселерометра.
- **Правый:**
  - **L1 (обязательно):** RF **path** kill (антенны) — нет TX/RX; DMA модема **возможен**.
  - **L2 (ODM, если есть отдельный rail baseband/eUICC):** **rail** kill.
  - Нет отдельного rail → только L1 в продукте.

## Threat model (кратко)
**Защищаем:** FBE, SMD, RF L1 (+ L2 if rail), DualBIOS+AVB, optional signed storage.  
**Не обещаем:** нет DMA на path-only; L2 без real rail; external boot без подписи/warning.

## Камеры
| Модуль | Спека |
|--------|--------|
| Основная | **Sony LYTIA 720** (не IMX903/907 — Apple-oriented) |
| Теле | ~70 мм, 50 МП, **f/1.8**, OIS, IMX858-класс (не f/1.4) |
| Ультраширик | **IMX858**, ~14 мм, **f/2.2**, 50 МП |
| DoF / селфи | 12 МП / 50 МП |

Публичные ориентиры: Xiaomi 15 Ultra (IMX858 UW/tele), iPhone 17 Pro (IMX903 — только как риск Apple supply). HDR Stacking — userspace GPLv3.

## Охлаждение / комплект
Cooler; VC *(концепт)*; XMC-2400. Напальчники = тепло 7075; USB→SATA; чехол.
