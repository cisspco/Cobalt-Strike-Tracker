# Cobalt Strike Snapshot — 2026-11-14 UTC

## 수집 상태
- 페치 성공: www.microsoft.com/en-us/security/blog/2024/09/26/storm-0501-ransomware-attacks-expanding-to-hybrid-cloud-environments/ (신규, 이번 실행에서 최초로 전체 본문 획득), cloud.google.com/blog/topics/threat-intelligence/defining-cobalt-strike-components (신규, 이번 실행에서 최초로 전체 본문 획득 — 2021-12-10 Mandiant 게시물)
- 페치 차단(이번 실행에서 신규로 시도·차단 확인): www.silentpush.com/blog/gentlemen-ransomware/, hunt.io/blog/rare-watermark-links-cobalt-strike-team-servers-to-ongoing-suspicious-activity, unit42.paloaltonetworks.com/cobalt-strike-team-server/, thedfirreport.com/2025/01/27/cobalt-strike-and-a-pair-of-socks-lead-to-lockbit-ransomware/, www.group-ib.com/blog/, www.recordedfuture.com/research/2025-year-in-review-malicious-infrastructure, research.checkpoint.com/2026/dfir-report-the-gentlemen/, securelist.com/strikeshark-campaign/120326/ — 전부 ENOTFOUND. (프롬프트의 "UNTESTED" 후보 4곳: recordedfuture.com·thedfirreport·group-ib·unit42 전부 이번 실행에서도 재확인 차단됨)
- 검증: 누적 17건 (C2 IP 6 + 해시 8 + 워터마크 666/Storm-0501 1 + GCTI 배경자료 1 + 팀서버 기술참조 1) / 미검증: 누적 7건 (C2 IP 1 + 도메인 5 + JARM 후보 1) / 검토 필요: 46

## 최근 캠페인 (최근 60일)

캠페인 수준의 전적으로 새로운 보고는 이번 실행에서도 없음 (60일 이내 신규 캠페인 기준, 32일 연속 조용한 날). 다만 이번 실행에서 처음으로 정식 기사 본문을 확보한 기존 캠페인이 있어 아래 별도 항목으로 기록:

### Storm-0501 — Embargo 랜섬웨어 (2024-09, 60일 창 밖이지만 최초 본문 검증)
- 대상: 하이브리드 클라우드 환경을 사용하는 기업
- 초기 침투: 탈취된 자격증명을 이용한 측면 이동
- Cobalt Strike 역할: 측면 이동 도구 (Beacon → rundll32.exe/.dll, regsvr32.exe/.ocx) → Embargo 랜섬웨어 배포로 이어지는 체인
- 관측 시점: 2024-09 (2025-08 업데이트 존재)
- 특이사항: 워터마크 "666" — 정상 라이선스는 9자리인데, 이 행위자가 의도적으로 3자리 값으로 변조. 공유/크랙판 기본값(0/1/987654321 등)과 달리 행위자 고유 피벗으로 간주.
- 출처: Microsoft Security Blog (fetched, verified)

- 참고(재확인, 변경 없음): The Gentlemen/CountLoader (91.107.247[.]163, Silent Push/Check Point), SNOWLIGHT/GoCobaltStrike, Aur0ra 랜섬웨어, FrostBeacon, Nitrogen→Sliver/BlackCat, Bumblebee→Cobalt Strike, RedNovember, 가짜 KeePass→ESXi/Black Basta IAB 워터마크 — 이번 실행 검색에서 재노출, 상세 변경 없음.

## 공격자 C2 팀서버 (차단 대상) (6)
- 108.61.242[.]65 — KnowledgeDeliver/CVE-2026-5426 또는 BlackByte 관련 검증된 캠페인 C2 — verified
- 109.206.243[.]59 — 상동 — verified
- 146.70.78[.]43 — 상동 — verified
- 45.150.108[.]213 — 상동 — verified
- 87.120.254[.]39 — 상동 — verified
- 92.204.160[.]240 — 상동 — verified

