# Cobalt Strike Snapshot — 2026-11-02 UTC

## 수집 상태
- 페치 성공: cloud.google.com/blog/topics/threat-intelligence (최신 게시물 목록 확인, Cobalt Strike 관련 신규 콘텐츠 없음)
- 페치 차단: unit42.paloaltonetworks.com (malleable-C2 원문 + team-server 원문, DNS 미해결, 2건), recordedfuture.com (RedNovember 원문, DNS 미해결 — 최초로 확정 차단 확인), thedfirreport.com (DNS 미해결 — 최초로 확정 차단 확인), silentpush.com (The Gentlemen 원문, DNS 미해결), threatfox.abuse.ch (IOC JSON, DNS 미해결), group-ib.com (DNS 미해결 — 최초로 확정 차단 확인)
- 검증: 0 (신규) / 미검증: 0 (신규 호스트 없음) / 검토 필요: 2 (신규 스캐너 피드 탐지)

**참고**: 이 저장소의 직전 스냅샷은 2026-10-25로 기록되어 있으며 2026-10-26~2026-11-01 사이의 스냅샷이 존재하지 않음 — 해당 기간 동안 예약 작업이 실행되지 않았거나 커밋되지 않은 것으로 보임. 이번 실행은 그 공백을 보충하는 것이 아니라 2026-11-02 당일의 검색/페치 결과만 반영함.

이번 실행은 지시사항의 6개 WebSearch 쿼리를 모두 수행했음. 결과는 대부분 기존에 추적 중인 캠페인·지표의 재언급이었음: StrikeShark/SharkLoader(기존 기록됨), The Gentlemen/CountLoader(기존 기록됨), 워터마크 987654321 클러스터(기존 기록됨), RedNovember/Pantegana(기존 기록됨), Ghostwriter APT(기존 기록됨), OrangeCon 2026 ML 탐지 발표(기존 기록됨). 지시사항이 제안한 미시험 출처 3곳(recordedfuture.com, thedfirreport.com, group-ib.com)을 이번 실행에서 직접 재시도했고 전부 DNS 미해결로 확인되어 "차단됨" 목록에 확정 추가함. unit42.paloaltonetworks.com도 2개 URL 모두 재시도했으나 DNS 미해결. cloud.google.com만 재확인용으로 성공했으나 Cobalt Strike 관련 신규 콘텐츠는 없었음(제목에서 추측한 "ARTEX and Friends" 슬러그는 404).

금일 신규 사항: WebSearch 스니펫에서 기존에 기록되지 않은 스캐너 전용 탐지 2건을 발견 — IP 111.228.62.67:80 (ThreatFox, Alibaba 호스팅, 고신뢰도 피드 태그, 캠페인 귀속 없음), 도메인 status.jarredlike.xyz (ANY.RUN 피드, 최종 관측 2026-06-09, 캠페인 귀속 없음). 둘 다 특정 캠페인·행위자 귀속 없이 자동 피드 분류만 존재하여 `iocs/needs-review.txt`에 추가(차단 금지, 스캐너 탐지만 된 항목).

캠페인 수준 신규 보고는 없음 — 조용한 하루(quiet day)가 계속됨.

## 최근 캠페인 (최근 60일)

신규 캠페인 보고 없음. 기존 추적 중인 캠페인(StrikeShark/SharkLoader, The Gentlemen, Ghostwriter APT, Nitrogen ransomware, RedNovember)에 대한 추가 세부 정보도 금일 검색에서는 발견되지 않음 — 전부 기존 보고의 재인덱싱.

## 공격자 C2 팀서버 (차단 대상) (6)
변경 없음 — 기존 6개 IP 유지. 상세는 `iocs/ips.txt` 참고. (도메인 0건, `iocs/domains.txt` 참고)

## 검토 필요 — 스캐너 탐지만 된 팀서버 (차단 금지) (38)
- 111.228.62.67 — ThreatFox 태그 "Cobalt Strike" C2(포트 80), Alibaba 호스팅, 고신뢰도 피드 태그, 캠페인/행위자 귀속 없음 — ⚠️ (미검증)
- status.jarredlike.xyz — ANY.RUN 피드 "Cobalt Strike" 태그, 최종 관측 2026-06-09, 캠페인/행위자 귀속 없음 — ⚠️ (미검증)
- (기존 36건 변경 없음, 상세는 `iocs/needs-review.txt` 참고)

## JARM 헌팅 신호 (차단 용도 아님)
변경 없음 (2개). 상세는 `iocs/jarm.txt` 참고.

## 워터마크 · 맬리어블 프로파일
변경 없음 — 전체 내역은 `iocs/watermarks-and-profiles.md` 참고 (이번 실행 재확인 로그 추가됨, recordedfuture.com/thedfirreport.com/group-ib.com 차단 확정).

## 파일 해시 (2)
변경 없음. 상세는 `iocs/sha256.txt` 참고.

## 호스트 IOC · 행위
- UNC4393/BASTA DNS BEACON 서브호스트 네이밍 패턴 (`h.dns.<C2>`, `ridoj4.<8char>.dns.<C2>` 등) — 기존 기록, 변경 없음.
- UNC2628/DarkSide — Slack API를 통한 C3-over-Slack BEACON 프록싱, SMB named pipe `\\.\pipe\UIA_PIPE_*` — 기존 기록, 변경 없음.

## 이번 실행 변경사항
- 신규 C2: 없음 (block-safe 기준)
- 신규 해시: 없음
- 승격(미검증→검증): 없음
- 분류 변경: 없음
- 검토 필요 신규 추가: 111.228.62.67, status.jarredlike.xyz (스캐너/피드 탐지, 캠페인 귀속 없음)

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
- [Google Cloud Blog — Threat Intelligence](https://cloud.google.com/blog/topics/threat-intelligence) — 확인일 2026-11-02 — fetched (최신 목록 확인, Cobalt Strike 관련 신규 콘텐츠 없음)
- [Unit42 — Cobalt Strike Malleable C2](https://unit42.paloaltonetworks.com/cobalt-strike-malleable-c2/) — blocked (DNS 미해결)
- [Unit42 — Cobalt Strike Team Server](https://unit42.paloaltonetworks.com/cobalt-strike-team-server/) — blocked (DNS 미해결)
- [Recorded Future — RedNovember](https://www.recordedfuture.com/research/rednovember-targets-government-defense-and-technology-organizations) — blocked (DNS 미해결, 확정)
- [The DFIR Report](https://thedfirreport.com) — blocked (DNS 미해결, 확정)
- [Silent Push — The Gentlemen Ransomware](https://www.silentpush.com/blog/gentlemen-ransomware/) — blocked (DNS 미해결)
- [Group-IB Blog](https://group-ib.com/blog/) — blocked (DNS 미해결, 확정)
- ThreatFox IOC Database (abuse.ch) — WebSearch 스니펫만 확인, 원문 페이지 fetch 차단 — 111.228.62.67:80 신규 확인
- ANY.RUN Malware Trends — WebSearch 스니펫만 확인 — status.jarredlike.xyz 신규 확인
- 이전 실행에서 기록된 모든 출처는 `iocs/watermarks-and-profiles.md` 참고
