# Cobalt Strike Snapshot — 2026-10-24 UTC

## 수집 상태
- 페치 성공: microsoft.com/en-us/security/blog (목록 페이지, Cobalt Strike 관련 신규 게시물 없음), cloud.google.com/blog/topics/threat-intelligence (목록 페이지, Cobalt Strike 관련 신규 게시물 없음)
- 페치 차단: community.gurucul.com (StrikeShark 원문, DNS 미해결), silentpush.com (The Gentlemen 원문, DNS 미해결), hunt.io (Rare Watermark 원문, DNS 미해결), unit42.paloaltonetworks.com (team-server 및 malleable-c2 원문, DNS 미해결, 2건), gbhackers.com (Nitrogen ransomware 원문, DNS 미해결), netlas.io (RST Cloud JARM 헌팅 원문, DNS 미해결), securelist.com (StrikeShark 원문, DNS 미해결), threatfox.abuse.ch (개별 IOC 페이지, DNS 미해결), recordedfuture.com (DNS 미해결, 신규 시도), thedfirreport.com (DNS 미해결, 신규 시도), group-ib.com (DNS 미해결, 신규 시도)
- 검증: 0 (신규) / 미검증: 0 (신규 호스트 없음) / 검토 필요: 0 (신규 없음)

이번 실행은 지시사항에 명시된 6개 WebSearch 쿼리를 모두 수행했으며, 결과는 전부 기존에 추적 중인 캠페인/지표의 재언급이었음: StrikeShark/SharkLoader(기존 기록됨), The Gentlemen/CountLoader 워터마크 1473793097/1357776117(기존 기록됨), watermark 987654321/666666666/678358251 클러스터(기존 기록됨), ThreatFox 개별 C2 엔트리 (107.174.14.102:443, 47.103.214.7:18443, 206.119.178.109:18443 — 전부 `iocs/needs-review.txt`에 이미 있음), hunt.io "Rare Watermark Links Cobalt Strike 4.10 Team Servers" 기사(기존 기록됨), Unit42의 team-server/malleable-C2 연구(일반론, 특정 캠페인·IOC 없음, 신규 기록 불필요), OrangeCon 2026 ML 탐지 발표(기존 기록됨), Operation Morpheus 법집행 조치(기존 기록됨, 배경 정보).

지시사항이 신규로 시도해보라고 명시한 3개 출처(recordedfuture.com, thedfirreport.com, group-ib.com)를 이번 실행에서 처음 직접 WebFetch로 시도했으나 전부 DNS 미해결(ENOTFOUND)로 차단됨 — "도달 가능할 경우 강조하라"는 지시와 반대로, 이 세 출처 모두 이 샌드박스에서 도달 불가능함을 확인. 기존에 알려진 차단 목록(thehackernews.com 등)에 더해 community.gurucul.com, silentpush.com, hunt.io, unit42.paloaltonetworks.com, gbhackers.com, netlas.io, securelist.com, threatfox.abuse.ch도 전부 DNS 미해결로 재확인됨 — 이 샌드박스에서 실질적으로 도달 가능한 출처는 microsoft.com과 cloud.google.com 두 곳뿐.

microsoft.com 보안 블로그 및 cloud.google.com Threat Intelligence 블로그 색인을 모두 재확인했으나 Cobalt Strike·랜섬웨어 전구체·악성 C2 관련 신규 게시물 없음.

12일 연속 조용한 하루(quiet day) — 2026-10-13 ~ 10-23에 이어.

## 최근 캠페인 (최근 60일)

신규 캠페인 보고 없음. 기존 추적 중인 캠페인(StrikeShark/SharkLoader, The Gentlemen, Ghostwriter APT, Nitrogen ransomware, RedNovember)에 대한 추가 세부 정보도 금일 검색에서는 발견되지 않음 — 전부 기존 보고의 재인덱싱.

