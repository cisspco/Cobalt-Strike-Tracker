# Cobalt Strike Snapshot — 2026-11-13 UTC

## 수집 상태
- 페치 성공: cloud.google.com/blog/topics/threat-intelligence (신규 Cobalt Strike IOC 없음), cloud.google.com/.../artex-and-friends-enter-agentic-offensive-frameworks (2026-10-30, Cobalt Strike는 역사적 사례로만 1회 언급, C2 IOC 없음), www.microsoft.com/en-us/security/blog (검색, 신규 콘텐츠 없음 — 2021/2022년 게시물만 재노출)
- 페치 차단(신규 시도, 이번 실행에서 최초로 시도·차단 확인): unit42.paloaltonetworks.com, thedfirreport.com, www.recordedfuture.com, www.group-ib.com, research.checkpoint.com, hunt.io — 모두 ENOTFOUND. (프롬프트의 "UNTESTED" 후보 4곳 중 recordedfuture.com·unit42·thedfirreport·group-ib 전부 이번 실행에서 차단으로 확인됨 — 장기적으로 사용 불가)
- 검증: 누적 9건 (C2 IP 6 + 해시 2 + GCTI 크랙판 배경자료 1) / 미검증: 누적 6건 (C2 IP 1 + 도메인 5) / 검토 필요: 46

## 최근 캠페인 (최근 60일)

캠페인 수준의 전적으로 새로운 보고는 이번 실행에서도 없음 (2026-10-13 이후 지속, 31일 연속 조용한 날 — 차단 대상 기준). 이번 실행에서 신규로 확인된 항목:

- **ARTEX (에이전틱 공격용 C2 플랫폼)** — Google Threat Intelligence Group/Mandiant, 2026-10-30 게시. 신규 에이전틱 오펜시브 프레임워크를 다루지만, Cobalt Strike는 "과거 유사 사례"로 한 차례만 언급됨 (펜테스트/레드팀 플랫폼이 악용된 선례). 이 캠페인 자체는 Cobalt Strike를 구성요소로 사용하지 않아 Cobalt Strike 전용 IOC로 기록하지 않음 — 배경 정보로만 남김.

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

## JARM 헌팅 신호 (차단 용도 아님)
- `07d14d16d21d21d00042d41d00041de5fb3038104f457d92ba02e9311512c2` — Cobalt Strike 기본 팀서버 JARM (OpenJDK 11), 일반 헌팅 신호
- `07d14d16d21d21d07c42d41d00041d24a458a375eef0c576d23a7bab9a9fb1` — 동일 기본값의 대체 보고값 (Java 11 SSL 스택), 2차 후보로 기록

## 워터마크 · 맬리어블 프로파일
- **0 / 1** — 크랙판 공통값, 차단 신호 아님 (LOW SIGNAL)
- **100000000 / 666666666 / 987654321 / 678358251 / 688983459** — 크랙판/공유 클러스터 값, 개별 캠페인 귀속 없음 또는 약한 귀속, 차단 신호로 사용 금지.
- **1473793097 / 1357776117** — "The Gentlemen"/CountLoader 체인 특정 값 (미검증, Silent Push)
- **BeudtKgqnlm0Ruvf+VYxuw==** — APT24 특정 워터마크 해시 (검증됨, Mandiant)
- 전체 목록은 `iocs/watermarks-and-profiles.md` 참조 (누적, 이번 실행 신규 추가 없음)

## 파일 해시 (2)
### SHA-256
- 5f37b85687780c089607670040dbb3da2749b91b8adc0aa411fd6280b5fa7103 — beacon — BlackByte ransomware intrusion (ProxyShell Exchange exploitation) — verified
- 7c1f99dca8e5a7897892f9d224a6495023a2cfd2671697d229d355978c415ed2 — loader — KnowledgeDeliver/CVE-2026-5426 — verified

## 호스트 IOC · 행위
- SMB BEACON named pipe `\\.\pipe\UIA_PIPE_*` (UNC2628/DarkSide)
- DNS BEACON 서브도메인 패턴 `h.dns.<C2 domain>`, `ridoj4.<8자>.dns.<C2 domain>` 등 (UNC4393/BASTA)
- 자세한 내용은 `iocs/watermarks-and-profiles.md` 참조

## 이번 실행 변경사항
- 신규 C2 (검증, 차단 대상): 없음
- 신규 C2 (미검증, 차단 대상 아님): 없음
- 신규 해시: 없음
- 승격(미검증→검증): 없음
- 분류 변경: 없음
- 검토 필요 신규 추가: 없음
- 신규 캠페인 배경 노트: ARTEX 에이전틱 C2 플랫폼 (Cobalt Strike는 역사적 언급뿐, 전용 IOC 없음 — 블로터에 기록하지 않음)
- 네트워크 범위 확인: unit42.paloaltonetworks.com, thedfirreport.com, www.recordedfuture.com, www.group-ib.com, research.checkpoint.com, hunt.io — 이번 실행에서 신규로 차단 확인 (ENOTFOUND). 프롬프트가 지정한 "UNTESTED" 후보 사이트 전부가 이 샌드박스에서는 도달 불가능함이 확인됨.

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
- [Google Cloud — Threat Intelligence Blog](https://cloud.google.com/blog/topics/threat-intelligence) — 2026-11-13 — fetched (신규 CS 콘텐츠 없음)
- [Google Cloud — "ARTEX and Friends: Enter Agentic Offensive Frameworks"](https://cloud.google.com/blog/topics/threat-intelligence/artex-and-friends-enter-agentic-offensive-frameworks) — 2026-10-30 — fetched (Cobalt Strike 역사적 언급뿐, IOC 없음)
- [Microsoft Security Blog — "cobalt strike" 검색](https://www.microsoft.com/en-us/security/blog/?s=cobalt+strike) — 2026-11-13 — fetched (신규 CS 콘텐츠 없음)
- unit42.paloaltonetworks.com — 2026-11-13 — blocked (ENOTFOUND, 신규 시도)
- thedfirreport.com — 2026-11-13 — blocked (ENOTFOUND, 신규 시도)
- www.recordedfuture.com — 2026-11-13 — blocked (ENOTFOUND, 신규 시도)
- www.group-ib.com — 2026-11-13 — blocked (ENOTFOUND, 신규 시도)
- research.checkpoint.com — 2026-11-13 — blocked (ENOTFOUND, 신규 시도)
- hunt.io — 2026-11-13 — blocked (ENOTFOUND, 신규 시도)
