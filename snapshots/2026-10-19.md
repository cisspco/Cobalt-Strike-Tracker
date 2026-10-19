# Cobalt Strike Snapshot — 2026-10-19 UTC

## 수집 상태
- 페치 성공: cloud.google.com/blog/products/identity-security/making-cobalt-strike-harder-for-threat-actors-to-abuse (2022-11-18 게시물 재확인 — YARA 규칙/VT Collection 소개, 신규 IOC·캠페인 없음)
- 페치 차단: unit42.paloaltonetworks.com, www.recordedfuture.com, thedfirreport.com, www.silentpush.com, hunt.io, www.group-ib.com, threatfox.abuse.ch (전부 DNS 미해결 — egress 차단, 기존 실행들과 동일한 차단 목록 + 오늘 추가 시도한 silentpush.com/hunt.io/threatfox.abuse.ch도 차단 확인)
- 검증: 0 (신규) / 미검증: 0 (신규 호스트 없음) / 검토 필요: 0 (신규 없음)

이번 실행의 WebSearch 6개 쿼리 결과는 전부 기존에 추적 중인 캠페인/지표의 재언급이었음(StrikeShark/SharkLoader — 도메인 connect-microsoft.com/ms-record.com/ms-record.top/ms-tray.top/harivo.vip 전부 기존 `iocs/unverified-domains.txt`에 이미 기록됨; The Gentlemen/CountLoader 랜섬웨어 제휴 — 워터마크 1473793097/1357776117 기존 `iocs/watermarks-and-profiles.md`에 이미 기록됨; Ghostwriter APT 지오펜싱 PDF 캠페인 — 기존 기록됨; ThreatFox 개별 C2 엔트리 107.174.14.102·47.103.214.7·206.119.178.109 — 모두 이미 `iocs/needs-review.txt`에 기록됨; watermark 987654321 클러스터; OrangeCon 2026 ML 탐지 발표; RST Cloud JARM 헌팅 방법론). "미검증" 상태의 "검증"으로의 승격 없음. 신규 공격자 귀속 C2, 신규 해시, 신규 검토 대상 없음.

site: 검색으로 microsoft.com 및 cloud.google.com에 추가 질의했으나 2026년 신규 Cobalt Strike 전용 게시물 없음. 추가로 silentpush.com(Gentlemen 랜섬웨어 원문), hunt.io(희귀 워터마크 리포트 원문), group-ib.com, threatfox.abuse.ch 직접 fetch를 시도했으나 전부 DNS 미해결로 차단됨 — 기존에 스니펫으로만 확인된 항목들을 검증 상태로 승격시키지 못함.

조용한 하루(quiet day) — 7연속 (2026-10-13 ~ 10-18에 이어).

## 최근 캠페인 (최근 60일)

신규 캠페인 보고 없음. 기존 추적 중인 캠페인(StrikeShark/SharkLoader, The Gentlemen, Ghostwriter APT, Nitrogen ransomware)에 대한 추가 세부 정보도 금일 검색에서는 발견되지 않음(기존 보고의 재인덱싱만 확인).

## 공격자 C2 팀서버 (차단 대상) (6)
변경 없음 — 기존 6개 IP 유지. 상세는 `iocs/ips.txt` 및 `iocs/needs-review.txt` 참고.

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
- 기타: silentpush.com, hunt.io, group-ib.com, threatfox.abuse.ch 직접 fetch 시도 — 전부 DNS 미해결로 차단 확인 (이번 실행에서 처음 시도). cloud.google.com 게시물 재확인, 신규 내용 없음.

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
- [Google Cloud — Making Cobalt Strike Harder for Threat Actors to Abuse](https://cloud.google.com/blog/products/identity-security/making-cobalt-strike-harder-for-threat-actors-to-abuse) — 2026-10-19 — fetched (2022-11-18 원문; YARA 규칙/VT Collection 배경, 신규 IOC 없음)
- [Unit 42 — Cobalt Strike Team Server](https://unit42.paloaltonetworks.com/cobalt-strike-team-server/) — 2026-10-19 — blocked (DNS 미해결)
- [Recorded Future — A Multi-Method Approach to Identifying Rogue Cobalt Strike Servers](https://www.recordedfuture.com/research/cobalt-strike-servers) — 2026-10-19 — blocked (DNS 미해결)
- [The DFIR Report — Cobalt Strike category](https://thedfirreport.com/category/cobaltstrike) — 2026-10-19 — blocked (DNS 미해결)
- [Silent Push — No Place to Hide: The Gentlemen](https://www.silentpush.com/blog/gentlemen-ransomware/) — 2026-10-19 — blocked (DNS 미해결)
- [Hunt.io — Rare Watermark Links Cobalt Strike Team Servers](https://hunt.io/blog/rare-watermark-links-cobalt-strike-team-servers-to-ongoing-suspicious-activity) — 2026-10-19 — blocked (DNS 미해결)
- [Group-IB Media Center](https://www.group-ib.com/media-center/press-releases/gib-cobalt-activity/) — 2026-10-19 — blocked (DNS 미해결)
- [ThreatFox IOC 1892469](https://threatfox.abuse.ch/ioc/1892469/json/) — 2026-10-19 — blocked (DNS 미해결)
- 이전 실행에서 기록된 모든 출처는 `iocs/watermarks-and-profiles.md` 참고 (중복 재검색만 수행, 신규 출처 없음)
