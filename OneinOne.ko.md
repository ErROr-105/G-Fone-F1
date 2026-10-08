# G-Fone F1 — Beta 5 (Engineering Edition)

> 컨셉. 일부 사양은 설계 가정이거나 기존 기술의 비표준 조합입니다.  
> *(컨셉)* 표시 항목은 ODM 및 인증 연구소의 추가 검증이 필요합니다.  
> 라이선스: CERN-OHL-P v2 (하드웨어), GPLv3 (소프트웨어), CC BY 4.0 (문서).  
> 상업적 사용 시 저작자 표시 필수.

---

## 이것은 무엇인가

G-Fone F1은 데이터가 아무에게나 읽히는 데 지친 사람들을 위한 프라이버시 스마트폰 컨셉입니다. 제품·판매 제안·제조 지침이 아니라 토론·비판·개선을 위한 엔지니어링 아이디어입니다.

대상: 프라이버시, 수리 가능성, “타협 없는 하드웨어” 애호가. 대중·기업·러시아 시장 아님.

---

## 주요 사양

- **SoC:** MediaTek Dimensity 9600 Pro, 2 nm, TSMC N2P. 2+3+3. LPDDR6 + UFS 5.0. (2026년 9월 발표)
- **메모리:** 16 GB LPDDR6 + 256 GB UFS 4.0 (UFS 5.0은 공급 상황에 따라).
- **디스플레이:** 7인치 LTPS IPS QHD.
- **배터리:** 5S1P, 5 × 2500 mAh, 18.5 V, **46.25 Wh**. 각형 리튬 폴리머. (드론/RC 양산, 스마트폰에서는 이례적)
- **충전:** 80 W, 효율 ≈ 95%. 0–80% ≈ 29분.
- **연결:** nanoSIM + microSD + eSIM + 외부 위성 터미널 BT. 직접 위성 모뎀 미주장.
- **가격:** 3,200€.

### 왜 2500 mAh가 오타가 아닌가

5S1P = 2500 mAh 셀 5개 직렬. 18.5 V, 46.25 Wh. Galaxy S24 Ultra 대비 **2.4배**. 3.7 V 기준 **12,500 mAh** 상당.

### 전원 / PMIC — 고도 컨트롤러 부분 통합

고전적 단셀 폰 PMIC는 **18.5 V(5S1P)** 와 2 nm hot rail에 잘 맞지 않음. **하이브리드**: HV 프론트엔드; SoC 코어 레일 **multiphase digital buck** 부분 통합; 기타 companion. 시스템 통합은 엔지니어링 선택 (ODM, 레이아웃, 열·EMC).

---

## 카메라

메인 50 MP Sony IMX907 f/1.4 OIS; 망원 50 MP; 초광각 50 MP IMX858; 심도 12 MP; 셀피 50 MP. 생성형 AI 없음. Zeiss는 라이선스 시. 카메라 주변 ≥ 7 mm.

---

## 본체 및 냉각

- **7075-T6 알루미늄**, glue-free.
- 방수: IP69 / IP69K(케이스).
- 3중 베이퍼 챔버 *(컨셉)*.
- 핀 *(컨셉)*: 12개.
- Anti-Burn: MEMS 마이크로펌프. **드라이버 전력: 0.1–0.3 W**.

---

## 독특한 하드웨어

**SMD 버튼(Stop Meta Data)**: 카메라·마이크·가속도계 물리 차단. 다중 모드 RGB. SK6812 IP65 + SMD 4020 RGB IP65.

**이스터 에그: Mindustry 부트 화살표** — **기기 부팅** 중 **Mindustry**를 열면 조명(SMD 4020 + SK6812)이 **Mindustry 로딩 화살표 애니메이션을 재현**합니다(LED 스트립을 따라 셰브론/화살표 체이싱, 게임 로딩 화면과 동기화). 오프라인 로컬 LED 패턴.

---

## 소프트웨어

LineageOS, GApps 없음. F-Droid, DuckDuckGo, Proton Mail. UnifiedPush 선택. E2EE; eBPF; **FBE**. 러시아: 공식 미공급; RTRCA/SORM 비호환.

---

## 특허 리스크 (요약)

SEP 5G; Motorola US 12,308,512 B2; US 20250357560 A1; MEMS; LED; SK6812; 핀; PMIC/multiphase FTO; G-Fone 상표; Qualcomm. 상세 LEGAL.md / PATENTS.md.

---

## Beta 5 상태

구현 가능 / 양산: 2 nm SoC, LPDDR6, UFS 5.0, 5S1P, 80 W, multiphase/HV 부품, MEMS(0.1–0.3 W), 7075-T6, LineageOS, eBPF, UnifiedPush, FBE, SK6812, SMD 버튼.

컨셉 / 시스템 통합: 3중 VC, 텔레스코픽 안테나, 핀, 부분 고도 PMIC, 다중 모드 LED, **Mindustry 부트 화살표 LED 이스터 에그**.

라이선스: CERN-OHL-P v2 / GPLv3 / CC BY 4.0.

---

## 기여 방법

허용: CAD, 열 시뮬레이션, 소프트웨어, BMS, 전원/PMIC 레이아웃, 문서, 테스트, 번역. 금지: 특허 우회, 위법 조장, 블랙리스트, 정치 발언.

---

> **면책.** 컨셉이지 제품이 아닙니다. 사양은 가정 또는 기존 기술 조합입니다. 미인증. 특허는 LEGAL.md / PATENTS.md. FTO 미실시. 저자 책임 없음. 사용자는 관할 법률 준수.
