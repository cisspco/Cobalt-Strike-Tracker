# Cobalt Strike Snapshot — 2026-10-17 UTC

## 수집 상태
- 페치 성공: www.microsoft.com/en-us/security/blog (검색, 신규 CS 게시물 없음), cloud.google.com/blog/topics/threat-intelligence (목록), cloud.google.com/.../armory-castle-exploits-beyondtrust (CS 언급 없음), cloud.google.com/.../financially-motivated-threat-actor-breeze-comet-targets-brazil (CS 언급 없음), cloud.google.com/.../defending-against-active-exploitation-of-citrix-netscaler-adc-and-gateway-appliances (CS 언급 없음)
- 페치 차단: unit42.paloaltonetworks.com, www.recordedfuture.com, www.thedfirreport.com, www.group-ib.com, threatfox.abuse.ch, threatcluster.io (전부 DNS 미해결 — egress 차단, 기존 실행들과 동일)
- 검증: 0 (신규) / 미검증: 0 (신규 호스트 없음) / 검토 필요: 0 (신규 없음)

이번 실행의 WebSearch 6개 쿼리는 모두 기존에 추적 중인 캠페인(StrikeShark/SharkLoader, The Gentlemen, Ghostwriter APT, watermark 987654321/1473793097/1357776117 클러스터, ThreatFox 개별 C2 엔트리, OrangeCon 2026 ML 탐지 발표, RST Cloud/Netlas JARM 방법론, hunt.io 집계)의 재언급이었음. "미검증" 상태의 "검증"으로의 승격 없음. 신규 공격자 귀속 C2, 신규 해시, 신규 검토 대상 없음.

Google Cloud/Mandiant 블로그에서 신규 게시물 3건(ARMORY CASTLE/BeyondTrust 제로데이, BREEZE COMET/브라질 금융권, Citrix NetScaler 제로데이 2건)을 직접 fetch하여 전문을 확인했으나, 셋 다 Cobalt Strike를 로더/비콘/C2로 사용하지 않음(각각 커스텀 툴체인 SAWFLY/BARECLAW, COBALTSPIN/REALBREEZE/MILDFROST 등, WHIPSHOT/SLAPSHOT 사용). 특히 BREEZE COMET 리포트의 "COBALTSPIN"은 이름이 유사하나 Cobalt Strike와 무관한 별도의 Rust 기반 터널러임 — 혼동 방지를 위해 기록. 이 3건은 IOC로 채택하지 않음(CS 미관련).

조용한 하루(quiet day) — 5연속 (2026-10-13 ~ 10-16에 이어).

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
- 기타: Google Cloud/Mandiant 신규 게시물 3건 전문 확인 — Cobalt Strike 무관 확인(IOC 미채택). "COBALTSPIN" 명칭 혼동 방지 노트.

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
- [Microsoft Security Blog 검색](https://www.microsoft.com/en-us/security/blog/?s=cobalt+strike) — 2026-10-17 — fetched (신규 CS 게시물 없음; 최신 CS 언급은 2021-01-20 Solorigate/TEARDROP 게시물)
- [Google Cloud Threat Intelligence Blog](https://cloud.google.com/blog/topics/threat-intelligence) — 2026-10-17 — fetched (목록만, 날짜 미표시)
- [Google Cloud — ARMORY CASTLE Exploits BeyondTrust](https://cloud.google.com/blog/topics/threat-intelligence/armory-castle-exploits-beyondtrust) — 2026-10-17 — fetched (CS 무관 확인; CVE-2026-102764, PRC-nexus 추정)
- [Google Cloud — BREEZE COMET Targets Brazil](https://cloud.google.com/blog/topics/threat-intelligence/financially-motivated-threat-actor-breeze-comet-targets-brazil) — 2026-10-17 — fetched (CS 무관 확인; "COBALTSPIN"은 별도 터널러, CS 아님)
- [Google Cloud — Citrix NetScaler ADC/Gateway Active Exploitation](https://cloud.google.com/blog/topics/threat-intelligence/defending-against-active-exploitation-of-citrix-netscaler-adc-and-gateway-appliances) — 2026-10-17 — fetched (CS 무관 확인; CVE-2026-88772/88771 제로데이)
- [Unit 42 — Cobalt Strike Team Server](https://unit42.paloaltonetworks.com/cobalt-strike-team-server/) — 2026-10-17 — blocked (DNS 미해결)
- [Recorded Future — RedNovember](https://www.recordedfuture.com/research/rednovember-targets-government-defense-and-technology-organizations) — 2026-10-17 — blocked (DNS 미해결)
- [The DFIR Report](https://www.thedfirreport.com/) — 2026-10-17 — blocked (DNS 미해결)
- [Group-IB Blog](https://www.group-ib.com/blog/) — 2026-10-17 — blocked (DNS 미해결)
- [ThreatFox (abuse.ch)](https://threatfox.abuse.ch/browse/malware/win.cobalt_strike/) — 2026-10-17 — blocked (DNS 미해결)
- [ThreatCluster — Multiple Cobalt Strike Beacons Detected on Various Ports](https://threatcluster.io/cluster/multiple-cobalt-strike-beacons-detected-on-various-ports-b03995dc) — 2026-10-17 — blocked (DNS 미해결; 검색 스니펫만, 구체 IP 미공개, 스캐너 탐지로 추정)
- 이전 실행에서 기록된 모든 출처는 `iocs/watermarks-and-profiles.md` 참고 (중복 재검색만 수행, 신규 출처 없음)
