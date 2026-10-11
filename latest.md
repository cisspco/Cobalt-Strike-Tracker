# Cobalt Strike Snapshot — 2026-10-11 UTC

## 수집 상태
- 페치 성공: [cloud.google.com/Mandiant — Threat Intelligence 블로그 목록](https://cloud.google.com/blog/topics/threat-intelligence) (2026-10 최신 게시글 11건 확인 — AI 위협 행위자, ShinyHunters/Oracle PeopleSoft, Citrix NetScaler, CI/CD, BREEZE COMET, UNC6671 비싱, 공급망 등; 목록 발췌문에는 Cobalt Strike 언급 없음, 전문 미확인), [microsoft.com — Security 블로그 목록](https://www.microsoft.com/en-us/security/blog/) (2026-09-29/30 게시글까지 확인 — RMM 악용 피싱, Zimbra CVE-2026-73570; Cobalt Strike 언급 없음)
- 페치 차단 (DNS 조회 실패): hunt.io (`/blog/guide-hunting-cobalt-strike-part-4-c2-feeds-api`), silentpush.com, community.gurucul.com, threatfox.abuse.ch (2개 IOC), netlas.io — 6건 전부 DNS 단계에서 차단 재확인
- 검증: 0 (신규) / 미검증: 0 (신규, 호스트 기준) / 검토 필요: 31 (총계, 신규 0)

조용한 하루였습니다 — 신규 공격자 C2(차단 대상), 신규 캠페인, 신규 해시는 발견되지 않았습니다. WebSearch 6개 쿼리 결과는 모두 이미 이 트래커에 기록된 기존 항목(StrikeShark/SharkLoader, The Gentlemen/CountLoader, Nitrogen 랜섬웨어, 워터마크 987654321/666666666/678358251, Operation Morpheus)의 재확인이었으며 2026-10 신규 보도는 확인되지 않았습니다. 접근 가능한 cloud.google.com(Mandiant/GTIG, 2026-10 최신 11건)과 microsoft.com(2026-09 말) 블로그 목록을 재확인했으나 목록 발췌문 기준으로 Cobalt Strike를 다루는 신규 게시글은 없었습니다. hunt.io, silentpush.com, community.gurucul.com, threatfox.abuse.ch, netlas.io 등 과거에도 반복적으로 DNS 차단되었던 5개 소스를 이번에도 재시도했으나 전부 동일하게 차단되어, 이 레포가 장기적으로 기댈 수 있는 신규 소스는 아님을 다시 확인했습니다.

## 최근 캠페인 (최근 60일) — 변경 없음, 기존 캠페인 참고용 재게시

### "The Gentlemen" 랜섬웨어 제휴자 — CountLoader + Cobalt Strike ⚠️ (미검증)
- 대상: 불특정 (LockBit·Black Basta·Qilin 제휴자 활동 추적)
- 초기 침투: CountLoader 경유
- Cobalt Strike 역할: CountLoader가 전달하는 2차 페이로드, 워터마크 1473793097 / 1357776117 사용
- 관측 시점: 2026-02 (Silent Push 보고서)
- 출처: silentpush.com (이번 실행에서도 fetch 차단, 검색 스니펫만 확인)

### Nitrogen 랜섬웨어 — Cobalt Strike + 로그 와이핑 ⚠️ (미검증)
- 대상: 불특정
- 초기 침투: 가짜 WinSCP 설치파일(악성 광고 유포 추정) 또는 불명
- Cobalt Strike 역할: 측면 이동/지속성 확보, 워터마크 678358251 사용 가능성 (BlackCat 랜섬웨어로 종결)
- 관측 시점: 2026-09 (2026-09-15 보도)
- 출처: gbhackers.com (변경 없음, 이번 실행에서 재시도하지 않음)

### StrikeShark / SharkLoader — Cobalt Strike Beacon 로더 ⚠️ (미검증) — 변경 없음
- 출처: community.gurucul.com (이번 실행에서도 fetch 차단 — DNS 조회 실패), securelist.com (fetch 차단, 알려진 차단 도메인) — 60일 범위 밖(참고용)

## 공격자 C2 팀서버 (차단 대상) (6) — 변경 없음
- 108.61.242.65 — UNC2628/DarkSide Cobalt Strike BEACON C2 (Mandiant/Google Cloud Blog) — verified
- 109.206.243.59 — UNC2628/DarkSide Cobalt Strike BEACON C2 (Mandiant/Google Cloud Blog) — verified
- 146.70.78.43 — UNC2628/DarkSide Cobalt Strike BEACON C2 (Mandiant/Google Cloud Blog) — verified
- 45.150.108.213 — UNC2628/DarkSide Cobalt Strike BEACON C2 (Mandiant/Google Cloud Blog) — verified
- 87.120.254.39 — UNC2628/DarkSide Cobalt Strike BEACON C2 (Mandiant/Google Cloud Blog) — verified
- 92.204.160.240 — UNC2628/DarkSide Cobalt Strike BEACON C2 (Mandiant/Google Cloud Blog) — verified
- (도메인 없음 — `iocs/domains.txt`는 현재 공백)

## 검토 필요 — 스캐너 탐지만 된 팀서버 (차단 금지) (31) — 변경 없음
전체 목록은 `iocs/needs-review.txt` 참고. 이번 실행에서 신규 추가 없음.

## JARM 헌팅 신호 (차단 용도 아님) (2) — 변경 없음
- 07d14d16d21d21d00042d41d00041de5fb3038104f457d92ba02e9311512c2 — Cobalt Strike 기본 팀서버(OpenJDK 11) — 일반 헌팅 신호, 캠페인 특정 아님 — unverified
- 07d14d16d21d21d07c42d41d00041d24a458a375eef0c576d23a7bab9a9fb1 — 위 값의 대체 보고치(Java 11 SSL 스택) — unverified

## 워터마크 · 맬리어블 프로파일 — 변경 없음
전체 내역은 `iocs/watermarks-and-profiles.md` 참고. 이번 실행에서 신규 추가 없음.

## 파일 해시 (2) — 변경 없음
### SHA-256
- 5f37b85687780c089607670040dbb3da2749b91b8adc0aa411fd6280b5fa7103 — beacon — BlackByte ransomware intrusion (ProxyShell Exchange exploitation) — verified
- 7c1f99dca8e5a7897892f9d224a6495023a2cfd2671697d229d355978c415ed2 — loader — KnowledgeDeliver/CVE-2026-5426 — verified

## 호스트 IOC · 행위 — 변경 없음
- `\\.\pipe\UIA_PIPE_*` (UNC2628/DarkSide SMB BEACON named pipe 패턴)
- Windows 서비스명 `CitrixInit`, 도메인 계정 `spservice` (UNC2628/DarkSide persistence)

## 이번 실행 변경사항
- 신규 C2: 없음
- 신규 해시: 없음
- 승격(미검증→검증): 없음
- 분류 변경: 없음
- 검토 필요 신규 추가: 없음
- 워터마크/프로파일 보강: 없음
- 메타: hunt.io, silentpush.com, community.gurucul.com, threatfox.abuse.ch, netlas.io — 5개 소스 재시도, 전부 DNS 조회 실패로 차단 재확인. cloud.google.com(2026-10 최신 11건 목록) 및 microsoft.com(2026-09 말) 블로그 목록은 접근 가능했으나 발췌문 기준 Cobalt Strike 신규 언급 없음.

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
- [Threat Intelligence blog listing (Google Cloud / Mandiant)](https://cloud.google.com/blog/topics/threat-intelligence) — 2026-10 (최신 목록, 11건) — fetched (no CS content in excerpts)
- [Microsoft Security Blog listing](https://www.microsoft.com/en-us/security/blog/) — 2026-09-30 (최신 목록) — fetched (no CS content)
- [The Complete Guide to Hunting Cobalt Strike – Part 4 (hunt.io)](https://hunt.io/blog/guide-hunting-cobalt-strike-part-4-c2-feeds-api) — undated — blocked (DNS)
- [No Place to Hide: Following a Serial Ransomware Affiliate... to The Gentlemen (Silent Push)](https://www.silentpush.com/blog/gentlemen-ransomware/) — undated — blocked (DNS)
- [StrikeShark: Investigating a New Campaign Delivering Cobalt Strike Through SharkLoader (Gurucul)](https://community.gurucul.com/articles/ThreatResearch/StrikeShark-Investigating-a-New-25-6-2026) — 2026-06-25 — blocked (DNS)
- [ThreatFox IOC 1795514](https://threatfox.abuse.ch/ioc/1795514/) — n/a — blocked (DNS)
- [ThreatFox IOC 1824628](https://threatfox.abuse.ch/ioc/1824628/) — n/a — blocked (DNS)
- [How we hunt C2 infrastructure at RST Cloud using Netlas](https://netlas.io/blog/с2_hunting_by_rst_cloud/) — 2026-03 — blocked (DNS)
