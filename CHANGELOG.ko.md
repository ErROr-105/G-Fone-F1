# CHANGELOG

G-Fone F1 컨셉의 변경 이력. 초기 버전(Beta 3 이전)은 게시되지 않음: 일부 결정은 수정되었고, 일부는 실현 불가능하여 삭제됨.

## Beta 5

- **이스터 에그 — Mindustry 로딩 화살표:** Mindustry를 열 때 게임 로딩 화면 동안 SMD 4020 버튼 + SK6812 악센트 라인이 수평선 중앙의 로딩 화살표를 **화면과 같은 빛/색**으로 재현 (기기 부팅과 무관).
- **전원 / PMIC:** SoC hot rail(CPU/GPU/NPU)용 고도 multiphase digital buck 컨트롤러 부분 통합 및 5S1P 18.5 V HV 프론트엔드 문서화; 기타 도메인은 companion.
- **컨셉 마커:** 개정 (SoC/LPDDR6/UFS 5.0/MEMS는 양산; 3중 VC, 텔레스코픽 안테나, 핀은 컨셉/시스템 통합).
- **MEMS:** 드라이버 전력 0.1–0.3 W 명시.
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
