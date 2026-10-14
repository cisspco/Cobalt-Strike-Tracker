# Cobalt Strike Snapshot — 2026-10-14 UTC

## 수집 상태
- 페치 성공: 없음
- 페치 차단: community.gurucul.com, www.silentpush.com, hunt.io, dailysecurityreview.com, unit42.paloaltonetworks.com, threatfox.abuse.ch, recordedfuture.com, www.thedfirreport.com, www.group-ib.com (egress proxy DNS 차단, 9개 모두 시도)
- 참고: microsoft.com/security/blog, cloud.google.com/blog/topics/threat-intelligence 페치는 성공했으나 신규 Cobalt Strike 관련 게시물 없음
- 검증: 0 / 미검증: 0 (신규 없음, 기존 누적 데이터와 전부 중복) / 검토 필요: 0 (신규 없음)

이번 실행의 WebSearch 결과(StrikeShark/Gurucul, Silent Push "The Gentlemen", hunt.io 워터마크 기사, ESET Ghostwriter, ThreatFox 항목들)는 모두 기존 `iocs/watermarks-and-profiles.md` 및 `iocs/needs-review.txt`에 이미 기록된 동일 캠페인/인프라에 대한 재언급이었음. 신규 공격자 귀속 C2, 신규 해시, 신규 검토 대상 없음 — 조용한 하루(quiet day).

## 최근 캠페인 (최근 60일)

신규 캠페인 보고 없음. 기존 추적 중인 캠페인(StrikeShark/SharkLoader, The Gentlemen, Ghostwriter APT, Nitrogen ransomware)에 대한 추가 세부 정보는 금일 검색에서 발견되지 않음 — 모두 `iocs/watermarks-and-profiles.md`에 이미 기록된 내용과 동일.

## 공격자 C2 팀서버 (차단 대상) (6)
변경 없음 — 기존 6개 IP (UNC2628/DarkSide, Mandiant/Google Cloud Blog 귀속, 2021년 보고, ~5년 경과 가능성 높음) 유지. 상세는 `iocs/ips.txt` 및 `iocs/needs-review.txt` 참고.

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
- 금일 WebFetch 시도 전부 실패 (DNS 차단): community.gurucul.com, www.silentpush.com, hunt.io, dailysecurityreview.com, unit42.paloaltonetworks.com, threatfox.abuse.ch, recordedfuture.com, www.thedfirreport.com, www.group-ib.com
- [Microsoft Security Blog 검색](https://www.microsoft.com/en-us/security/blog/?s=cobalt+strike) — 2026-10-14 — fetched (신규 CS 게시물 없음)
- [Google Cloud Threat Intelligence Blog](https://cloud.google.com/blog/topics/threat-intelligence) — 2026-10-14 — fetched (신규 CS 게시물 없음)
- 이전 실행에서 기록된 모든 출처는 `iocs/watermarks-and-profiles.md` 참고 (중복 재검색만 수행, 신규 출처 없음)
