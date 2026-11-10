# Cobalt Strike Snapshot — 2026-11-10 UTC

## 수집 상태
- 페치 성공: cloud.google.com/blog/topics/threat-intelligence (신규 Cobalt Strike 콘텐츠 없음 — 최신 게시물 2건 모두 무관: "Shutting the Door on the XCPE Botnet", "ARTEX and Friends: Enter Agentic Offensive Frameworks"), www.microsoft.com/en-us/security/blog (검색, 신규 콘텐츠 없음 — 기존 2021/2022 게시물만 재노출)
- 페치 차단(신규 시도): unit42.paloaltonetworks.com, recordedfuture.com, thedfirreport.com, group-ib.com, www.techtarget.com — 모두 ENOTFOUND. 이전 실행에서 "미시도, 1회 시도 가치 있음"으로 표시된 4개 도메인(unit42/recordedfuture/thedfirreport/group-ib) 전부 이번 실행에서 차단 확인됨 — 장기적으로 이 트래커가 접근 가능한 도메인 범위는 cloud.google.com, microsoft.com 등 극소수로 유지됨.
- 페치 차단(기존 목록, 재확인 없음): thehackernews.com, medium.com, securityweek.com 등 기존 차단 도메인 리스트 그대로 (이번 실행 미시도)
- 검증: 누적 9건 (C2 IP 6 + 해시 2 + GCTI 크랙판 배경자료 1) / 미검증: 누적 6건 (C2 IP 1 + 도메인 5) / 검토 필요: 46

## 최근 캠페인 (최근 60일)

캠페인 수준의 전적으로 새로운 보고는 이번 실행에서도 없음 (2026-10-13 이후 지속, 28일 연속 조용한 날 — 차단 대상 기준). WebSearch 결과는 모두 기존에 기록된 캠페인(StrikeShark/SharkLoader, The Gentlemen/CountLoader, UNG0002/Operation Dragon Whistle, Middle East Malicious Infrastructure Report, hunt.io "Rare Watermark" 클러스터)의 재노출이었으며, 모두 60일 기준을 벗어나거나 이미 미검증으로 기록된 내용과 동일함. ThreatFox 스니펫에서 신규 IOC ID 다수(예: #1856814, #1850746, #1832048 등)가 노출되었으나, threatfox.abuse.ch 자체가 지속적으로 페치 차단되어 실제 IP/도메인 값을 확인할 수 없었으므로 기록하지 않음(ID만으로는 호스트 값을 알 수 없어 검토 필요 목록에도 추가하지 않음).

- 참고(재확인, 변경 없음): Silver Dragon, UNG0002(Dragon Whistle/Cobalt Whisper/AmberMist), StrikeShark/SharkLoader, The Gentlemen/CountLoader, Ghostwriter, RedNovember — 이번 실행 검색에서 재노출, 상세 변경 없음.

## 공격자 C2 팀서버 (차단 대상) (6)
- 108.61.242[.]65 — KnowledgeDeliver/CVE-2026-5426 또는 BlackByte 관련 검증된 캠페인 C2 — verified
- 109.206.243[.]59 — 상동 — verified
- 146.70.78[.]43 — 상동 — verified
- 45.150.108[.]213 — 상동 — verified
- 87.120.254[.]39 — 상동 — verified
- 92.204.160[.]240 — 상동 — verified

(도메인 없음)

## 검토 필요 — 스캐너 탐지만 된 팀서버 (차단 금지) (46)
- 변경 없음, 기존 46건 유지. 상세는 `iocs/needs-review.txt` 참조.

## JARM 헌팅 신호 (차단 용도 아님)
- `07d14d16d21d21d00042d41d00041de5fb3038104f457d92ba02e9311512c2` — Cobalt Strike 기본 팀서버 JARM (OpenJDK 11), 일반 헌팅 신호
- `07d14d16d21d21d07c42d41d00041d24a458a375eef0c576d23a7bab9a9fb1` — 동일 기본값의 대체 보고값 (Java 11 SSL 스택), 2차 후보로 기록
- 이번 실행에서 두 값 모두 재확인(RST Cloud, HiveSecurity 스니펫) — 두 소스가 서로 다른 해시를 "기본값"으로 제시하여 기존의 미합치 상태 유지. 신규 변경 없음.

## 워터마크 · 맬리어블 프로파일
- **0 / 1** — 크랙판 공통값, 차단 신호 아님 (LOW SIGNAL)
- **100000000 / 666666666 / 987654321 / 678358251 / 688983459** — 크랙판/공유 클러스터 값, 개별 캠페인 귀속 없음 또는 약한 귀속, 차단 신호로 사용 금지.
- **1473793097 / 1357776117** — "The Gentlemen"/CountLoader 체인 특정 값 (미검증, Silent Push)
- **BeudtKgqnlm0Ruvf+VYxuw==** — APT24 특정 워터마크 해시 (검증됨, Mandiant)
- 전체 목록은 `iocs/watermarks-and-profiles.md` 참조 (누적, 이번 실행 변경 없음)

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
- 네트워크 범위 확인: unit42.paloaltonetworks.com, recordedfuture.com, thedfirreport.com, group-ib.com, www.techtarget.com — 이번 실행에서 신규로 차단 확인 (ENOTFOUND)

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
- [Google Cloud — Threat Intelligence Blog](https://cloud.google.com/blog/topics/threat-intelligence) — 2026-11-10 — fetched (신규 CS 콘텐츠 없음)
- [Microsoft Security Blog — "cobalt strike" 검색](https://www.microsoft.com/en-us/security/blog/?s=cobalt+strike) — 2026-11-10 — fetched (신규 CS 콘텐츠 없음)
- unit42.paloaltonetworks.com — 2026-11-10 — blocked (ENOTFOUND, 신규 시도)
- recordedfuture.com — 2026-11-10 — blocked (ENOTFOUND, 신규 시도)
- thedfirreport.com — 2026-11-10 — blocked (ENOTFOUND, 신규 시도)
- group-ib.com — 2026-11-10 — blocked (ENOTFOUND, 신규 시도)
- www.techtarget.com — 2026-11-10 — blocked (ENOTFOUND, 신규 시도)