(도메인 없음)

## 검토 필요 — 스캐너 탐지만 된 팀서버 (차단 금지) (46)
- 변경 없음, 기존 46건 유지. 상세는 `iocs/needs-review.txt` 참조.

## JARM 헌팅 신호 (차단 용도 아님) (3)
- `07d14d16d21d21d00042d41d00041de5fb3038104f457d92ba02e9311512c2` — Cobalt Strike 기본 팀서버 JARM (OpenJDK 11), 일반 헌팅 신호 — unverified
- `07d14d16d21d21d07c42d41d00041d24a458a375eef0c576d23a7bab9a9fb1` — 동일 기본값의 대체 보고값 (Java 11 SSL 스택), 2차 후보 — unverified
- `2ad2ad16d2ad2ad00042d42d00042ddb04deffa1705e2edc44cae1ed24a4da` — 🆕 socat/iptables 뒤로 리다이렉트된 팀서버의 3번째 후보값(Kali 기반 예시); 2026-11-12 기록에서 잘려 있던 값이 이번 실행에서 완성됨 — unverified

## 워터마크 · 맬리어블 프로파일
- **0 / 1** — 크랙판 공통값, 차단 신호 아님 (LOW SIGNAL)
- **100000000 / 666666666 / 987654321 / 678358251 / 688983459** — 크랙판/공유 클러스터 값, 개별 캠페인 귀속 없음 또는 약한 귀속, 차단 신호로 사용 금지.
- **1473793097 / 1357776117** — "The Gentlemen"/CountLoader 체인 특정 값 (미검증, Silent Push)
- **BeudtKgqnlm0Ruvf+VYxuw==** — APT24 특정 워터마크 해시 (검증됨, Mandiant)
- **🆕 666** — Storm-0501 고유 변조 워터마크 (검증됨, Microsoft, 2024-09-26). 정상 9자리 라이선스 값을 "666"으로 변조; 공유/크랙판 기본값이 아닌 행위자 고유 피벗.
- **🆕 팀서버 기술 참조** — Mandiant "Defining Cobalt Strike Components" (검증됨, 2021-12-10, 이번 실행에서 최초 전체 본문 확보): 팀서버 기본 포트 TCP 50050, 평문 비콘 명령 로그 구조, 트라이얼판 EICAR 문자열 삽입, 스테이저 URL 4자 체크섬 규칙 등 — 신규 IOC는 아니며 탐지 참고 정보.
- 전체 목록은 `iocs/watermarks-and-profiles.md` 참조 (누적)

## 파일 해시 (8)
### SHA-256
- 53e2dec3e16a0ff000a8c8c279eeeca8b4437edb8ec8462bfbd9f64ded8072d9 — beacon — 🆕 Storm-0501/Embargo ransomware — verified
- 5f37b85687780c089607670040dbb3da2749b91b8adc0aa411fd6280b5fa7103 — beacon — BlackByte ransomware intrusion (ProxyShell Exchange exploitation) — verified
- 7c1f99dca8e5a7897892f9d224a6495023a2cfd2671697d229d355978c415ed2 — loader — KnowledgeDeliver/CVE-2026-5426 — verified
- 827f7178802b2e92988d7cff349648f334bc86317b0b628f4bb9264285fccf5f — beacon — 🆕 Storm-0501/Embargo ransomware — verified
- caa21a8f13a0b77ff5808ad7725ff3af9b74ce5b67426c84538b8fa43820a031 — beacon — 🆕 Storm-0501/Embargo ransomware — verified
- d37dc37fdcebbe0d265b8afad24198998ae8c3b2c6603a9258200ea8a1bd7b4a — beacon — 🆕 Storm-0501/Embargo ransomware — verified
- de09ec092b11a1396613846f6b082e1e1ee16ea270c895ec6e4f553a13716304 — beacon — 🆕 Storm-0501/Embargo ransomware — verified
- ee80f3e3ad43a283cbc83992e235e4c1b03ff3437c880be02ab1d15d92a8348a — beacon — 🆕 Storm-0501/Embargo ransomware — verified

