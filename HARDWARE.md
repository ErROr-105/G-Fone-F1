# HARDWARE

## Основные характеристики
- **SoC:** MediaTek Dimensity 9600 Pro, 2 нм. LPDDR6 + UFS 5.0.
- **Память (только внутренняя):** 16 ГБ LPDDR6 + **256 ГБ UFS 5.0** (слота microSD нет).
- **Экран:** 6.77" LTPS IPS QHD.
- **АКБ:** 5S1P, 46.25 Вт·ч. Номинал **~18.5 В**, полный заряд **~21 В** (5×4.2). **X-Cross**. Active BMS. Cert — **ODM gate**.
- **Зарядка:** до 80 Вт **проводная**. Тракт до **~21 В** → **USB PD PPS** (не только 20 В fixed). ~80 Вт ≈ **1.6C** — агрессивно; **щадящий режим (40–50 Вт) по умолчанию**; ресурс циклов TBD. Без wireless. Времена — расчёт/оценка.
- **Защита:** IP69 / IP69K. **Корпус:** 7075-T6 glue-free; стальное кольцо — cooler.

## BMS
V каждой ячейки; NTC на каждой; шунт пакета. **Активная** балансировка — baseline.

## Питание / PMIC
HV до ~21 В full; дроссель фильтра **в телефоне**; multiphase на hot rails SoC.

## Связь и накопители
- Слотов SIM/microSD **нет**. **eSIM only** (Privacy-First userspace; **eUICC/модем закрыты**; OS-политика ≠ гарантия на стороне модема).
- Внутреннее: **256 ГБ UFS 5.0**.
- **USB Host** + **USB → SATA с питанием** (2.5″; 3.5″ — отдельные **12 В**).
- **Why No microSD?** надёжность/IP, не ремонт mainboard.

## DualBIOS (запасной boot-чип) *(инженерный узел)*
Boot ROM в SoC → UFS 5.0; при отказе UFS → DualBIOS notify + optional external Android (если образ записан).

## SMD = Stop Meta Data (не surface-mount) — сдвоенная кнопка
- **Левый:** питание камер/мик/акселерометра.
- **Правый:** **RF path kill** (антенный тракт).

## Threat model (кратко)
**Защищаем:** FBE, SMD, RF kill, eSIM UX (userspace), DualBIOS.  
**Не обещаем:** аудит baseband/eUICC/SoC; external boot без образа; «АКБ уже сертифицирована»; crypto-immutable log без TEE/SE.

## Камеры / охлаждение / комплект
IMX903 и др. Магнитный cooler; VC *(концепт)*; XMC-2400. Напальчники = **тепло** 7075; USB→SATA; чехол-рамка.
