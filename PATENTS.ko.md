# PATENTS

> 이 파일은 법률 자문이 아닙니다. 리스크와 권장 사항을 설명합니다.  
> 상용화를 위해서는 완전한 FTO(Freedom to Operate) 감사가 필요합니다.

## SEP — Standards Essential Patents

**규모.** ETSI 데이터베이스에 10만 개 이상의 5G 특허 패밀리가 신고되어 있습니다. 실제로 구현된 것은 ~44.65%(스마트폰의 경우 관련성 91.5%에서 ~39.8%)입니다.

**플레이어.** 상위 20개 권리자가 신고된 패밀리의 ~88%를 통제합니다. 선두: Huawei, Qualcomm, LG, Samsung, Ericsson — ~43%.

**요율.** 5G 합산 로열티는 기기당 $15–20에 달합니다. Wi-Fi, Bluetooth 및 코덱 포함 시 소매가의 10–15%. 법원 판결(ZTE 대 Samsung)은 5G에 대해 7.8–11.6%를 확인합니다.

**FRAND.** 법원은 성실한 협상을 요구합니다. 회피는 판매 금지로 이어질 수 있습니다.

**G-Fone F1의 경우:** 3,200€ 가격에서 로열티는 마진으로 흡수되지만 SEP 라이선스 풀과의 합의가 필요합니다.

**컨셉의 SEP 소스.** MediaTek(Dimensity SoC를 통해), Nokia, Ericsson, Samsung의 SEP 라이선스만 사용하는 것으로 가정합니다. 컨셉에서 Qualcomm 라이선스는 **사용되지 않습니다**.

**Qualcomm 리스크.** Qualcomm은 다른 제조사(MediaTek 등)의 SoC를 사용하는 경우에도 특허 포트폴리오를 적극적으로 방어합니다. 5G, RF 프론트엔드, 모뎀 및 관련 기술과 관련된 SEP 및 non-SEP 특허에 따른 청구 위험이 있습니다. 이 리스크는 FTO 감사에서 별도로 다루어야 합니다. Qualcomm과 기존 계약 또는 크로스 라이선스가 있는 ODM 파트너를 통해 리스크를 줄일 수 있습니다.

## 하드웨어 특허

- **Motorola US 12,308,512 B2** — 확장 가능한 폼팩터용 재구성 가능 안테나(텔레스코픽 지지). 텔레스코픽 안테나에 대한 직접 리스크.
- **Huawei EP 4 020 705 B1** — 롤러블 디스플레이용 안테나 어셈블리. 낮은 하지만 실제 리스크.
- **US 20250357560 A1** (우선권 2017) — 전동 공구용 5S1P 배터리. 적용 분야는 다르지만 청구항 범위가 넓어 리스크를 만듦.
- **MEMS 냉각** — Murata, STMicroelectronics, Frore Systems.
- **충전 및 온도 표시가 있는 LED 버튼 조명** — Samsung, LG, Motorola (“multi-mode button illumination”).
- **SK6812** — Worldsemi, APA Electronic, Shenzhen LED (어드레스 가능 RGB 스트립).
- **본체 핀** — 모바일 장치 열 설계에 대한 FTO.

## 상표

- **Zeiss** — 별도 라이선스 시에만.
- **IceLoop** — 권리자 및 조건 확인.
- **G-Fone** — 니스 분류 9 및 38에서 확인. 인도에서 2010–2015년 G-Fone 브랜드가 존재(Gee Pee Ess India). 휴면 상표 가능.
- **Roblox, Sony, MediaTek, Micron** — 충돌 확인.
- **DuckDuckGo Premium “영원히”** — 별도 라이선스 시에만.
- **SK6812** — 상업 제품에서의 사용 조건.

## 권장 사항

1. **개발 시작 전 SEP FTO 감사:** 5G, Wi-Fi, Bluetooth, 코덱.
2. **US 12,308,512 B2 (안테나) 및 US 20250357560 A1 (5S1P)에 대한 설계 회피 또는 라이선스**.
3. **비즈니스 플랜에 소매가의 10–15%를 라이선싱 비용으로 책정**.
4. **이미 SEP 라이선스 풀을 보유한 ODM과의 파트너십**이 가장 현실적인 경로.
5. **안테나 확장 시 SAR/EMC 재테스트** — 인증 계획에 포함.
6. **본체 핀 및 MEMS 냉각에 대한 특허 검색** — 별도 항목.
7. **LED 버튼 조명 및 SK6812에 대한 FTO 검색** — 별도 항목.
8. **니스 분류 9 및 38에서 G-Fone 상표 확인** (인도, Gee Pee Ess).
9. **MediaTek SoC 사용 시 Qualcomm 리스크 별도 분석** (Qualcomm 칩이 없어도).

## 면책 조항

이 파일은 리스크를 설명하며 법적 보장을 제공하지 않습니다. CERN-OHL-P v2 하에 CAD를 게시해도 특허 소송으로부터 보호되지 않습니다. 공개 디자인은 사용 증거가 될 수 있습니다. 상용화 전 FTO 감사는 필수입니다.