## 공격자 C2 팀서버 (차단 대상) (6)
변경 없음 — 기존 6개 IP 유지. 상세는 `iocs/ips.txt` 참고.

## 검토 필요 — 스캐너 탐지만 된 팀서버 (차단 금지) (34)
변경 없음. 상세는 `iocs/needs-review.txt` 참고.

## JARM 헌팅 신호 (차단 용도 아님)
변경 없음 (2개). 상세는 `iocs/jarm.txt` 참고.

## 워터마크 · 맬리어블 프로파일
변경 없음 (신규 IOC 없음). 이번 실행의 11개 출처 도달성 재확인 결과를 `iocs/watermarks-and-profiles.md`에 기록.

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
- 기타: 지시사항이 지정한 8개 핵심 출처(gurucul, silentpush, hunt.io, unit42 ×2, gbhackers, netlas, securelist) 및 threatfox.abuse.ch에 WebFetch를 시도했으나 전부 DNS 미해결로 차단. 추가로 지시사항이 "미시도(untested)"로 분류한 recordedfuture.com, thedfirreport.com, group-ib.com도 이번 실행에서 처음 시도했으나 역시 전부 DNS 미해결 — 도달 가능 출처 목록에 추가되지 않음(강조할 변경 없음). `iocs/watermarks-and-profiles.md`에 이번 실행의 출처 도달성 확인 결과를 기록.

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
- [Microsoft Security Blog — index](https://www.microsoft.com/en-us/security/blog/) — 2026-10-24 — fetched (목록 페이지, Cobalt Strike 관련 신규 게시물 없음)
- [Google Cloud Threat Intelligence — blog index](https://cloud.google.com/blog/topics/threat-intelligence) — 2026-10-24 — fetched (목록 페이지, Cobalt Strike 관련 신규 게시물 없음)
- [Gurucul — StrikeShark](https://community.gurucul.com/articles/ThreatResearch/StrikeShark-Investigating-a-New-25-6-2026) — blocked (DNS 미해결)
- [Silent Push — The Gentlemen](https://www.silentpush.com/blog/gentlemen-ransomware/) — blocked (DNS 미해결)
- [Hunt.io — Rare Watermark Links Cobalt Strike 4.10 Team Servers](https://hunt.io/blog/rare-watermark-links-cobalt-strike-team-servers-to-ongoing-suspicious-activity) — blocked (DNS 미해결)
- [Unit42 — Cobalt Strike Team Server](https://unit42.paloaltonetworks.com/cobalt-strike-team-server/) — blocked (DNS 미해결)
- [Unit42 — Cobalt Strike Malleable C2](https://unit42.paloaltonetworks.com/cobalt-strike-malleable-c2/) — blocked (DNS 미해결)
- [GBHackers — Nitrogen Ransomware](https://gbhackers.com/nitrogen-ransomware-uses-cobalt-strike-and-log-wiping/) — blocked (DNS 미해결)
- [Netlas.io — RST Cloud C2 Hunting](https://netlas.io/blog/с2_hunting_by_rst_cloud/) — blocked (DNS 미해결)
- [Securelist — StrikeShark](https://securelist.com/strikeshark-cobalt-strike-campaign/) — blocked (DNS 미해결)
- [ThreatFox IOC](https://threatfox.abuse.ch/ioc/1824628/) — blocked (DNS 미해결)
- [Recorded Future — Cobalt Strike C2](https://www.recordedfuture.com/research/cobalt-strike-c2) — blocked (DNS 미해결, 신규 시도)
- [The DFIR Report — search](https://thedfirreport.com/?s=cobalt+strike) — blocked (DNS 미해결, 신규 시도)
- [Group-IB — blog](https://www.group-ib.com/blog/) — blocked (DNS 미해결, 신규 시도)
- 이전 실행에서 기록된 모든 출처는 `iocs/watermarks-and-profiles.md` 참고 (중복 재검색만 수행, 신규 출처 없음)
