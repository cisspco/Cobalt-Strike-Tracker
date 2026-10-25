# Cobalt Strike Snapshot — 2026-10-25 UTC

## 수집 상태
- 페치 성공: cloud.google.com/blog (Google Cloud "Making Cobalt Strike Harder for Threat Actors to Abuse", 2022년 게시물, 신규 지표 없음)
- 페치 차단: unit42.paloaltonetworks.com (team-server 원문, DNS 미해결), silentpush.com (The Gentlemen 원문, DNS 미해결), hunt.io (Rare Watermark 원문 + Hunting Guide Part 3, DNS 미해결, 2건), community.gurucul.com (StrikeShark 원문, DNS 미해결), threatbook.io (북한 연계 우즈베키스탄 캠페인 원문, DNS 미해결), netlas.io (RST Cloud JARM 헌팅 원문, DNS 미해결), dailysecurityreview.com (Ghostwriter 원문, DNS 미해결)
- 검증: 0 (신규) / 미검증: 0 (신규 호스트 없음) / 검토 필요: 2 (신규 ThreatFox 스캐너 탐지 IP)

이번 실행은 지시사항의 6개 WebSearch 쿼리를 모두 수행했음. 결과는 대부분 기존에 추적 중인 캠페인·지표의 재언급이었음: StrikeShark/SharkLoader(기존 기록됨), The Gentlemen/CountLoader 워터마크 1473793097·1357776117(기존 기록됨), 워터마크 987654321 클러스터 및 ThreatBook의 북한 연계 우즈베키스탄 캠페인 가설(기존 기록됨), Ghostwriter APT 지오펜싱 PDF 캠페인(기존 기록됨), Unit42의 team-server/malleable-C2 일반 연구(특정 캠페인·IOC 없음), JARM 피벗 헌팅 방법론(기존 기록됨). 지시사항이 지정한 8개 핵심 출처에 WebFetch를 시도했으나 전부 DNS 미해결로 차단되어 모두 미검증(unverified) 상태로 유지됨. cloud.google.com만 재확인용으로 성공했고 2022년 구 게시물 재확인에 그침(YARA 규칙/VirusTotal 컬렉션 공지, 신규 IOC 없음).

금일 신규 사항: ThreatFox 검색 결과에서 기존에 기록되지 않은 "Cobalt Strike" 태그 스캐너 탐지 IP 2건을 발견 — 107.175.206.36:8866 (최초 관측 2026-03-02), 47.92.109.107:32251 (최종 관측 2026-03-27). 둘 다 특정 캠페인·행위자 귀속 없이 ThreatFox 자동 피드 분류만 존재하여 `iocs/needs-review.txt`에 추가(차단 금지, 스캐너 탐지만 된 항목).

캠페인 수준 신규 보고는 없음 — 13일 연속 조용한 하루(quiet day), 2026-10-13 ~ 10-24에 이어.

## 최근 캠페인 (최근 60일)

신규 캠페인 보고 없음. 기존 추적 중인 캠페인(StrikeShark/SharkLoader, The Gentlemen, Ghostwriter APT, Nitrogen ransomware, RedNovember)에 대한 추가 세부 정보도 금일 검색에서는 발견되지 않음 — 전부 기존 보고의 재인덱싱.

## 공격자 C2 팀서버 (차단 대상) (6)
변경 없음 — 기존 6개 IP 유지. 상세는 `iocs/ips.txt` 참고.

## 검토 필요 — 스캐너 탐지만 된 팀서버 (차단 금지) (36)
- 107.175.206.36 — ThreatFox 태그 "Cobalt Strike" C2(포트 8866), 캠페인/행위자 귀속 없음, 스캐너/피드 분류만 — ⚠️ (미검증)
- 47.92.109.107 — ThreatFox 태그 "Cobalt Strike" C2(포트 32251), 캠페인/행위자 귀속 없음, 스캐너/피드 분류만 — ⚠️ (미검증)
- (기존 34건 변경 없음, 상세는 `iocs/needs-review.txt` 참고)

## JARM 헌팅 신호 (차단 용도 아님)
변경 없음 (2개). 상세는 `iocs/jarm.txt` 참고.

## 워터마크 · 맬리어블 프로파일
- 987654321 — ⚠️ (미검증) ThreatBook의 북한(APT37 TTP 중복) 연계 우즈베키스탄 캠페인 가설과 연결된 워터마크로 재확인됨; ThreatBook 자체도 "확정적 증거 없음"이라고 명시 — 기존 기록, 신규 정보 없음.
- 그 외 전체 내역은 `iocs/watermarks-and-profiles.md` 참고 (이번 실행 재확인 로그 추가됨).

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
- 검토 필요 신규 추가: 107.175.206.36, 47.92.109.107 (ThreatFox 스캐너 탐지, 캠페인 귀속 없음)

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
- [Google Cloud — Making Cobalt Strike Harder for Threat Actors to Abuse](https://cloud.google.com/blog/products/identity-security/making-cobalt-strike-harder-for-threat-actors-to-abuse) — 2022-11-18 — fetched (구 게시물, 신규 지표 없음)
- [Unit42 — Cobalt Strike Team Server](https://unit42.paloaltonetworks.com/cobalt-strike-team-server/) — blocked (DNS 미해결)
- [Silent Push — The Gentlemen Ransomware](https://www.silentpush.com/blog/gentlemen-ransomware/) — blocked (DNS 미해결)
- [Hunt.io — Rare Watermark Links Cobalt Strike 4.10 Team Servers](https://hunt.io/blog/rare-watermark-links-cobalt-strike-team-servers-to-ongoing-suspicious-activity) — blocked (DNS 미해결)
- [Hunt.io — Complete Guide to Hunting Cobalt Strike, Part 3](https://hunt.io/blog/guide-hunting-cobalt-strike-part-3-automated-discovery) — blocked (DNS 미해결)
- [Gurucul — StrikeShark](https://community.gurucul.com/articles/ThreatResearch/StrikeShark-Investigating-a-New-25-6-2026) — blocked (DNS 미해결)
- [ThreatBook — Suspected North Korea-linked Hackers Target Uzbekistan](https://threatbook.io/blog/suspected-north-korea-linked-hackers-conduct-targeted-attack-campaign-against-uzbekistan) — blocked (DNS 미해결)
- [Netlas.io — C2 Hunting by RST Cloud](https://netlas.io/blog/с2_hunting_by_rst_cloud/) — blocked (DNS 미해결)
- [Daily Security Review — Ghostwriter APT Geofenced Ukraine Campaign](https://dailysecurityreview.com/cyber-security/ghostwriter-apt-deploys-cobalt-strike-in-geofenced-ukraine-campaign/) — blocked (DNS 미해결)
- ThreatFox IOC Database (abuse.ch) — 다수 엔트리, WebSearch 스니펫만 확인, 원문 페이지 fetch 미시도 (알려진 차단 도메인) — 107.175.206.36:8866, 47.92.109.107:32251 신규 확인
- 이전 실행에서 기록된 모든 출처는 `iocs/watermarks-and-profiles.md` 참고