## 호스트 IOC · 행위
- SMB BEACON named pipe `\\.\pipe\UIA_PIPE_*` (UNC2628/DarkSide)
- DNS BEACON 서브도메인 패턴 `h.dns.<C2 domain>`, `ridoj4.<8자>.dns.<C2 domain>` 등 (UNC4393/BASTA)
- Beacon이 `rundll32.exe`(.dll)/`regsvr32.exe`(.ocx)로 실행됨 (Storm-0501)
- 자세한 내용은 `iocs/watermarks-and-profiles.md` 참조

## 이번 실행 변경사항
- 신규 C2 (검증, 차단 대상): 없음
- 신규 C2 (미검증, 차단 대상 아님): 없음
- 신규 해시: 6건 (Storm-0501/Embargo ransomware, Cobalt Strike Beacon, 전부 verified)
- 승격(미검증→검증): 없음
- 분류 변경: 없음
- 검토 필요 신규 추가: 없음
- 신규 JARM 후보: 1건 (2ad2ad16d2ad2ad00042d42d00042ddb04deffa1705e2edc44cae1ed24a4da, unverified, 이전 실행에서 잘려있던 값 완성)
- 신규 워터마크: 1건 (666, Storm-0501, verified)
- 신규 캠페인 배경 노트: Storm-0501/Embargo ransomware 보고서 본문 최초 확보 (2024-09 활동, 60일 창 밖이지만 Cobalt Strike 구성요소 확정 캠페인으로 해시/워터마크 신규 기록)
- 네트워크 범위 확인: silentpush.com, hunt.io, unit42.paloaltonetworks.com, thedfirreport.com, group-ib.com, recordedfuture.com, research.checkpoint.com, securelist.com — 이번 실행에서 재시도, 전부 차단 확인 (ENOTFOUND). microsoft.com과 cloud.google.com의 특정 기사 URL(블로그 검색/색인 페이지가 아닌)에 대해 이번 실행 최초로 전체 본문 확보 성공.

## 차단 운영 포맷 (복붙용)

### Domain/IP blocklist (un-defanged, one per line — attributed attacker C2 only)
```
108.61.242.65
109.206.243.59
146.70.78.43
45.150.108.213
87.120.254.39
92.204.160.240
```

## 출처
- [Microsoft Security Blog — "Storm-0501: Ransomware attacks expanding to hybrid cloud environments"](https://www.microsoft.com/en-us/security/blog/2024/09/26/storm-0501-ransomware-attacks-expanding-to-hybrid-cloud-environments/) — 2024-09-26 (업데이트 2025-08-27) — fetched
- [Google Cloud / Mandiant — "Defining Cobalt Strike Components"](https://cloud.google.com/blog/topics/threat-intelligence/defining-cobalt-strike-components) — 2021-12-10 — fetched
- www.silentpush.com/blog/gentlemen-ransomware/ — 2026-11-14 — blocked (ENOTFOUND)
- hunt.io/blog/rare-watermark-links-cobalt-strike-team-servers-to-ongoing-suspicious-activity — 2026-11-14 — blocked (ENOTFOUND)
- unit42.paloaltonetworks.com/cobalt-strike-team-server/ — 2026-11-14 — blocked (ENOTFOUND)
- thedfirreport.com/2025/01/27/cobalt-strike-and-a-pair-of-socks-lead-to-lockbit-ransomware/ — 2026-11-14 — blocked (ENOTFOUND)
- www.group-ib.com/blog/ — 2026-11-14 — blocked (ENOTFOUND)
- www.recordedfuture.com/research/2025-year-in-review-malicious-infrastructure — 2026-11-14 — blocked (ENOTFOUND)
- research.checkpoint.com/2026/dfir-report-the-gentlemen/ — 2026-11-14 — blocked (ENOTFOUND)
- securelist.com/strikeshark-campaign/120326/ — 2026-11-14 — blocked (ENOTFOUND)
