# Cobalt Strike Snapshot — 2026-11-05 UTC

## 수집 상태
- 페치 성공: 없음
- 페치 차단: connectwise.com, infoblox.com, netlas.io, unit42.paloaltonetworks.com (및 .md 변형), techcentral.co.za, it-daily.net, blog.eset.ie, scworld.com (모두 이번 실행에서 DNS 해석 실패로 신규 확인됨, microsoft.com·cloud.google.com 외 모두 차단된 기존 목록과 일치)
- 검증: 2 / 미검증: 6 / 검토 필요: 41

## 최근 캠페인 (최근 60일)

캠페인 수준의 전적으로 새로운 보고는 이번 실행에서 없음 (2026-10-13 이후 지속). 기존에 추적 중인 캠페인(StrikeShark/SharkLoader, The Gentlemen/CountLoader, RedNovember, Ghostwriter, UNG0002 등)에 대한 세부 보강만 발생.

### "The Gentlemen" 랜섬웨어 제휴자 — CountLoader + Cobalt Strike ⚠️ (미검증)
- 대상: 특정되지 않음 (LockBit·Black Basta·Qilin 제휴 이력을 가진 연쇄 랜섬웨어 제휴자)
- 초기 침투: CountLoader (크랙/불법 복제 소프트웨어 유포 사이트 경유)
- Cobalt Strike 역할: CountLoader → Cobalt Strike 페이로드 전달 → 랜섬웨어
- 관측 시점: 2026-02 (최초 탐지)
- 신규 IOC: C2 IP **91.107.247[.]163** — Silent Push가 Check Point의 공개 침해대응 보고서와 교차 매칭; 출처 미페치(silentpush.com, DNS 불가) — `iocs/unverified-ips.txt`에 미검증 공격자 C2로 추가
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
- 기존 39건 유지 (UNC2628/DarkSide 2021년 구 인프라, ThreatFox 일반 태그, Vermilion Strike 등 — 상세는 `iocs/needs-review.txt` 참조)
- **신규**: 197.51.170[.]131 — Middle East Malicious Infrastructure Report (securitricks.com, 차단됨); 2026년 2-5월 지역 집계(98개 공급자, 1,350+ C2), 개별 캠페인 귀속 없음 — 스캐너 탐지만, 차단 금지
- **신규**: 5.109.182[.]231 — 상동 리포트, 상동 이유 — 차단 금지

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
- 신규 C2 (미검증, 차단 대상 아님): 91.107.247[.]163 (The Gentlemen/CountLoader, unverified-ips.txt)
- 신규 해시: 없음
- 승격(미검증→검증): 없음
- 분류 변경: 없음
- 검토 필요 신규 추가: 197.51.170[.]131, 5.109.182[.]231 (Middle East 인프라 리포트, 스캐너 집계만)
- 신규 차단 확인 도메인: connectwise.com, infoblox.com, netlas.io, techcentral.co.za, it-daily.net, blog.eset.ie, scworld.com (unit42.paloaltonetworks.com은 기존 차단 재확인)

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
- [Middle East Malicious Infrastructure Report](https://securitricks.com/attackreports/middle-east-malicious-infrastructure-report-1350-c2-servers-mapped-across-98-providers) — 2026-05 — blocked
- [Cobalt Strike: Complete detection and defense guide](https://www.vectra.ai/topics/cobalt-strike) — undated — blocked
- [How we hunt C2 infrastructure at RST Cloud using Netlas](https://netlas.io/blog/%D1%812_hunting_by_rst_cloud/) — 2026-03 — blocked
- [Fake Kaseya updates serving up Cobalt Strike](https://connectwise.com/resources/fake-kaseya-updates-serving-up-cobalt-strike) — undated — blocked
- [Cobalt Strike malware campaign targets job seekers](https://www.techtarget.com/cybersecurity/news/252525560/Cobalt-Strike-malware-campaign-targets-job-seekers) — undated — blocked (from prior run)
