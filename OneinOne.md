# G-Fone F1 — Beta 6.3.13 (Engineering Edition)

> Концепт. Часть спецификаций — проектные допущения, а не подтверждённые серийные компоненты.  
> Всё, что помечено *(концепт)*, требует дополнительной проверки с ODM и сертификационными лабораториями.  
> Лицензии: CERN-OHL-P v2 (железо); **ядро GPLv2-only**; **userspace G-Fone — GPLv3**; Lineage/AOSP — **Apache 2.0**. Компоненты распространяются **раздельно**: Apache-код **не** объединяется с ядром GPLv2 (Apache 2.0 и GPLv2 при слиянии в одну программу **несовместимы**; с GPLv3 — совместимы). Не перелицензирование. CC BY 4.0 (документация).  
> Коммерческое использование требует указания авторства.

---

## Что это

G-Fone F1 — концепт защищённого смартфона для **технарей** и энтузиастов приватности, ремонтопригодности и «железа без компромиссов». Не продукт, не оферта, не инструкция к производству. Не масс-маркет. Не enterprise.

---

## Основные характеристики

- **SoC:** MediaTek Dimensity 9600 Pro, 2 нм, TSMC N2P. LPDDR6 + UFS 5.0. (*projected / assumption.*)
- **Память (только внутренняя):** 16 ГБ LPDDR6 + **256 ГБ UFS 5.0** (слота microSD нет).
- **Экран:** 6.77" LTPS IPS QHD (осознанный IPS).
- **АКБ:** 5S1P, ~18.5 В номинал / ~21 В full, **46.25 Вт·ч**. **X-Cross** = механика. **BMS** = active + шунт + NTC на **документируемом IC** (TI BQ-класс / аналог). Cert — **ODM gate**.
- **Зарядка:** до 80 Вт, **USB PD PPS** (~21 В). ~1.6C → **щадящий default 40–50 Вт**. Без wireless.
- **Связь:** нет SIM/microSD. **eSIM only**.
- **Хранилище:** UFS 5.0; **USB Host** (2.5″ → USB-C/PD где возможно; 3.5″ → 12 В; optional signed storage).
- **Цена:** €3200.

### DualBIOS *(инженерный узел)*
SPI NOR + secondary loader; LED/USB notify; external Android only with AVB user-keys or explicit disable+warning.

### eSIM: Privacy-First Control
Userspace policy. **eUICC/модем закрыты**.

### SMD = Stop Meta Data (не surface-mount)
- **Левый:** питание камер/мик/акселерометра.
- **Правый:** RF **L1 path** (обязательно); **L2 rail** только если есть отдельный baseband/eUICC rail.

---

## Камеры
IMX903 и др. **quad-Bayer binning 50→~12.5 МП**; full 50 МП — отдельный режим. **Без generative AI** (нет проприетарных «улучшалок» на закрытых весах).

### Open-source HDR Stacking *(userspace, GPLv3)*
- Съёмка **серии кадров** (разные экспозиции / burst) и **объединение в процессе** на устройстве.
- Полностью в **userspace**, лицензия **GPLv3** (совместимо с userspace G-Fone; не смешивается с ядром GPLv2).
- Алгоритмы открытые (alignment + merge / exposure fusion и аналоги) — **без** проприетарного ISP-AI и без облака.
- Цель: контролируемый динамический диапазон там, где binning и один кадр не тянут, без передачи снимков вендору.

---

## Корпус и охлаждение
7075-T6 glue-free; IP69 / IP69K; VC *(концепт)*; вентиляционная текстура *(концепт)*; XMC-2400.

---

## Софт
LineageOS-based, без GApps. FBE. Ядро **GPLv2-only**; userspace G-Fone **GPLv3** (в т.ч. **HDR Stacking**); Lineage/AOSP **Apache 2.0** — **раздельные** компоненты.

---

## Threat model
**Защищаем:** FBE; SMD; RF L1 (+ L2 if rail); eSIM UX; USB Host + optional signed storage; DualBIOS+AVB; локальный HDR без облака.  
**Не гарантируем:** аудит SoC/baseband; нет DMA на path-only; external boot без подписи/warning.

---

## Статус Beta 6.3.13

- **Изменения Beta 6.3.13:** **Open-source HDR Stacking** (burst/bracket merge в userspace, **GPLv3**, без проприетарного AI); (наследие 6.3.12).

---

> **Дисклеймер.** Это концепт. Не продукт. См. LEGAL.md и PATENTS.md.
