# Cobalt Strike Snapshot — 2026-10-13 UTC

## 수집 상태
- 페치 성공: [Threat Intelligence 블로그 목록 (Google Cloud/Mandiant)](https://cloud.google.com/blog/topics/threat-intelligence) (목록 재확인 — Cobalt Strike/Beacon/C2 팀서버 관련 신규 게시물 없음), [Microsoft Security Blog 검색 결과 (cobalt strike)](https://www.microsoft.com/en-us/security/blog/?s=cobalt+strike) (검색 결과 확인 — 2026년 신규 Cobalt Strike 전용 게시물 없음, 기존에 알려진 2021~2024년 게시물만 노출)
- 페치 차단 (DNS 조회 실패): threatfox.abuse.ch (`/ioc/1892469/json/`), hunt.io (`/blog/rare-watermark-links-cobalt-strike-team-servers-to-ongoing-suspicious-activity`) — 둘 다 과거 실행에서도 반복적으로 차단되었던 소스로, 이번 실행에서도 DNS 단계에서 동일하게 차단됨을 재확인
- 검증: 0 (신규) / 미검증: 0 (신규) / 검토 필요: 0 (신규, 총계 34, 변경 없음)

조용한 하루였습니다 — 신규 공격자 C2(차단 대상), 신규 캠페인, 신규 해시, 신규 검토 필요 항목 모두 발견되지 않았습니다. WebSearch 6개 쿼리 결과는 전부 이미 이 트래커에 기록된 기존 항목(StrikeShark/SharkLoader, The Gentlemen/CountLoader, Nitrogen 랜섬웨어, 워터마크 987654321/678358251, Operation Morpheus, hunt.io 워터마크 클러스터, JARM/RST Cloud 헌팅 기법, OrangeCon 2026 ML 탐지 발표)의 재확인이었습니다. 검색 스니펫에 언급된 ThreatFox IP 3건(107.174.14.102:443, 47.103.214.7:18443, 206.119.178.109:18443)은 모두 이미 `iocs/needs-review.txt`에 등록되어 있어 신규 추가 사항이 없습니다. threatfox.abuse.ch와 hunt.io는 직접 fetch를 시도했으나 과거와 동일하게 DNS 조회 단계에서 차단되었습니다.

## 최근 캠페인 (최근 60일) — 변경 없음, 기존 캠페인 참고용 재게시

### "The Gentlemen" 랜섬웨어 제휴자 — CountLoader + Cobalt Strike ⚠️ (미검증)
- 대상: 불특정 (LockBit·Black Basta·Qilin 제휴자 활동 추적)
- 초기 침투: CountLoader 경유
- Cobalt Strike 역할: CountLoader가 전달하는 2차 페이로드, 워터마크 1473793097 / 1357776117 사용
- 관측 시점: 2026-02 (Silent Push 보고서)
- 출처: silentpush.com (fetch 미시도, 과거 반복 차단 확인됨 — 검색 스니펫만 재확인)

### Nitrogen 랜섬웨어 — Cobalt Strike + 로그 와이핑 ⚠️ (미검증)
- 대상: 불특정
- 초기 침투: 가짜 WinSCP 설치파일(악성 광고 유포 추정) 또는 불명
- Cobalt Strike 역할: 측면 이동/지속성 확보, 워터마크 678358251 사용 가능성 (BlackCat 랜섬웨어로 종결)
- 관측 시점: 2026-09 (2026-09-15 보도)
- 출처: gbhackers.com (변경 없음, 이번 실행에서 재시도하지 않음)

### StrikeShark / SharkLoader — Cobalt Strike Beacon 로더 ⚠️ (미검증) — 변경 없음
- 출처: community.gurucul.com, securelist.com (둘 다 알려진 차단 도메인, 이번 실행 재시도하지 않음) — 60일 범위 밖(참고용)

## 공격자 C2 팀서버 (차단 대상) (6) — 변경 없음
- 108.61.242.65 — UNC2628/DarkSide Cobalt Strike BEACON C2 (Mandiant/Google Cloud Blog) — verified
- 109.206.243.59 — UNC2628/DarkSide Cobalt Strike BEACON C2 (Mandiant/Google Cloud Blog) — verified
- 146.70.78.43 — UNC2628/DarkSide Cobalt Strike BEACON C2 (Mandiant/Google Cloud Blog) — verified
- 45.150.108.213 — UNC2628/DarkSide Cobalt Strike BEACON C2 (Mandiant/Google Cloud Blog) — verified
- 87.120.254.39 — UNC2628/DarkSide Cobalt Strike BEACON C2 (Mandiant/Google Cloud Blog) — verified
- 92.204.160.240 — UNC2628/DarkSide Cobalt Strike BEACON C2 (Mandiant/Google Cloud Blog) — verified
- (도메인 없음 — `iocs/domains.txt`는 현재 공백)

## 검토 필요 — 스캐너 탐지만 된 팀서버 (차단 금지) (34) — 변경 없음
전체 목록은 `iocs/needs-review.txt` 참고. 이번 실행 신규 추가 없음 (검색에 나온 ThreatFox IP 3건은 기존 등록분과 중복).

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
- 메타: cloud.google.com 블로그 목록과 Microsoft Security Blog 검색 결과를 fetch하여 2026년 신규 Cobalt Strike 전용 게시물 유무를 확인했으나 발견되지 않음. threatfox.abuse.ch, hunt.io는 이번 실행에서도 DNS 조회 단계에서 차단 재확인.

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
- [Threat Intelligence blog listing (Google Cloud / Mandiant)](https://cloud.google.com/blog/topics/threat-intelligence) — 2026-10 — fetched (no CS content)
- [Microsoft Security Blog search: "cobalt strike"](https://www.microsoft.com/en-us/security/blog/?s=cobalt+strike) — 2026-10 — fetched (no new 2026 CS-specific posts)
- [ThreatFox IOC Database entry 1892469](https://threatfox.abuse.ch/ioc/1892469/json/) — n/a — blocked (DNS)
- [Rare Watermark Links Cobalt Strike 4.10 Team Servers to Ongoing Suspicious Activity (Hunt.io)](https://hunt.io/blog/rare-watermark-links-cobalt-strike-team-servers-to-ongoing-suspicious-activity) — undated — blocked (DNS)
- [StrikeShark: Investigating a New Campaign Delivering Cobalt Strike Through SharkLoader (Gurucul)](https://community.gurucul.com/articles/ThreatResearch/StrikeShark-Investigating-a-New-25-6-2026) — 2026-06-25 — not attempted this run (known blocked)
- [No Place to Hide: Following a Serial Ransomware Affiliate... to The Gentlemen (Silent Push)](https://www.silentpush.com/blog/gentlemen-ransomware/) — undated — not attempted this run (known blocked, DNS-unreachable)
- [ThreatFox IOC Database — Cobalt Strike C2 entries](https://threatfox.abuse.ch/) — 2026-05/09 — search-snippet only, fetch blocked
