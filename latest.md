# Cobalt Strike Snapshot — 2026-10-12 UTC

## 수집 상태
- 페치 성공: [cloud.google.com/Mandiant — Threat Intelligence 블로그 목록](https://cloud.google.com/blog/topics/threat-intelligence) (목록 재확인), [Citrix NetScaler 악용 방어 (Mandiant/GTIG)](https://cloud.google.com/blog/topics/threat-intelligence/defending-against-active-exploitation-of-citrix-netscaler-adc-and-gateway-appliances) (본문 확인 — Cobalt Strike 언급 없음, 자체 제작 웹셸 WHIPSHOT/SLAPSHOT만 확인), [UNC6671 비싱/탈취 (GTIG)](https://cloud.google.com/blog/topics/threat-intelligence/unc6671-targets-financial-services-and-enterprise-cloud-environments) (본문 확인 — Cobalt Strike 또는 기타 C2 프레임워크 언급 없음)
- 페치 차단 (DNS 조회 실패): unit42.paloaltonetworks.com (`/cobalt-strike-team-server/`), recordedfuture.com (`/research/rednovember-...`), thedfirreport.com, group-ib.com (`/blog/`), silentpush.com (`/blog/gentlemen-ransomware/`) — 작업 지시서가 "미검증" 상태로 명시한 4개 소스(unit42, recordedfuture, thedfirreport, group-ib) 전부 이번 실행에서 처음 시도했으나 전부 DNS 단계에서 차단됨을 확인. 장기적으로 기댈 수 있는 신규 소스가 아님이 이번 실행으로 추가 확인됨 — silentpush.com은 과거에도 반복 차단되었던 소스로 재확인만 됨.
- 검증: 0 (신규) / 미검증: 0 (신규) / 검토 필요: 3 (신규, 총계 34)

조용한 하루였습니다 — 신규 공격자 C2(차단 대상), 신규 캠페인, 신규 해시는 발견되지 않았습니다. WebSearch 6개 쿼리 결과는 모두 이미 이 트래커에 기록된 기존 항목(StrikeShark/SharkLoader, The Gentlemen/CountLoader, Nitrogen 랜섬웨어, 워터마크 987654321/666666666/678358251, Operation Morpheus, JARM 헌팅 기법)의 재확인이었습니다. ThreatFox 검색 스니펫에서 기존에 기록되지 않은 Cobalt Strike 태그 스캐너 탐지 IP 3건(124.70.184.106, 43.204.108.246, 47.102.184.26)을 새로 확인했으며, 모두 캠페인/행위자 귀속이 없는 스캐너 전용 탐지이므로 `검토 필요` 목록에만 추가했습니다. 작업 지시서가 지정한 미검증 소스 4곳(unit42.paloaltonetworks.com, recordedfuture.com, thedfirreport.com, group-ib.com)을 이번 실행에서 처음 시도했으나 전부 DNS 조회 실패로 차단되어, 접근 가능한 신규 소스는 발견하지 못했습니다.

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
- 출처: community.gurucul.com (미시도, 과거 차단 확인됨), securelist.com (알려진 차단 도메인) — 60일 범위 밖(참고용)

## 공격자 C2 팀서버 (차단 대상) (6) — 변경 없음
- 108.61.242.65 — UNC2628/DarkSide Cobalt Strike BEACON C2 (Mandiant/Google Cloud Blog) — verified
- 109.206.243.59 — UNC2628/DarkSide Cobalt Strike BEACON C2 (Mandiant/Google Cloud Blog) — verified
- 146.70.78.43 — UNC2628/DarkSide Cobalt Strike BEACON C2 (Mandiant/Google Cloud Blog) — verified
- 45.150.108.213 — UNC2628/DarkSide Cobalt Strike BEACON C2 (Mandiant/Google Cloud Blog) — verified
- 87.120.254.39 — UNC2628/DarkSide Cobalt Strike BEACON C2 (Mandiant/Google Cloud Blog) — verified
- 92.204.160.240 — UNC2628/DarkSide Cobalt Strike BEACON C2 (Mandiant/Google Cloud Blog) — verified
- (도메인 없음 — `iocs/domains.txt`는 현재 공백)

## 검토 필요 — 스캐너 탐지만 된 팀서버 (차단 금지) (34)
전체 목록은 `iocs/needs-review.txt` 참고. 이번 실행 신규 추가 3건:
- 124.70.184.106 — ThreatFox 태그 일반 "Cobalt Strike" C2 (포트 443), 2026-05~06월 관측, 2026-10-12 검색 스니펫 기준 (fetch 미시도) — 캠페인/행위자 귀속 없음 — 스캐너/피드 분류만, 차단 금지
- 43.204.108.246 — ThreatFox 태그 일반 "Cobalt Strike" C2 (포트 443), 2026-05~06월 관측, 2026-10-12 검색 스니펫 기준 (fetch 미시도) — 캠페인/행위자 귀속 없음 — 스캐너/피드 분류만, 차단 금지
- 47.102.184.26 — ThreatFox 태그 일반 "Cobalt Strike" C2 (포트 8443), 2026-05~06월 관측, 2026-10-12 검색 스니펫 기준 (fetch 미시도) — 캠페인/행위자 귀속 없음 — 스캐너/피드 분류만, 차단 금지

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
- 검토 필요 신규 추가: 124.70.184.106, 43.204.108.246, 47.102.184.26 (ThreatFox 스캐너 탐지, 귀속 없음)
- 워터마크/프로파일 보강: 없음
- 메타: 작업 지시서가 지정한 미검증 소스 4곳(unit42.paloaltonetworks.com, recordedfuture.com, thedfirreport.com, group-ib.com)을 이번 실행에서 처음 시도 — 전부 DNS 조회 실패로 차단 확인. silentpush.com도 재시도하여 차단 재확인. cloud.google.com은 목록 페이지 및 개별 게시글 2건(Citrix NetScaler, UNC6671) 본문까지 확인했으나 Cobalt Strike 언급 없음.

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
- [Threat Intelligence blog listing (Google Cloud / Mandiant)](https://cloud.google.com/blog/topics/threat-intelligence) — 2026-10 — fetched (no CS content in list excerpt)
- [Defending Against Active Exploitation of Citrix NetScaler ADC and Gateway Appliances (Mandiant/GTIG)](https://cloud.google.com/blog/topics/threat-intelligence/defending-against-active-exploitation-of-citrix-netscaler-adc-and-gateway-appliances) — 2026-09-29 — fetched (no CS content)
- [UNC6671 Rebrands: Multi-Brand Vishing Extortion... (GTIG)](https://cloud.google.com/blog/topics/threat-intelligence/unc6671-targets-financial-services-and-enterprise-cloud-environments) — 2026 — fetched (no CS content)
- [Cobalt Strike Team Server (Unit 42)](https://unit42.paloaltonetworks.com/cobalt-strike-team-server/) — undated — blocked (DNS)
- [RedNovember Targets Government, Defense, and Technology Organizations (Recorded Future/Insikt Group)](https://www.recordedfuture.com/research/rednovember-targets-government-defense-and-technology-organizations) — 2025-09-24 — blocked (DNS)
- [The DFIR Report — site listing](https://www.thedfirreport.com/) — n/a — blocked (DNS)
- [Group-IB Blog listing](https://www.group-ib.com/blog/) — n/a — blocked (DNS)
- [No Place to Hide: Following a Serial Ransomware Affiliate... to The Gentlemen (Silent Push)](https://www.silentpush.com/blog/gentlemen-ransomware/) — undated — blocked (DNS)
- [StrikeShark: Investigating a New Campaign Delivering Cobalt Strike Through SharkLoader (Gurucul)](https://community.gurucul.com/articles/ThreatResearch/StrikeShark-Investigating-a-New-25-6-2026) — 2026-06-25 — not attempted this run (known blocked)
- [ThreatFox IOC Database — Cobalt Strike C2 entries](https://threatfox.abuse.ch/) — 2026-05/06 — search-snippet only, fetch not attempted this run
