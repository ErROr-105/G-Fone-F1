# HARDWARE

## Основные характеристики
- **SoC:** MediaTek Dimensity 9600 Pro, 2 нм. LPDDR6 + UFS 5.0.
- **Память (только внутренняя):** 16 ГБ LPDDR6 + **256 ГБ UFS 5.0** (слота microSD нет).
- **Экран:** 6.77" LTPS IPS QHD.
- **АКБ:** 5S1P, 46.25 Вт·ч. **X-Cross**. Active BMS. Сертификация — **ODM gate**.
- **Зарядка:** 80 Вт **проводная**. Без wireless. Тракт **18.5 В**. Времена — расчёт/оценка.
- **Защита:** IP69 / IP69K. **Корпус:** 7075-T6 glue-free; стальное кольцо — cooler.

## BMS
V каждой ячейки; NTC на каждой; шунт пакета. **Активная** балансировка — baseline.

## Питание / PMIC
HV 18.5 В; дроссель фильтра **в телефоне**; multiphase на hot rails SoC.

## Связь и накопители
- Слотов SIM/microSD **нет**. **eSIM only** (Privacy-First в userspace; не доказывает отсутствие baseband-side действий).
- Внутреннее: **256 ГБ UFS 5.0**.
- **USB Host** + **USB → SATA с питанием** (2.5″; 3.5″ — отдельные **12 В**).
- **Why No microSD?** надёжность/IP, не ремонт mainboard.

## DualBIOS (запасной boot-чип) *(инженерный узел)*
- Носитель **вне UFS** со **своей** boot-прошивкой.
- Цепочка: **Boot ROM в SoC** → обычно UFS 5.0; при отказе UFS → DualBIOS **уведомляет** и **предлагает** boot Android с внешнего USB/SATA-диска, если образ записан.
- Не «unbrick из воздуха»; secure-boot policy — ODM.

## SMD — сдвоенная кнопка
- **Левый:** питание камер/мик/акселерометра.
- **Правый:** **RF path kill** (антенный тракт). Модем в SoC остаётся; kill = нет TX/RX.

## Threat model (кратко)
**Защищаем:** FBE, SMD, RF kill, eSIM UX, DualBIOS fallback.  
**Не обещаем:** аудит baseband/SoC; external boot без образа/DualBIOS; «АКБ уже сертифицирована».

## Камеры / охлаждение / комплект
IMX903 и др. Магнитный cooler; VC *(концепт)*; XMC-2400. Напальчники; USB→SATA; чехол-рамка.
