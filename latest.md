# Cobalt Strike Snapshot — 2026-11-06 UTC

## 수집 상태
- 페치 성공: microsoft.com (en-us/security/blog 검색), cloud.google.com/blog/topics/threat-intelligence (둘 다 2026년 신규 Cobalt Strike 특정 콘텐츠 없음)
- 페치 차단: www.silentpush.com, unit42.paloaltonetworks.com (team-server, malleable-c2 두 URL 모두), hunt.io, msrc.microsoft.com (**신규 확인** — microsoft.com 본체는 reachable이나 서브도메인은 차단), threatfox.abuse.ch, community.gurucul.com, thedfirreport.com — 모두 DNS 해석 실패(ENOTFOUND), 기존 차단 목록과 일치(msrc.microsoft.com 제외)
- 검증: 누적 8건 (C2 IP 6 + 해시 2) / 미검증: 누적 6건 (C2 IP 1 + 도메인 5) / 검토 필요: 41

## 최근 캠페인 (최근 60일)

캠페인 수준의 전적으로 새로운 보고는 이번 실행에서도 없음 (2026-10-13 이후 지속, 24일 연속 조용한 날). 기존에 추적 중인 캠페인(StrikeShark/SharkLoader, The Gentlemen/CountLoader, RedNovember, Ghostwriter, UNG0002 등)에 대한 신규 세부 보강도 없음 — 이번 실행 검색 스니펫은 모두 기존에 기록된 내용의 재확인이었음.

### "The Gentlemen" 랜섬웨어 제휴자 — CountLoader + Cobalt Strike ⚠️ (미검증, 참고용 — 상세는 누적 기록 참조)
- 대상: 특정되지 않음 (LockBit·Black Basta·Qilin 제휴 이력을 가진 연쇄 랜섬웨어 제휴자)
- 초기 침투: CountLoader (크랙/불법 복제 소프트웨어 유포 사이트 경유)
- Cobalt Strike 역할: CountLoader → Cobalt Strike 페이로드 전달 → 랜섬웨어
- 관측 시점: 2026-02 (최초 탐지, 60일 창 밖이나 유일한 네임드 캠페인으로 참고 유지)
- C2 IP: 91.107.247[.]163 — `iocs/unverified-ips.txt`에 미검증 공격자 C2로 기존 등재
- 출처: Silent Push "No Place to Hide..." (silentpush.com, 차단됨 — 검색 스니펫만)

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
- 신규 차단 확인 도메인: msrc.microsoft.com (microsoft.com 본체는 reachable이나 이 서브도메인은 DNS 해석 실패로 신규 확인됨; www.silentpush.com, unit42.paloaltonetworks.com, hunt.io, threatfox.abuse.ch, community.gurucul.com, thedfirreport.com은 기존 차단 재확인)

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
- [StrikeShark: Investigating a New Campaign Delivering Cobalt Strike Through SharkLoader](https://community.gurucul.com/articles/ThreatResearch/StrikeShark-Investigating-a-New-25-6-2026) — 2026-06-25 — blocked
- [No Place to Hide: Following a Serial Ransomware Affiliate ... to The Gentlemen](https://www.silentpush.com/blog/gentlemen-ransomware/) — 2026-02 — blocked
- [Cobalt Strike team server](https://unit42.paloaltonetworks.com/cobalt-strike-team-server/) — undated — blocked
- [Cobalt Strike Malleable C2 Profile](https://unit42.paloaltonetworks.com/cobalt-strike-malleable-c2/) — undated — blocked
- [Rare Watermark Links Cobalt Strike 4.10 Team Servers to Ongoing Suspicious Activity](https://hunt.io/blog/rare-watermark-links-cobalt-strike-team-servers-to-ongoing-suspicious-activity) — 2026-10 — blocked
- [Hunting for Cobalt Strike: mining and plotting for fun and profit](https://msrc.microsoft.com/blog/2022/10/hunting-for-cobalt-strike-mining-and-plotting-for-fun-and-profit) — 2022-10 — blocked (신규 확인)
- [Microsoft Security Blog search: Cobalt Strike](https://www.microsoft.com/en-us/security/blog/?s=cobalt+strike) — 다양 (2021-2024) — fetched, 2026년 신규 콘텐츠 없음
- [Google Cloud Blog — Threat Intelligence](https://cloud.google.com/blog/topics/threat-intelligence) — 다양 — fetched, Cobalt Strike 관련 신규 콘텐츠 없음
