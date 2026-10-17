# CHANGELOG

G-Fone F1 컨셉의 변경 이력. 초기 버전(Beta 3 이전)은 게시되지 않음: 일부 결정은 수정되었고, 일부는 실현 불가능하여 삭제됨.

## Beta 6

- **X-Cross:** 5S1P 각형 셀 고정용 내부 금속 십자 부품 설명.
- **팩 레벨 PTC 필름**(저온 보호); 5S1P에서 cell-level은 무의미(직렬=단일 전기·열 팩).
- **일반 직물 손가락 커버** 동봉: 7075 알루미늄 열전달 극단; 베어 메탈 취급 안전.
- **케이스:** 그립 프레임; 중가 실리콘 카메라 캡(스크래치 방지).

## Beta 5.1

- **디스플레이:** 7인치 → **6.77인치** LTPS IPS QHD.
- **메인 카메라:** Sony **IMX903** (기존 IMX907).
- **MEMS / Anti-Burn:** 구체 모델 **xMEMS Lab XMC-2400** — 3 V, 30 mW(펌프) / **드라이버 포함 70 mW**; 일반 전력 구간 폐기.
- **라이선스:** Linux 커널 변경은 **GPLv2-only**(GPLv3와 비호환); 프로젝트 userspace는 GPLv3; LineageOS/AOSP 기반은 주로 **Apache 2.0** — GPLv3와 호환되나 혼합 라이선스가 원본 Apache를 취소하지 않음.
- **NOTICE.md:** LineageOS `android_frameworks_base` NOTICE 전문 수록 (AOSP 귀속 / Apache 2.0 §4(d)).
- **문서:** SOFTWARE.md / LICENSE.md / OneinOne.* 라이선스 설명 갱신.

## Beta 5

- **이스터 에그 — Mindustry 로딩 화살표:** Mindustry를 열 때 게임 로딩 화면 동안 SMD 4020 버튼 + SK6812 악센트 라인이 수평선 중앙의 로딩 화살표를 **화면과 같은 빛/색**으로 재현 (기기 부팅과 무관).
- **전원 / PMIC:** SoC hot rail(CPU/GPU/NPU)용 고도 multiphase digital buck 컨트롤러 부분 통합 및 5S1P 18.5 V HV 프론트엔드 문서화; 기타 도메인은 companion.
- **컨셉 마커:** 개정 (SoC/LPDDR6/UFS 5.0/MEMS는 양산; 3중 VC, 텔레스코픽 안테나, 핀은 컨셉/시스템 통합).
- **MEMS:** 드라이버 전력 0.1–0.3 W 구간 (Beta 5.1에서 XMC-2400 사양으로 대체).
- **암호화:** FBE(file-based encryption) 표기.
- **문서:** 러시아어 OneinOne.md 복구; HARDWARE/OneinOne 4개 언어 동기화.

## Beta 4

- **LED 조명:**
  - 악센트 라인: 어드레스 가능한 RGB 스트립 SK6812 IP65, 60 LEDs/m, 측면 발광, SMD 4020.
  - SMD 버튼: 어드레스 가능한 RGB SMD 4020, IP65.
  - Thermal Hue를 후면 패널 라인으로 연결, 버튼과 동기화.
- **소프트웨어:**
  - Work Profile (Geo-Stable) 제거 (과도한 격리로 판단).
  - 러시아 관련 문구를 “거부”에서 “아키텍처 비호환성”으로 재작성.
  - 앱 블랙리스트를 RTRCA 및 SORM과의 비호환성 설명으로 대체.
- **라이선스:**
  - 하드웨어: CERN-OHL-P v2.
  - 소프트웨어: GPLv3.
  - 문서: CC BY 4.0.
- **문서:**
  - LEGAL.md 추가 (법적 분석).
  - DISCLAIMER.md 추가.
  - Encryption-Notification-Date.md 추가 (BIS 통지).
  - OneinOne.md — 전체 Engineering Edition 단일 파일.

## Beta 3

- SMD (Stop Meta Data) 버튼 추가: 카메라, 마이크, 가속도계 물리 전원 차단.
- 버튼 다중 모드 LED 조명 추가:
  - Privacy Mode (빨간색).
  - Charge Y-Fill.
  - Thermal Hue.
- 초기 특허 분석 수행:
  - SEP 5G (소매가의 10–15%).
  - Motorola US 12,308,512 B2 (텔레스코픽 안테나).
  - US 20250357560 A1 (5S1P).
- Anti-Burn 열 안정화 블록 설명 (MEMS 마이크로펌프).

초기 버전(Beta 1, Beta 2)은 게시되지 않음.
