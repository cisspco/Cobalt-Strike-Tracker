# Cobalt Strike Snapshot — 2026-11-21 UTC

## 수집 상태
- 페치 성공: www.microsoft.com/th-th/security/business/security-insider/threat-briefs/ (Manatee Tempest 재확인, 신규 정보 없음), www.microsoft.com/en-us/security/security-insider/manatee-tempest (재확인, 2024-01-25 게시물, 변경 없음)
- 페치 차단: research.checkpoint.com, securelist.com, hunt.io, community.gurucul.com, thedfirreport.com, unit42.paloaltonetworks.com (모두 ENOTFOUND로 재확인 — 기존 차단 목록과 일치, 신규 차단 도메인 없음)
- 검증: 누적 17건 (IOC 값 기준, 변경 없음) / 미검증: 누적 7건 (변경 없음) / 검토 필요: 46건 (변경 없음)

## 최근 캠페인 (최근 60일)

캠페인 수준의 전적으로 새로운 보고는 이번 실행에서도 없음 (35일 연속 조용한 날). 이번 실행의 6개 필수 검색 쿼리는 모두 기존에 기록된 캠페인/IOC만 재노출함: StrikeShark/SharkLoader(Securelist/Gurucul, 2026-06, 출처 접근 불가), The Gentlemen/CountLoader(Silent Push·Check Point, 2026-02~04, 출처 접근 불가, 워터마크 1473793097/1357776117, C2 91.107.247[.]163 — 기존과 동일 미검증), Manatee Tempest/EvilCorp(Microsoft, 검증, IOC 값 없음, 재확인만). 신규 캠페인명, 신규 공격자 귀속 C2, 신규 해시, 신규 워터마크 값 없음.

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

## JARM 헌팅 신호 (차단 용도 아님) (3)
- `07d14d16d21d21d00042d41d00041de5fb3038104f457d92ba02e9311512c2` — Cobalt Strike 기본 팀서버 JARM (OpenJDK 11), 일반 헌팅 신호 — unverified
- `07d14d16d21d21d07c42d41d00041d24a458a375eef0c576d23a7bab9a9fb1` — 동일 기본값의 대체 보고값 (Java 11 SSL 스택), 2차 후보 — unverified
- `2ad2ad16d2ad2ad00042d42d00042ddb04deffa1705e2edc44cae1ed24a4da` — socat/iptables 뒤로 리다이렉트된 팀서버의 3번째 후보값(Kali 기반 예시) — unverified
- 참고: 이번 실행에서도 신규 JARM 값 없음.

## 워터마크 · 맬리어블 프로파일
- **0 / 1** — 크랙판 공통값, 차단 신호 아님 (LOW SIGNAL)
- **100000000 / 666666666 / 987654321 / 678358251 / 688983459** — 크랙판/공유 클러스터 값, 개별 캠페인 귀속 없음 또는 약한 귀속, 차단 신호로 사용 금지.
- **1473793097 / 1357776117** — "The Gentlemen"/CountLoader 체인 특정 값 (미검증, Silent Push)
- **BeudtKgqnlm0Ruvf+VYxuw==** — APT24 특정 워터마크 해시 (검증됨, Mandiant)
- **666** — Storm-0501 고유 변조 워터마크 (검증됨, Microsoft, 2024-09-26)
- Manatee Tempest/EvilCorp — Cobalt Strike 로더 공급자 역할 (검증됨, Microsoft, IOC 값 없음)
- 전체 목록은 `iocs/watermarks-and-profiles.md` 참조 (누적, 이번 실행 변경 없음)

