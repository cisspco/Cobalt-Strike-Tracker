# Cobalt Strike Snapshot — 2026-10-15 UTC

## 수집 상태
- 페치 성공: www.microsoft.com/en-us/security/blog (검색), cloud.google.com/blog/topics/threat-intelligence (신규 Cobalt Strike 게시물 없음)
- 페치 차단: unit42.paloaltonetworks.com, www.recordedfuture.com, www.thedfirreport.com, www.group-ib.com, hunt.io (전부 DNS 미해결 — egress 차단)
- 검증: 0 (신규) / 미검증: 0 (신규 호스트 없음, 기존 StrikeShark 항목에 CVE 세부사항만 보강) / 검토 필요: 0 (신규 없음)

이번 실행의 WebSearch 6개 쿼리는 모두 기존에 추적 중인 캠페인(StrikeShark/SharkLoader, The Gentlemen, Nitrogen ransomware, Ghostwriter APT, watermark 987654321/678358251 클러스터, hunt.io 2026-01 집계, RST Cloud/Netlas JARM 방법론, OrangeCon 2026 ML 탐지 발표)의 재언급이었음. "미검증" 상태의 "검증"으로의 승격 없음. 신규 공격자 귀속 C2, 신규 해시, 신규 검토 대상 없음.

유일한 보강: SOCRadar IOC Radar 리포트(socradar.io — 알려진 차단 도메인이라 페치 시도 안 함)의 검색 스니펫이 StrikeShark/SharkLoader 캠페인의 초기 침투 벡터로 **CVE-2021-26855**(Exchange ProxyLogon)와 **CVE-2023-46747**(F5 BIG-IP)을 구체적으로 명시함. 이미 "인터넷 노출 앱 악용"으로 기록된 내용과 일치하며, 동일 캠페인의 세 번째 독립 출처 상호 확인(hash/domain 세트는 기존 기록과 동일한 것으로 보임) — `iocs/watermarks-and-profiles.md`에 보강 노트로 추가. 신규 IOC는 아님.

조용한 하루(quiet day) — 2연속 (2026-10-13, 10-14에 이어).

## 최근 캠페인 (최근 60일)

신규 캠페인 보고 없음. 기존 추적 중인 캠페인(StrikeShark/SharkLoader, The Gentlemen, Ghostwriter APT, Nitrogen ransomware)에 대한 추가 세부 정보는 금일 검색에서 CVE 정보 보강 1건 외에 발견되지 않음.

## 공격자 C2 팀서버 (차단 대상) (6)
변경 없음 — 기존 6개 IP (UNC2628/DarkSide, Mandiant/Google Cloud Blog 귀속, 2021년 보고, ~5년 경과 가능성 높음) 유지. 상세는 `iocs/ips.txt` 및 `iocs/needs-review.txt` 참고.

## 검토 필요 — 스캐너 탐지만 된 팀서버 (차단 금지) (34)
변경 없음. 상세는 `iocs/needs-review.txt` 참고.

## JARM 헌팅 신호 (차단 용도 아님)
변경 없음 (2개). 상세는 `iocs/jarm.txt` 참고.

## 워터마크 · 맬리어블 프로파일
StrikeShark 항목에 CVE-2021-26855 / CVE-2023-46747 보강 노트 추가(상세는 `iocs/watermarks-and-profiles.md` 참고). 그 외 변경 없음.

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
- 기타: StrikeShark 캠페인 보강 노트(CVE-2021-26855, CVE-2023-46747) 추가

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
- [Microsoft Security Blog 검색](https://www.microsoft.com/en-us/security/blog/?s=cobalt+strike) — 2026-10-15 — fetched (신규 CS 게시물 없음; 9월 게시물 1건 확인, CS 무관)
- [Google Cloud Threat Intelligence Blog](https://cloud.google.com/blog/topics/threat-intelligence) — 2026-10-15 — fetched (신규 CS 게시물 없음)
- [SOCRadar IOC Radar — StrikeShark/SharkLoader](https://socradar.io/free-tools/ioc-radar/reports/strikeshark-investigating-a-new-campaign-delivering-cobalt-strike-through-sharkloader-f7414ec2fe73) — 검색 스니펫만 (socradar.io, 알려진 차단 도메인 — fetch 시도 안 함) — blocked
- [Unit 42 — Cobalt Strike Team Server](https://unit42.paloaltonetworks.com/cobalt-strike-team-server/) — 2026-10-15 — blocked (DNS 미해결)
- [Recorded Future Research](https://www.recordedfuture.com/research) — 2026-10-15 — blocked (DNS 미해결)
- [The DFIR Report](https://www.thedfirreport.com/) — 2026-10-15 — blocked (DNS 미해결)
- [Group-IB Blog](https://www.group-ib.com/blog/) — 2026-10-15 — blocked (DNS 미해결)
- [Hunt.io — Rare Watermark Links CS 4.10 Team Servers](https://hunt.io/blog/rare-watermark-links-cobalt-strike-team-servers-to-ongoing-suspicious-activity) — 2026-10-15 — blocked (DNS 미해결)
- 이전 실행에서 기록된 모든 출처는 `iocs/watermarks-and-profiles.md` 참고 (중복 재검색만 수행, 신규 출처 없음)
