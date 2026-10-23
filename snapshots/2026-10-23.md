# Cobalt Strike Snapshot — 2026-10-23 UTC

## 수집 상태
- 페치 성공: cloud.google.com/blog/topics/threat-intelligence (목록 페이지, 최근 게시물 확인), microsoft.com/en-us/security/blog (목록 페이지, 최근 게시물 확인), cloud.google.com/blog/topics/threat-intelligence/unc6671-targets-financial-services-and-enterprise-cloud-environments (2026-08-06, UNC6671 비싱/AiTM — Cobalt Strike 무관), cloud.google.com/blog/topics/threat-intelligence/shinyhunters-renewed-mass-exploitation-campaign-targeting-oracle-peoplesoft (2026-09-25, SIDEEYE 백도어 — Cobalt Strike 무관), cloud.google.com/blog/topics/threat-intelligence/distinct-clusters-target-individuals-of-interest-to-russia (2026-08-20, VIDAR/ATOMIC/ENGINELIGHT/CHERRYPIE — Cobalt Strike 무관), cloud.google.com/blog/topics/threat-intelligence/investigating-ephemeral-supply-chain-tampering (2026-10-15, SHINYROAD/Adaptix C2 — Cobalt Strike 무관)
- 페치 차단: www.recordedfuture.com (DNS 미해결, RedNovember 원문 재시도)
- 검증: 0 (신규) / 미검증: 0 (신규 호스트 없음) / 검토 필요: 0 (신규 없음)

이번 실행의 WebSearch 6개 쿼리 결과는 전부 기존에 추적 중인 캠페인/지표의 재언급이었음: StrikeShark/SharkLoader(기존 기록됨), The Gentlemen/CountLoader 워터마크 1473793097/1357776117(기존 기록됨), Nitrogen ransomware 워터마크 678358251(기존 기록됨), KnowledgeDeliver/CVE-2026-5426(기존 기록됨), ThreatFox 개별 C2 엔트리(107.174.14.102:443, 47.103.214.7:18443, 206.119.178.109:18443 — 전부 `iocs/needs-review.txt`에 이미 있음), watermark 987654321/666666666 클러스터(기존 기록됨), hunt.io "Rare Watermark" 기사(기존 기록됨), OrangeCon 2026 ML 탐지 발표(기존 기록됨), Operation Morpheus 법집행 조치(기존 기록됨, 배경 정보).

cloud.google.com Threat Intelligence 블로그에서 최근 게시물 4건(UNC6671, ShinyHunters/Oracle PeopleSoft, Russia 표적 클러스터, Ephemeral Supply Chain Tampering/SHINYROAD·Adaptix C2)을 원문까지 전체 텍스트 검색했으나 전부 Cobalt Strike를 전혀 언급하지 않음 — 각각 AiTM 비싱, SIDEEYE 커스텀 백도어, VIDAR/ATOMIC/ENGINELIGHT/CHERRYPIE 인포스틸러, SHINYROAD/Adaptix C2(별개의 C2 프레임워크)만 확인됨. 둘 다 Cobalt Strike 관련 IOC로 기록하지 않음. microsoft.com 보안 블로그 목록도 확인했으나 Cobalt Strike·랜섬웨어 전구체·악성 C2 관련 신규 게시물 없음(10월 게시물은 피싱 인프라, AI 공급망 공격, 포스트퀀텀 인증 등).

recordedfuture.com(RedNovember 원문)에 재시도했으나 이번에도 DNS 미해결로 차단됨 — 기존 기록된 미검증 상태 유지.

11일 연속 조용한 하루(quiet day) — 2026-10-13 ~ 10-22에 이어.

## 최근 캠페인 (최근 60일)

신규 캠페인 보고 없음. 기존 추적 중인 캠페인(StrikeShark/SharkLoader, The Gentlemen, Ghostwriter APT, Nitrogen ransomware, RedNovember)에 대한 추가 세부 정보도 금일 검색에서는 발견되지 않음 — 전부 기존 보고의 재인덱싱. 금일 새로 원문까지 확인한 4건(UNC6671, ShinyHunters, Russia 표적 클러스터, Ephemeral Supply Chain Tampering)은 Cobalt Strike가 구성요소로 확인되지 않아 이 섹션에 포함하지 않음.

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
- 기타: cloud.google.com Threat Intelligence 블로그 최신 게시물 4건(UNC6671/비싱, ShinyHunters/Oracle PeopleSoft, Russia 표적 클러스터, Ephemeral Supply Chain Tampering) 원문 확인 — 전부 Cobalt Strike 무관으로 확인되어 기록 제외. recordedfuture.com(RedNovember) 재시도 — 여전히 DNS 미해결로 차단.

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
- [Google Cloud Threat Intelligence — blog index](https://cloud.google.com/blog/topics/threat-intelligence) — 2026-10-23 — fetched (목록 페이지, 최근 게시물 확인)
- [Google Cloud — UNC6671 Rebrands: Multi-Brand Vishing Extortion](https://cloud.google.com/blog/topics/threat-intelligence/unc6671-targets-financial-services-and-enterprise-cloud-environments) — 2026-08-06 — fetched (Cobalt Strike 무관, AiTM/비싱)
- [Google Cloud — ShinyHunters Renewed Mass Exploitation Campaign Targeting Oracle PeopleSoft](https://cloud.google.com/blog/topics/threat-intelligence/shinyhunters-renewed-mass-exploitation-campaign-targeting-oracle-peoplesoft) — 2026-09-25 — fetched (Cobalt Strike 무관, SIDEEYE 백도어)
- [Google Cloud — Going with the Flow(s): Distinct Clusters Target Individuals of Interest to Russia](https://cloud.google.com/blog/topics/threat-intelligence/distinct-clusters-target-individuals-of-interest-to-russia) — 2026-08-20 — fetched (Cobalt Strike 무관, VIDAR/ATOMIC/ENGINELIGHT/CHERRYPIE)
- [Google Cloud — Investigating Ephemeral Supply Chain Tampering](https://cloud.google.com/blog/topics/threat-intelligence/investigating-ephemeral-supply-chain-tampering) — 2026-10-15 — fetched (Cobalt Strike 무관, SHINYROAD/Adaptix C2)
- [Microsoft Security Blog — index](https://www.microsoft.com/en-us/security/blog/) — 2026-10-23 — fetched (목록 페이지, Cobalt Strike 관련 신규 게시물 없음)
- [Recorded Future — RedNovember research](https://www.recordedfuture.com/research/rednovember-targets-government-defense-and-technology-organizations) — 2026-10-23 — blocked (DNS 미해결)
- 이전 실행에서 기록된 모든 출처는 `iocs/watermarks-and-profiles.md` 참고 (중복 재검색만 수행, 신규 출처 없음)
