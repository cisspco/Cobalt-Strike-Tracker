# Cobalt Strike Snapshot — 2026-10-21 UTC

## 수집 상태
- 페치 성공: cloud.google.com/blog/topics/threat-intelligence (목록 페이지, 신규 게시물 8건 확인 — 전부 Cobalt Strike 무관), cloud.google.com/blog/products/identity-security/making-cobalt-strike-harder-for-threat-actors-to-abuse (2022-11-18, Google Cloud GCTI의 165개 YARA 시그니처/크랙판 탐지 연구 — 신규 IOC 없음)
- 페치 차단: unit42.paloaltonetworks.com (team-server, malleable-c2 두 페이지 모두 DNS 미해결), www.recordedfuture.com, www.thedfirreport.com, www.group-ib.com, threatfox.abuse.ch (JSON 엔드포인트)
- 검증: 0 (신규) / 미검증: 0 (신규 호스트 없음) / 검토 필요: 0 (신규 없음)

이번 실행의 WebSearch 6개 쿼리 결과는 전부 기존에 추적 중인 캠페인/지표의 재언급이었음: StrikeShark/SharkLoader(도메인·MD5 해시 7개, 기존 `iocs/unverified-domains.txt` 및 watermarks 파일에 이미 기록됨), The Gentlemen/CountLoader(워터마크 1473793097/1357776117, 기존 기록됨), Nitrogen ransomware(워터마크 678358251, 기존 기록됨), RedNovember/LESLIELOADER(기존 기록됨), ThreatFox 개별 C2 엔트리(107.174.14.102:443, 47.103.214.7:18443, 206.119.178.109:18443 — 전부 `iocs/needs-review.txt`에 이미 있음), watermark 987654321 클러스터(기존 기록됨), OrangeCon 2026 ML 탐지 발표(기존 기록됨). Unit 42의 일반 팀서버 헌팅 방법론 관련 WebSearch 요약에서 특정 IP(23.95.44.80)와 해시가 언급되었으나, 원문 페치가 차단되어 교차검증이 불가능하고 특정 악성 캠페인 귀속도 없는 일반 연구 사례로 판단되어 — 신뢰도 부족으로 이번 실행에서는 기록하지 않음(검색엔진 AI 요약의 지표 정확성을 원문 없이 보증할 수 없음).

9일 연속 조용한 하루(quiet day) — 2026-10-13 ~ 10-20에 이어.

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
- 기타: cloud.google.com Threat Intelligence 블로그 목록에서 신규 게시물 8건(ARMORY CASTLE/BeyondTrust, 공급망 변조, AI 취약점 동향, Citrix NetScaler 악용 대응, ShinyHunters/Oracle PeopleSoft, CI/CD 하드닝, 러시아 관련 인물 표적 클러스터, Agentic 코드 리뷰) 확인 — 제목/요약 기준 전부 Cobalt Strike 무관. unit42.paloaltonetworks.com 2개 페이지(team-server, malleable-c2) 재시도 — 여전히 DNS 미해결로 차단.

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
- [Google Cloud Threat Intelligence — blog index](https://cloud.google.com/blog/topics/threat-intelligence) — 2026-10-21 — fetched (목록 페이지, Cobalt Strike 신규 게시물 없음)
- [Google Cloud — Making Cobalt Strike Harder for Threat Actors to Abuse](https://cloud.google.com/blog/products/identity-security/making-cobalt-strike-harder-for-threat-actors-to-abuse) — 2022-11-18 — fetched (GCTI YARA 연구, 신규 IOC 없음)
- [Unit 42 — Cobalt Strike Team Server](https://unit42.paloaltonetworks.com/cobalt-strike-team-server/) — 2026-10-21 — blocked (DNS 미해결)
- [Unit 42 — Cobalt Strike Malleable C2](https://unit42.paloaltonetworks.com/cobalt-strike-malleable-c2/) — 2026-10-21 — blocked (DNS 미해결)
- [Recorded Future — RedNovember](https://www.recordedfuture.com/research/rednovember-targets-government-defense-and-technology-organizations) — 2026-10-21 — blocked (DNS 미해결)
- [The DFIR Report — Cobalt Strike search](https://www.thedfirreport.com/?s=cobalt+strike) — 2026-10-21 — blocked (DNS 미해결)
- [Group-IB blog search](https://www.group-ib.com/blog/?s=cobalt+strike) — 2026-10-21 — blocked (DNS 미해결)
- [ThreatFox IOC 1892469](https://threatfox.abuse.ch/ioc/1892469/json/) — 2026-10-21 — blocked (DNS 미해결)
- 이전 실행에서 기록된 모든 출처는 `iocs/watermarks-and-profiles.md` 참고 (중복 재검색만 수행, 신규 출처 없음)
