# Cobalt Strike Snapshot — 2026-10-18 UTC

## 수집 상태
- 페치 성공: cloud.google.com/blog/products/identity-security/making-cobalt-strike-harder-for-threat-actors-to-abuse (2022-11-18 게시물, CS JAR 버전 식별용 YARA 규칙/VT Collection 소개 — 신규 IOC/캠페인 없음, 이미 알려진 배경 정보)
- 페치 차단: unit42.paloaltonetworks.com, netlas.io, www.recordedfuture.com, thedfirreport.com, www.group-ib.com (전부 DNS 미해결 — egress 차단, 기존 실행들과 동일한 차단 목록)
- 검증: 0 (신규) / 미검증: 0 (신규 호스트 없음) / 검토 필요: 0 (신규 없음)

이번 실행의 WebSearch 6개 쿼리 결과는 전부 기존에 추적 중인 캠페인/지표의 재언급이었음(StrikeShark/SharkLoader, The Gentlemen, watermark 987654321/666666666 클러스터, ThreatFox 개별 C2 엔트리 107.174.14.102·47.103.214.7·206.119.178.109 — 모두 이미 `iocs/needs-review.txt`에 기록됨, OrangeCon 2026 ML 탐지 발표, RST Cloud/Netlas JARM 방법론). "미검증" 상태의 "검증"으로의 승격 없음. 신규 공격자 귀속 C2, 신규 해시, 신규 검토 대상 없음.

site: 검색으로 microsoft.com 및 cloud.google.com에 추가로 질의했으나 2026년 신규 Cobalt Strike 전용 게시물은 발견되지 않음 — 2022-11-18 Google Cloud 게시물("Making Cobalt Strike Harder for Threat Actors to Abuse")만 신규로 직접 fetch하여 확인, 내용은 YARA 규칙/VirusTotal Collection 배경 설명으로 구체 IOC·캠페인 없음.

조용한 하루(quiet day) — 6연속 (2026-10-13 ~ 10-17에 이어).

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
- 기타: Google Cloud "Making Cobalt Strike Harder for Threat Actors to Abuse" (2022-11-18) 전문 확인 — CS 버전 식별용 YARA/VT Collection 배경 설명, 신규 IOC 없음(IOC 미채택).

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
- [Google Cloud — Making Cobalt Strike Harder for Threat Actors to Abuse](https://cloud.google.com/blog/products/identity-security/making-cobalt-strike-harder-for-threat-actors-to-abuse) — 2026-10-18 — fetched (2022-11-18 원문; YARA 규칙/VT Collection 배경, 신규 IOC 없음)
- [Unit 42 — Cobalt Strike Malleable C2](https://unit42.paloaltonetworks.com/cobalt-strike-malleable-c2/) — 2026-10-18 — blocked (DNS 미해결)
- [Netlas.io — RST Cloud JARM Hunting](https://netlas.io/blog/%D1%812_hunting_by_rst_cloud/) — 2026-10-18 — blocked (DNS 미해결)
- [Recorded Future — RedNovember](https://www.recordedfuture.com/research/rednovember-targets-government-defense-and-technology-organizations) — 2026-10-18 — blocked (DNS 미해결)
- [The DFIR Report](https://thedfirreport.com/) — 2026-10-18 — blocked (DNS 미해결)
- [Group-IB Blog](https://www.group-ib.com/blog/) — 2026-10-18 — blocked (DNS 미해결)
- 이전 실행에서 기록된 모든 출처는 `iocs/watermarks-and-profiles.md` 참고 (중복 재검색만 수행, 신규 출처 없음)
