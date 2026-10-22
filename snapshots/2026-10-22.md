# Cobalt Strike Snapshot — 2026-10-22 UTC

## 수집 상태
- 페치 성공: microsoft.com/en-us/security/blog (검색 결과 페이지, Cobalt Strike 무관 신규 게시물 1건 확인), cloud.google.com/blog/topics/threat-intelligence (목록 페이지, 신규 게시물 3건 확인), cloud.google.com/blog/topics/threat-intelligence/financially-motivated-threat-actor-breeze-comet-targets-brazil (2026-09-01, BREEZE COMET — Cobalt Strike 무관, COBALTSPIN이라는 별개의 커스텀 Rust 터널러), cloud.google.com/blog/topics/threat-intelligence/armory-castle-exploits-beyondtrust (2026-10-15, ARMORY CASTLE/CVE-2026-102764 — Cobalt Strike 무관, SAWFLY 웹셸·BARECLAW 터널러만 확인)
- 페치 차단: hunt.io (워터마크 기사 2건, DNS 미해결), www.silentpush.com, gbhackers.com, community.gurucul.com, unit42.paloaltonetworks.com, threatfox.abuse.ch, netlas.io, www.recordedfuture.com, www.thedfirreport.com, www.group-ib.com — 전부 DNS 미해결
- 검증: 0 (신규) / 미검증: 0 (신규 호스트 없음) / 검토 필요: 0 (신규 없음)

이번 실행의 WebSearch 6개 쿼리 결과는 전부 기존에 추적 중인 캠페인/지표의 재언급이었음: StrikeShark/SharkLoader(기존 기록됨), The Gentlemen/CountLoader 워터마크 1473793097/1357776117(기존 기록됨), Nitrogen ransomware 워터마크 678358251(기존 기록됨), ThreatFox 개별 C2 엔트리(107.174.14.102:443, 47.103.214.7:18443, 206.119.178.109:18443 — 전부 `iocs/needs-review.txt`에 이미 있음), watermark 987654321 클러스터(기존 기록됨), hunt.io "Rare Watermark Links Cobalt Strike 4.10 Team Servers" 기사(기존 기록됨, 2026-10-03 항목), Unit 42의 일반 팀서버/맬리어블 C2 헌팅 방법론(배경 정보, 신규 IOC 없음), OrangeCon 2026 ML 탐지 발표(기존 기록됨).

cloud.google.com Threat Intelligence 블로그에서 신규 게시물 2건(ARMORY CASTLE/BeyondTrust CVE-2026-102764, BREEZE COMET/브라질 금융권)을 원문까지 읽었으나 둘 다 Cobalt Strike를 전혀 언급하지 않음 — ARMORY CASTLE은 SAWFLY PHP 웹셸과 BARECLAW SOCKS5-over-WebSocket 터널러만 사용, BREEZE COMET은 COBALTSPIN(별개의 커스텀 Rust 터널러, 이름만 유사)과 XWORM/인포스틸러를 사용. 둘 다 Cobalt Strike 관련 IOC로 기록하지 않음.

10일 연속 조용한 하루(quiet day) — 2026-10-13 ~ 10-21에 이어.

## 최근 캠페인 (최근 60일)

신규 캠페인 보고 없음. 기존 추적 중인 캠페인(StrikeShark/SharkLoader, The Gentlemen, Ghostwriter APT, Nitrogen ransomware, RedNovember)에 대한 추가 세부 정보도 금일 검색에서는 발견되지 않음 — 전부 기존 보고의 재인덱싱. 금일 새로 확인한 두 건(ARMORY CASTLE, BREEZE COMET)은 Cobalt Strike가 구성요소로 확인되지 않아 이 섹션에 포함하지 않음.

## 공격자 C2 팀서버 (차단 대상) (6)
변경 없음 — 기존 6개 IP 유지. 상세는 `iocs/ips.txt` 참고.

## 검토 필요 — 스캐너 탐지만 된 팀서버 (차단 금지) (34)
변경 없음. 상세는 `iocs/needs-review.txt` 참고.

## JARM 헌팅 신호 (차단 용도 아님)
변경 없음 (2개). 상세는 `iocs/jarm.txt` 참고.

## 워터마크 · 맬리어블 프로파일
변경 없음. 상세는 `iocs/watermarks-and-profiles.md` 참고.

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
- 기타: cloud.google.com Threat Intelligence 블로그에서 신규 게시물 2건(ARMORY CASTLE/BeyondTrust 제로데이 CVE-2026-102764, BREEZE COMET/브라질 금융권 표적) 원문 확인 — 둘 다 Cobalt Strike 무관으로 확인되어 기록 제외. 그 외 8개 핵심 소스(hunt.io ×2, silentpush.com, gbhackers.com, community.gurucul.com, unit42.paloaltonetworks.com, threatfox.abuse.ch, netlas.io) 재시도 — 여전히 전부 DNS 미해결로 차단.

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
- [Google Cloud Threat Intelligence — blog index](https://cloud.google.com/blog/topics/threat-intelligence) — 2026-10-22 — fetched (목록 페이지, 신규 게시물 3건 확인)
- [Google Cloud — Financially Motivated Threat Actor BREEZE COMET Targets Brazil](https://cloud.google.com/blog/topics/threat-intelligence/financially-motivated-threat-actor-breeze-comet-targets-brazil) — 2026-09-01 — fetched (Cobalt Strike 무관, COBALTSPIN 별개 도구)
- [Google Cloud — ARMORY CASTLE Exploits BeyondTrust](https://cloud.google.com/blog/topics/threat-intelligence/armory-castle-exploits-beyondtrust) — 2026-10-15 — fetched (Cobalt Strike 무관, SAWFLY/BARECLAW 사용)
- [Hunt.io — Rare Watermark Links Cobalt Strike 4.10 Team Servers](https://hunt.io/blog/rare-watermark-links-cobalt-strike-team-servers-to-ongoing-suspicious-activity) — 2026-10-22 — blocked (DNS 미해결)
- [Hunt.io — Complete Guide to Hunting Cobalt Strike Part 3](https://hunt.io/blog/guide-hunting-cobalt-strike-part-3-automated-discovery) — 2026-10-22 — blocked (DNS 미해결)
- [Silent Push — No Place to Hide (The Gentlemen)](https://www.silentpush.com/blog/gentlemen-ransomware/) — 2026-10-22 — blocked (DNS 미해결)
- [GBHackers — Nitrogen Ransomware](https://gbhackers.com/nitrogen-ransomware-uses-cobalt-strike-and-log-wiping/) — 2026-10-22 — blocked (DNS 미해결)
- [Gurucul — StrikeShark](https://community.gurucul.com/articles/ThreatResearch/StrikeShark-Investigating-a-New-25-6-2026) — 2026-10-22 — blocked (DNS 미해결)
- [Unit 42 — Cobalt Strike Team Server](https://unit42.paloaltonetworks.com/cobalt-strike-team-server/) — 2026-10-22 — blocked (DNS 미해결)
- [ThreatFox IOC 1892469](https://threatfox.abuse.ch/ioc/1892469/json/) — 2026-10-22 — blocked (DNS 미해결)
- [Netlas.io — C2 Hunting (RST Cloud)](https://netlas.io/blog/%D1%812_hunting_by_rst_cloud/) — 2026-10-22 — blocked (DNS 미해결)
- 이전 실행에서 기록된 모든 출처는 `iocs/watermarks-and-profiles.md` 참고 (중복 재검색만 수행, 신규 출처 없음)
