# Cobalt Strike Snapshot — 2026-10-20 UTC

## 수집 상태
- 페치 성공: cloud.google.com/blog/topics/threat-intelligence (목록 페이지, 2026년 게시물 다수 확인 — Cobalt Strike 관련 신규 게시물 없음), cloud.google.com/blog/topics/threat-intelligence/financially-motivated-threat-actor-breeze-comet-targets-brazil (2026-09-01, Cobalt Strike 무관 — COBALTSPIN은 별도의 Rust 터널러), cloud.google.com/blog/topics/threat-intelligence/unc6671-targets-financial-services-and-enterprise-cloud-environments (2026-08-06, Cobalt Strike 무관 — AiTM 비싱 체인), www.microsoft.com/en-us/security/blog (검색 페이지, 2021-2024년 기존 게시물만 재확인, 신규 없음)
- 페치 차단: community.gurucul.com, www.silentpush.com, hunt.io, gbhackers.com, unit42.paloaltonetworks.com, netlas.io, threatfox.abuse.ch, thedfirreport.com, www.recordedfuture.com, www.group-ib.com (전부 DNS 미해결 — 기존 차단 목록과 동일, 오늘 재시도한 thedfirreport.com/recordedfuture.com/group-ib.com도 차단 확인됨 — "미테스트" 후보였으나 모두 차단으로 판명)
- 검증: 0 (신규) / 미검증: 0 (신규 호스트 없음) / 검토 필요: 0 (신규 없음)

이번 실행의 WebSearch 6개 쿼리 결과는 전부 기존에 추적 중인 캠페인/지표의 재언급이었음(StrikeShark/SharkLoader — 도메인 connect-microsoft.com/ms-record.com/ms-record.top/ms-tray.top/harivo.vip, MD5 해시 7개 전부 기존 `iocs/unverified-domains.txt` 및 `iocs/watermarks-and-profiles.md`에 이미 기록됨; The Gentlemen/CountLoader 랜섬웨어 제휴 — 워터마크 1473793097/1357776117 기존 기록됨; Nitrogen ransomware — 워터마크 678358251 기존 기록됨; ThreatFox 개별 C2 엔트리 107.174.14.102:443·47.103.214.7:18443·206.119.178.109:18443 — 모두 이미 `iocs/needs-review.txt`에 기록됨; watermark 987654321 클러스터 — 기존 기록됨; JARM 헌팅 방법론, 기본 CS 인증서 시리얼 8BB00EE, Hunt.io 집계 통계 — 전부 기존 기록됨). 신규 호스트, 신규 해시, "미검증→검증" 승격 없음.

처음으로 시도한 thedfirreport.com, www.recordedfuture.com, www.group-ib.com — 전부 DNS 미해결로 차단 확인(이전 실행에서 이미 차단 목록에 있었으나 재확인). cloud.google.com Threat Intelligence 블로그에서 BREEZE COMET(브라질 금융권 타겟) 및 UNC6671(비싱/AiTM) 두 건의 2026년 신규 게시물을 직접 열람했으나 둘 다 Cobalt Strike를 전혀 언급하지 않아 본 트래커와 무관(COBALTSPIN은 CS와 무관한 커스텀 Rust 터널러).

조용한 하루(quiet day) — 8연속 (2026-10-13 ~ 10-19에 이어).

## 최근 캠페인 (최근 60일)

신규 캠페인 보고 없음. 기존 추적 중인 캠페인(StrikeShark/SharkLoader, The Gentlemen, Ghostwriter APT, Nitrogen ransomware, RedNovember)에 대한 추가 세부 정보도 금일 검색에서는 발견되지 않음 — 전부 기존 보고의 재인덱싱.

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
- 기타: thedfirreport.com, www.recordedfuture.com, www.group-ib.com 직접 fetch 재시도 — 전부 DNS 미해결로 차단 재확인. cloud.google.com Threat Intelligence 블로그의 2026년 신규 게시물(BREEZE COMET, UNC6671) 직접 열람 — 둘 다 Cobalt Strike 무관으로 확인, 신규 내용 없음.

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
- [Google Cloud Threat Intelligence — blog index](https://cloud.google.com/blog/topics/threat-intelligence) — 2026-10-20 — fetched (목록 페이지, Cobalt Strike 신규 게시물 없음)
- [Google Cloud — Financially Motivated Threat Actor BREEZE COMET Targets Brazil](https://cloud.google.com/blog/topics/threat-intelligence/financially-motivated-threat-actor-breeze-comet-targets-brazil) — 2026-09-01 — fetched (Cobalt Strike 무관)
- [Google Cloud — UNC6671 Targets Financial Services and Enterprise Cloud Environments](https://cloud.google.com/blog/topics/threat-intelligence/unc6671-targets-financial-services-and-enterprise-cloud-environments) — 2026-08-06 — fetched (Cobalt Strike 무관)
- [Microsoft Security Blog — search](https://www.microsoft.com/en-us/security/blog/?s=cobalt+strike) — 2026-10-20 — fetched (2021-2024년 기존 게시물만, 신규 없음)
- [The DFIR Report — Cobalt Strike search](https://thedfirreport.com/?s=cobalt+strike) — 2026-10-20 — blocked (DNS 미해결)
- [Recorded Future — Cobalt Strike research](https://www.recordedfuture.com/research/cobalt-strike) — 2026-10-20 — blocked (DNS 미해결)
- [Group-IB blog search](https://www.group-ib.com/blog/?s=cobalt+strike) — 2026-10-20 — blocked (DNS 미해결)
- [Gurucul — StrikeShark](https://community.gurucul.com/articles/ThreatResearch/StrikeShark-Investigating-a-New-25-6-2026) — 2026-10-20 — blocked (DNS 미해결)
- [Silent Push — The Gentlemen](https://www.silentpush.com/blog/gentlemen-ransomware/) — 2026-10-20 — blocked (DNS 미해결)
- [Hunt.io — Rare Watermark Links CS Team Servers](https://hunt.io/blog/rare-watermark-links-cobalt-strike-team-servers-to-ongoing-suspicious-activity) — 2026-10-20 — blocked (DNS 미해결)
- [GBHackers — Nitrogen ransomware](https://gbhackers.com/nitrogen-ransomware-uses-cobalt-strike-and-log-wiping/) — 2026-10-20 — blocked (DNS 미해결)
- [Unit 42 — Cobalt Strike Team Server](https://unit42.paloaltonetworks.com/cobalt-strike-team-server/) — 2026-10-20 — blocked (DNS 미해결)
- [Netlas.io — RST Cloud C2 hunting](https://netlas.io/blog/%D1%812_hunting_by_rst_cloud/) — 2026-10-20 — blocked (DNS 미해결)
- [ThreatFox IOC 1892469](https://threatfox.abuse.ch/ioc/1892469/json/) — 2026-10-20 — blocked (DNS 미해결)
- 이전 실행에서 기록된 모든 출처는 `iocs/watermarks-and-profiles.md` 참고 (중복 재검색만 수행, 신규 출처 없음)
