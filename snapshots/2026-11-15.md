# Cobalt Strike Snapshot — 2026-11-15 UTC

## 수집 상태
- 페치 성공: cloud.google.com/blog/products/identity-security/making-cobalt-strike-harder-for-threat-actors-to-abuse (2022-11-18 GCTI 크랙판 카탈로그 — 기존 자료 재확인, 신규 내용 없음)
- 페치 차단: unit42.paloaltonetworks.com/cobalt-strike-team-server/, unit42.paloaltonetworks.com/attackers-exploit-public-cobalt-strike-profiles/, thedfirreport.com/2025/01/27/cobalt-strike-and-a-pair-of-socks-lead-to-lockbit-ransomware/, thedfirreport.com/?p=48447 (Lunar Spider), www.silentpush.com/blog/gentlemen-ransomware/, hunt.io/blog/rare-watermark-links-cobalt-strike-team-servers-to-ongoing-suspicious-activity, securelist.com/strikeshark-campaign/120326/, www.recordedfuture.com/research/2025-year-in-review-malicious-infrastructure, msrc.microsoft.com/blog/2022/10/hunting-for-cobalt-strike-mining-and-plotting-for-fun-and-profit — 전부 ENOTFOUND (모두 이전 실행에서도 차단 확인된 호스트와 동일 패턴)
- 검증: 누적 17건 (변경 없음) / 미검증: 누적 7건 (IOC 값 없는 캠페인 언급 2건이 신규로 등장했으나 구체적 IP/도메인/해시/워터마크 값이 없어 IOC 수에는 반영되지 않음) / 검토 필요: 46건 (변경 없음)

## 최근 캠페인 (최근 60일)

캠페인 수준의 전적으로 새로운 보고는 이번 실행에서도 없음. 다만 검색 스니펫에서 두 건의 새로운 DFIR Report 기사 제목이 처음 노출되어 아래 기록 (기사 본문 접근 차단, IOC 값 없음, 날짜상 60일 창 밖 또는 불명):

### Cobalt Strike + SOCKS 프록시 → LockBit 랜섬웨어 (DFIR Report, 2025-01-27, 60일 창 밖)
- Cobalt Strike 역할: "Windows Media Configuration Utility"를 위장한 Beacon이 초기 사후침투 임플란트로 사용, SOCKS 프록시 체이닝을 거쳐 LockBit 랜섬웨어 배포로 이어짐
- 관측 시점: 2025-01 (보고서 게시일 2025-01-27)
- 출처: thedfirreport.com (fetch blocked, 미검증)

### "Lunar Spider" — 약 2개월간 지속된 침투 (DFIR Report, 날짜 불명)
- Cobalt Strike 역할/IOC: 스니펫에 구체적 정보 없음 (행위자명만 확인)
- 출처: thedfirreport.com (fetch blocked, 미검증)

- 참고(재확인, 변경 없음): StrikeShark/SharkLoader, The Gentlemen/CountLoader(워터마크 1473793097/1357776117, C2 91.107.247.163), RedNovember/Pantegana, SNOWLIGHT/GoCobaltStrike, Nitrogen(워터마크 678358251), Aur0ra 랜섬웨어, Ghostwriter, UNG0002/Dragon Whistle, Silver Dragon(APT41) — 이번 실행 검색에서 재노출, 상세 변경 없음.

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

## 워터마크 · 맬리어블 프로파일
- **0 / 1** — 크랙판 공통값, 차단 신호 아님 (LOW SIGNAL)
- **100000000 / 666666666 / 987654321 / 678358251 / 688983459** — 크랙판/공유 클러스터 값, 개별 캠페인 귀속 없음 또는 약한 귀속, 차단 신호로 사용 금지.
- **1473793097 / 1357776117** — "The Gentlemen"/CountLoader 체인 특정 값 (미검증, Silent Push)
- **BeudtKgqnlm0Ruvf+VYxuw==** — APT24 특정 워터마크 해시 (검증됨, Mandiant)
- **666** — Storm-0501 고유 변조 워터마크 (검증됨, Microsoft, 2024-09-26)
- 전체 목록 및 신규 캠페인 언급 2건은 `iocs/watermarks-and-profiles.md` 참조 (누적)

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
- 신규 워터마크: 없음
- 신규 캠페인 배경 노트: 2건 (DFIR Report "Cobalt Strike and a Pair of SOCKS Lead to LockBit Ransomware", 2025-01-27; DFIR Report "Lunar Spider" 침투 사례) — 둘 다 미검증(fetch 차단), IOC 값 없음
- 네트워크 범위 확인: unit42.paloaltonetworks.com, thedfirreport.com, silentpush.com, hunt.io, securelist.com, recordedfuture.com, msrc.microsoft.com — 이번 실행에서 재시도, 전부 차단 확인 (ENOTFOUND). cloud.google.com 특정 기사 URL은 이번 실행에서도 재차 전체 본문 확보 성공 (2022년 기존 자료, 신규 내용 없음).

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
- [Google Cloud / GCTI — "Making Cobalt Strike harder for threat actors to abuse"](https://cloud.google.com/blog/products/identity-security/making-cobalt-strike-harder-for-threat-actors-to-abuse) — 2022-11-18 — fetched (재확인)
- unit42.paloaltonetworks.com/cobalt-strike-team-server/ — 2026-11-15 — blocked (ENOTFOUND)
- unit42.paloaltonetworks.com/attackers-exploit-public-cobalt-strike-profiles/ — 2026-11-15 — blocked (ENOTFOUND)
- thedfirreport.com/2025/01/27/cobalt-strike-and-a-pair-of-socks-lead-to-lockbit-ransomware/ — 2026-11-15 — blocked (ENOTFOUND)
- thedfirreport.com/?p=48447 (Lunar Spider) — 2026-11-15 — blocked (ENOTFOUND)
- www.silentpush.com/blog/gentlemen-ransomware/ — 2026-11-15 — blocked (ENOTFOUND)
- hunt.io/blog/rare-watermark-links-cobalt-strike-team-servers-to-ongoing-suspicious-activity — 2026-11-15 — blocked (ENOTFOUND)
- securelist.com/strikeshark-campaign/120326/ — 2026-11-15 — blocked (ENOTFOUND)
- www.recordedfuture.com/research/2025-year-in-review-malicious-infrastructure — 2026-11-15 — blocked (ENOTFOUND)
- msrc.microsoft.com/blog/2022/10/hunting-for-cobalt-strike-mining-and-plotting-for-fun-and-profit — 2026-11-15 — blocked (ENOTFOUND)
