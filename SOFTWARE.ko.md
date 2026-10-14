# SOFTWARE

- **OS:** LineageOS 기반, GApps 없음.
- **사전 설치:** F-Droid, DuckDuckGo, Proton Mail.
- **Aurora Store:** 사전 설치되지 않음. 사용자가 직접 설치. 책임은 사용자에게 있음.
- **Push:** 선택적 게이트웨이(UnifiedPush/WebSocket). 합법적 감청 책임은 앱 개발자에게 있음.
- **러시아 호환성:** 공식 공급하지 않음. RTRCA 및 SORM 요구사항이 적용되지 않음. 이는 기술적 비호환성이며 정치적 성명이 아님.
- **E2EE:** X25519, AES-256-GCM / ChaCha20-Poly1305. 키는 TEE에 저장.
- **FBE:** file-based encryption.
- **SMD 버튼:**
  - Privacy Mode: 빨간색.
  - Charge Y-Fill: 흰색 → 노란색 → 초록색.
  - Thermal Hue: 청록색 → 노란색 → 주황색 → 빨간색.
- **이스터 에그:**
  - Roblox, RTRCA.
  - **Mindustry 로딩 화살표:** Mindustry를 열 때 **게임 자체의 로딩 화면** 동안 주소 지정 조명(SMD 4020 버튼 + SK6812 악센트 라인)이 Mindustry 로딩 화살표 애니메이션을 재현합니다 — 수평선 중앙에서 펼쳐지는 그 화살표들 — **로딩 화면과 같은 빛/색**으로.

## 라이선스 (소프트웨어)

- **Linux 커널(기기 변경/패치):** **GPLv2-only**. Linux 커널은 GPLv2-only로 배포되며 **GPLv3와 호환되지 않으므로** 모든 커널 수정은 엄격히 GPLv2-only.
- **프로젝트 userspace 코드(해당 시):** GPLv3 (LICENSE.md 참조).
- **LineageOS / AOSP 기반:** 주로 **Apache License 2.0**. Apache 2.0은 **GPLv3와 호환**(한 제품에 공존 가능)하지만, **혼합 라이선스가 원본을 취소하지 않음**: Apache 2.0으로 들어온 코드는 Apache 2.0으로 유지되며 GPLv3가 그 라이선스를 덮어쓰지 않음.
