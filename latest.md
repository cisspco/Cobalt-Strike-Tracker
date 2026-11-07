# Cobalt Strike Snapshot — 2026-11-07 UTC

## 수집 상태
- 페치 성공: microsoft.com (en-us/security/blog 검색, 2026년 신규 Cobalt Strike 콘텐츠 없음 — 최신 항목은 2024-09 Storm-0501), cloud.google.com/blog/topics/threat-intelligence (Cobalt Strike/beacon/team server 언급 없음, 날짜 미기재)
- 페치 차단: www.recordedfuture.com, unit42.paloaltonetworks.com, thedfirreport.com, www.group-ib.com (모두 ENOTFOUND — 이번 실행에서 신규로 시도했으나 차단 확인), threatfox.abuse.ch (기존 차단 재확인)
- 검증: 누적 8건 (C2 IP 6 + 해시 2) / 미검증: 누적 6건 (C2 IP 1 + 도메인 5) / 검토 필요: 41

## 최근 캠페인 (최근 60일)

캠페인 수준의 전적으로 새로운 보고는 이번 실행에서도 없음 (2026-10-13 이후 지속, 25일 연속 조용한 날). 검색 쿼리 6종 모두 기존에 기록된 캠페인(StrikeShark/SharkLoader, The Gentlemen/CountLoader, Ghostwriter, UNG0002, RedNovember)의 재확인 결과만 반환했음. 신규 세부 보강 없음.

- 참고(신규 확인되지 않음, 기존 기록 유지): ESET Ghostwriter(지오펜싱 PDF, 우크라이나/폴란드 정부 대상, 2026-03~) — 이번 검색 스니펫에서 재확인, 상세 변경 없음.
- 참고(신규 확인되지 않음, 기존 기록 유지): Seqrite UNG0002(중국 대학 대상, medium-high confidence, 2026-05-22) — 재확인, 상세 변경 없음.

## 공격자 C2 팀서버 (차단 대상) (6)
- 108.61.242[.]65 — KnowledgeDeliver/CVE-2026-5426 또는 BlackByte 관련 검증된 캠페인 C2 — verified
- 109.206.243[.]59 — 상동 — verified
- 146.70.78[.]43 — 상동 — verified
- 45.150.108[.]213 — 상동 — verified
- 87.120.254[.]39 — 상동 — verified
- 92.204.160[.]240 — 상동 — verified

(도메인 없음)

## 검토 필요 — 스캐너 탐지만 된 팀서버 (차단 금지) (41)
- 기존 41건 유지, 신규 추가 없음 (상세는 `iocs/needs-review.txt` 참조)

## JARM 헌팅 신호 (차단 용도 아님)
- `07d14d16d21d21d00042d41d00041de5fb3038104f457d92ba02e9311512c2` — Cobalt Strike 기본 팀서버 JARM (OpenJDK 11), 일반 헌팅 신호
- `07d14d16d21d21d07c42d41d00041d24a458a375eef0c576d23a7bab9a9fb1` — 동일 기본값의 대체 보고값 (Java 11 SSL 스택), 2차 후보로 기록

## 워터마크 · 맬리어블 프로파일
- **0** — 크랙판 공통값, 차단 신호 아님 (LOW SIGNAL)
- **1** — 크랙판 공통값, Talos 보고 (미검증), LOW SIGNAL
- **100000000 / 666666666 / 987654321 / 678358251 / 688983459** — 크랙판/공유 클러스터 값, 개별 캠페인 귀속 없음 또는 약한 귀속, 차단 신호로 사용 금지
- **1473793097 / 1357776117** — "The Gentlemen"/CountLoader 체인 특정 값 (미검증, Silent Push)
- **BeudtKgqnlm0Ruvf+VYxuw==** — APT24 특정 워터마크 해시 (검증됨, Mandiant)
- 전체 목록은 `iocs/watermarks-and-profiles.md` 참조 (누적)

## 파일 해시 (2)
### SHA-256
- 5f37b85687780c089607670040dbb3da2749b91b8adc0aa411fd6280b5fa7103 — beacon — BlackByte ransomware intrusion (ProxyShell Exchange exploitation) — verified
- 7c1f99dca8e5a7897892f9d224a6495023a2cfd2671697d229d355978c415ed2 — loader — KnowledgeDeliver/CVE-2026-5426 — verified

## 호스트 IOC · 행위
- SMB BEACON named pipe `\\.\pipe\UIA_PIPE_*` (UNC2628/DarkSide)
- DNS BEACON 서브도메인 패턴 `h.dns.<C2 domain>`, `ridoj4.<8자>.dns.<C2 domain>` 등 (UNC4393/BASTA)
- 자세한 내용은 `iocs/watermarks-and-profiles.md` 참조

## 이번 실행 변경사항
- 신규 C2 (검증, 차단 대상): 없음
- 신규 C2 (미검증, 차단 대상 아님): 없음
- 신규 해시: 없음
- 승격(미검증→검증): 없음
- 분류 변경: 없음
- 검토 필요 신규 추가: 없음
- 신규 차단 확인 도메인: www.recordedfuture.com, unit42.paloaltonetworks.com, thedfirreport.com, www.group-ib.com (이번 실행에서 처음 시도 — 모두 ENOTFOUND로 신규 확인); threatfox.abuse.ch는 기존 차단 재확인

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
- [Microsoft Security Blog search: Cobalt Strike](https://www.microsoft.com/en-us/security/blog/?s=cobalt+strike) — 다양 (2021-2024) — fetched, 2026년 신규 콘텐츠 없음
- [Google Cloud Blog — Threat Intelligence](https://cloud.google.com/blog/topics/threat-intelligence) — 다양 — fetched, Cobalt Strike 관련 신규 콘텐츠 없음
- [Recorded Future — Cobalt Strike research](https://www.recordedfuture.com/research/cobalt-strike) — N/A — blocked (신규 시도, ENOTFOUND)
- [Unit 42 — Cobalt Strike team server](https://unit42.paloaltonetworks.com/cobalt-strike-team-server/) — undated — blocked (신규 시도, ENOTFOUND)
- [The DFIR Report search: Cobalt Strike](https://thedfirreport.com/?s=cobalt+strike) — N/A — blocked (신규 시도, ENOTFOUND)
- [Group-IB Blog](https://www.group-ib.com/blog/) — N/A — blocked (신규 시도, ENOTFOUND)
- [ThreatFox IOC #1850746](https://threatfox.abuse.ch/ioc/1850746/json/) — N/A — blocked (기존 차단 재확인)
