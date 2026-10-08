# HARDWARE

## 주요 사양
- **SoC:** MediaTek Dimensity 9600 Pro, 2 nm, TSMC N2P. 2+3+3. LPDDR6 + UFS 5.0. (2026년 9월 발표)
- **메모리:** 16 GB LPDDR6 + 256 GB UFS 4.0 (UFS 5.0은 공급 상황에 따라).
- **디스플레이:** 7인치 LTPS IPS QHD, 하이엔드.
- **배터리:** 5S1P, 5 × 2500 mAh, 18.5 V, 46.25 Wh. 각형 리튬 폴리머. (5S1P는 드론/RC에서 양산, 스마트폰에서는 이례적)
- **충전:** 80 W, 효율 ≈ 95%.
- **방수/방진:** IP69 / IP69K (케이스 장착 시).
- **본체:** 7075-T6 알루미늄, 접착제 없는 설계(glue-free).

## 왜 2500 mAh가 오타가 아닌가?
5S1P는 46.25 Wh를 제공합니다. Galaxy S24 Ultra보다 2.4배 많고 Galaxy S26보다도 많습니다. 3.7 V 기준 12,500 mAh에 해당합니다. 각형 셀: 간단한 절연, 평평한 열 접촉, 성숙한 BMS.

## 전원 / PMIC (부분 통합)
- **아키텍처:** 하이브리드 — 단일 모놀리식 PMIC가 아니라 전원 도메인 분리.
- **고전압 프론트엔드 (5S1P → 버스):** 18.5 V에서 중간 버스(~5–9 V)로 고효율 step-down; 80 W 충전 및 BMS 밸런싱은 별도 경로.
- **SoC 코어 레일 (CPU / GPU / NPU):** 주 레일에 **더 진보된 multiphase digital buck 컨트롤러** + power stage 부분 통합 (Vcore / GPU / NPU). MediaTek DVFS와 연동된 AVS/DVS; 2 nm 부하용 빠른 과도 응답.
- **기타 레일:** companion PMIC / 이산 레귤레이터 (LPDDR6, RF, ISP/카메라, 디스플레이, always-on).
- **이유:** 5S1P + 플래그십 2 nm SoC는 고전적 단셀 폰 PMIC에 잘 맞지 않음; hot rail multiphase로 효율·열 여유 확보, companion으로 수급·FTO·수리 단순화.
- **상태:** multiphase 컨트롤러와 HV buck은 양산 기술; **18.5 V + Dimensity 9600 Pro용 시스템 통합은 엔지니어링 선택** (ODM 검증, 레이아웃, 열·EMC 필요).

## 카메라
- 메인: 50 MP Sony IMX907, f/1.4, OIS.
- 망원: 50 MP, f/1.4, OIS.
- 초광각: 50 MP IMX858, f/1.4.
- 심도: 12 MP.
- 셀피: 50 MP.
- 생성형 AI 없음.

## 냉각
- 3중 베이퍼 챔버 *(컨셉)*, 핀(12개) *(컨셉)*, 그래핀 코팅.
- MEMS 마이크로펌프 (실제 기술, Goertek 등 공급사 존재)로 온도 구배 균등화. **드라이버 전력: 0.1–0.3 W** (에너지 효율에 중요; 무소음, 가동부 없음).