## 파일 해시 (8)
### SHA-256
- 53e2dec3e16a0ff000a8c8c279eeeca8b4437edb8ec8462bfbd9f64ded8072d9 — beacon — Storm-0501/Embargo ransomware — verified
- 5f37b85687780c089607670040dbb3da2749b91b8adc0aa411fd6280b5fa7103 — beacon — BlackByte ransomware intrusion (ProxyShell Exchange exploitation) — verified
- 7c1f99dca8e5a7897892f9d224a6495023a2cfd2671697d229d355978c415ed2 — loader — KnowledgeDeliver/CVE-2026-5426 — verified
- 827f7178802b2e92988d7cff349648f334bc86317b0b628f4bb9264285fccf5f — beacon — Storm-0501/Embargo ransomware — verified
- caa21a8f13a0b77ff5808ad7725ff3af9b74ce5b67426c84538b8fa43820a031 — beacon — Storm-0501/Embargo ransomware — verified
- d37dc37fdcebbe0d265b8afad24198998ae8c3b2c6603a9258200ea8a1bd7b4a — beacon — Storm-0501/Embargo ransomware — verified
- de09ec092b11a1396613846f6b082e1e1ee16ea270c895ec6e4f553a13716304 — beacon — Storm-0501/Embargo ransomware — verified
- ee80f3e3ad43a283cbc83992e235e4c1b03ff3437c880be02ab1d15d92a8348a — beacon — Storm-0501/Embargo ransomware — verified

## 호스트 IOC · 행위
- SMB BEACON named pipe `\\.\pipe\UIA_PIPE_*` (UNC2628/DarkSide)
- DNS BEACON 서브도메인 패턴 `h.dns.<C2 domain>`, `ridoj4.<8자>.dns.<C2 domain>` 등 (UNC4393/BASTA)
- Beacon이 `rundll32.exe`(.dll)/`regsvr32.exe`(.ocx)로 실행됨 (Storm-0501)
- Beacon이 "Windows Media Configuration Utility"로 위장 (LockBit 선행 침투, DFIR Report 2025-01-27, 미검증)
- 자세한 내용은 `iocs/watermarks-and-profiles.md` 참조

## 이번 실행 변경사항
- 신규 C2 (검증, 차단 대상): 없음
- 신규 C2 (미검증, 차단 대상 아님): 없음
- 신규 해시: 없음
- 승격(미검증→검증): 없음
- 분류 변경: 없음
- 검토 필요 신규 추가: 없음
- 신규 JARM 후보: 없음
- 신규 워터마크/배경 귀속 노트: 없음
- 네트워크 범위 확인: research.checkpoint.com, securelist.com, hunt.io, community.gurucul.com, thedfirreport.com, unit42.paloaltonetworks.com — 모두 재시도, 전부 차단 재확인 (ENOTFOUND, 기존 목록과 일치). www.microsoft.com은 정상 접근(2회), 신규 CS 관련 콘텐츠 없음. 35번째 연속 조용한 날 (검증된 공격자 C2/캠페인 수준 신규 발견 없음, 스트릭: 2026-10-13 ~ 2026-11-21).

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
- [Microsoft Security Insider — Manatee Tempest](https://www.microsoft.com/en-us/security/security-insider/manatee-tempest) — 재확인 2026-11-21 — fetched
- [Microsoft Security Insider — Threat briefs (th-th)](https://www.microsoft.com/th-th/security/business/security-insider/threat-briefs/) — 2026-11-21 — fetched
- [Check Point Research — DFIR Report: The Gentlemen](https://research.checkpoint.com/2026/dfir-report-the-gentlemen/) — 2026-11-21 — blocked (ENOTFOUND)
- [Securelist — StrikeShark campaign](https://securelist.com/strikeshark-campaign/120326/) — 2026-11-21 — blocked (ENOTFOUND)
- [Hunt.io — Rare watermark links Cobalt Strike team servers](https://hunt.io/blog/rare-watermark-links-cobalt-strike-team-servers-to-ongoing-suspicious-activity) — 2026-11-21 — blocked (ENOTFOUND)
- [Gurucul Community — StrikeShark investigation](https://community.gurucul.com/articles/ThreatResearch/StrikeShark-Investigating-a-New-25-6-2026) — 2026-11-21 — blocked (ENOTFOUND)
- [The DFIR Report — Lunar Spider intrusion](https://thedfirreport.com/?p=48447) — 2026-11-21 — blocked (ENOTFOUND)
- [Unit 42 — Cobalt Strike Team Server](https://unit42.paloaltonetworks.com/cobalt-strike-team-server/) — 2026-11-21 — blocked (ENOTFOUND)
