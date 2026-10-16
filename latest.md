# Cobalt Strike Snapshot — 2026-10-16 UTC

## 수집 상태
- 페치 성공: www.microsoft.com/en-us/security/blog (검색, 신규 CS 게시물 없음), cloud.google.com/blog/topics/threat-intelligence (신규 CS 게시물 없음)
- 페치 차단: hunt.io, unit42.paloaltonetworks.com, netlas.io, www.recordedfuture.com, www.thedfirreport.com, www.group-ib.com (전부 DNS 미해결 — egress 차단, 기존 실행들과 동일)
- 검증: 0 (신규) / 미검증: 0 (신규 호스트 없음, 기존 노트에 컨텍스트만 보강) / 검토 필요: 0 (신규 없음)

이번 실행의 WebSearch 6개 쿼리는 모두 기존에 추적 중인 캠페인(StrikeShark/SharkLoader, The Gentlemen, Nitrogen ransomware, Ghostwriter APT, watermark 987654321/678358251 클러스터, hunt.io 집계, RST Cloud/Netlas JARM 방법론, OrangeCon 2026 ML 탐지 발표)의 재언급이었음. "미검증" 상태의 "검증"으로의 승격 없음. 신규 공격자 귀속 C2, 신규 해시, 신규 검토 대상 없음.

보강 2건 (모두 hunt.io 검색 스니펫, 소스 자체는 이번 실행에서도 fetch 차단 — DNS 미해결):
1. Cobalt Strike 팀서버 기본(out-of-the-box) 자체서명 TLS 인증서 일련번호 `8BB00EE` — 워터마크 0/1과 동일한 저신호(LOW SIGNAL) 성격, 차단/귀속 판단에 사용 금지. `iocs/watermarks-and-profiles.md`에 추가.
2. 2025년 전체 집계치: 고유 IP 8,868개가 Cobalt Strike 인프라로 관측됨(기존에 기록된 2026년 1월 집계 1,921개와 별개 수치). 개별 귀속 없는 집계 트렌드 정보일 뿐 — IOC로 사용 불가.

조용한 하루(quiet day) — 4연속 (2026-10-13, 10-14, 10-15에 이어).

## 최근 캠페인 (최근 60일)

신규 캠페인 보고 없음. 기존 추적 중인 캠페인(StrikeShark/SharkLoader, The Gentlemen, Ghostwriter APT, Nitrogen ransomware)에 대한 추가 세부 정보도 금일 검색에서는 발견되지 않음(기존 보고의 재인덱싱만 확인).

## 공격자 C2 팀서버 (차단 대상) (6)
변경 없음 — 기존 6개 IP 유지. 상세는 `iocs/ips.txt` 및 `iocs/needs-review.txt` 참고.

## 검토 필요 — 스캐너 탐지만 된 팀서버 (차단 금지) (34)
변경 없음. 상세는 `iocs/needs-review.txt` 참고.

## JARM 헌팅 신호 (차단 용도 아님)
변경 없음 (2개). 상세는 `iocs/jarm.txt` 참고.

## 워터마크 · 맬리어블 프로파일
기본 인증서 일련번호 `8BB00EE` 및 2025년 집계 IP 수(8,868) 보강 노트 추가(상세는 `iocs/watermarks-and-profiles.md` 참고). 그 외 변경 없음.

## 파일 해시 (2)
변경 없음. 상세는 `iocs/sha256.txt` 참고.

## 호스트 IOC · 행위
- UNC4393/BASTA DNS BEACON 서브호스트 네이밍 패턴 (`h.dns.<C2>`, `ridoj4.<8char>.dns.<C2>` 등) — 기존 기록, 변경 없음.
- UNC2628/DarkSide — Slack API를 통한 C3-over-Slack BEACON 프록싱, SMB named pipe `\\.\pipe\UIA_PIPE_*` — 기존 기록, 변경 없음.

## 이번 실행 변경사항
- 신규 C2: 없음
- 신규 해시: 없음
- 승격(미검증→검증): 없음
- 분류 변경: 없음
- 기타: 기본 인증서 일련번호 `8BB00EE` 저신호 노트 추가, 2025년 전체 집계 IP 수(8,868) 트렌드 노트 추가

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
- [Microsoft Security Blog 검색](https://www.microsoft.com/en-us/security/blog/?s=cobalt+strike) — 2026-10-16 — fetched (신규 CS 게시물 없음; 최신 결과는 2026-09-03 ASCII smuggling 게시물로 CS 무관)
- [Google Cloud Threat Intelligence Blog](https://cloud.google.com/blog/topics/threat-intelligence) — 2026-10-16 — fetched (신규 CS 게시물 없음; ShinyHunters/PeopleSoft, BREEZE COMET 게시물 확인되었으나 CS 언급 없음)
- [Hunt.io — Complete Guide to Hunting Cobalt Strike Part 4: C2 Feeds & API Automation](https://hunt.io/blog/guide-hunting-cobalt-strike-part-4-c2-feeds-api) — 검색 스니펫만 (fetch 시도, DNS 미해결) — blocked
- [Unit 42 — Cobalt Strike Team Server](https://unit42.paloaltonetworks.com/cobalt-strike-team-server/) — 2026-10-16 — blocked (DNS 미해결)
- [Netlas.io — RST Cloud C2 Hunting](https://netlas.io/blog/%D1%812_hunting_by_rst_cloud/) — 2026-10-16 — blocked (DNS 미해결)
- [Recorded Future Research](https://www.recordedfuture.com/research) — 2026-10-16 — blocked (DNS 미해결)
- [The DFIR Report](https://www.thedfirreport.com/) — 2026-10-16 — blocked (DNS 미해결)
- [Group-IB Blog](https://www.group-ib.com/blog/) — 2026-10-16 — blocked (DNS 미해결)
- 이전 실행에서 기록된 모든 출처는 `iocs/watermarks-and-profiles.md` 참고 (중복 재검색만 수행, 신규 출처 없음)
