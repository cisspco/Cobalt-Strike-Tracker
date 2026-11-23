# Cobalt Strike Snapshot — 2026-11-23 UTC

## 수집 상태
- 페치 성공: 없음 (이번 실행에서는 신규 콘텐츠 페치 성공 없음 — cloud.google.com/microsoft.com에 대한 site: 검색만 수행, 신규 기사 없어 추가 페치 생략)
- 페치 차단: unit42.paloaltonetworks.com, thedfirreport.com, www.recordedfuture.com, assets.recordedfuture.com, www.silentpush.com, www.group-ib.com (모두 ENOTFOUND로 신규 확인 — "UNTESTED" 목록에 있던 5개 도메인을 이번 실행에서 처음 시도했고 전부 차단 확인됨; 기존 알려진 차단 목록과 동일한 패턴)
- 검증: 누적 변경 없음 / 미검증: 누적 변경 없음 / 검토 필요: 46건 (변경 없음)

## 최근 캠페인 (최근 60일)

캠페인 수준의 전적으로 새로운 보고는 이번 실행에서도 없음 (37일 연속 조용한 날, 스트릭: 2026-10-13 ~ 2026-11-23). 6개 필수 검색 쿼리는 모두 기존에 기록된 캠페인/IOC만 재노출함: StrikeShark/SharkLoader(Securelist/Gurucul, 2026-06), The Gentlemen/CountLoader(Silent Push·Check Point, 2026-02~04, 워터마크 1473793097/1357776117, C2 91.107.247[.]163 — 기존과 동일 미검증), Nitrogen 랜섬웨어(2026-09), SNOWLIGHT/GoCobaltStrike(SOCRadar, 2026-04~06), Aur0ra 랜섬웨어(Sophos, 2026-08). 추가로 이번 실행 검색에서 Microsoft가 보고한 호텔/숙박업 대상 "Photo ZIP" 캠페인(2026-04~, microsoft.com/en-us/security/blog/2026/06/25)을 확인했으나, 해당 캠페인의 최종 페이로드는 TONResolver(Node.js 기반 RAT)이며 Cobalt Strike는 보고서에 언급되지 않아 이 트래커의 수집 대상(Cobalt Strike가 체인의 확인된 구성요소인 경우)에서 제외함. 신규 캠페인명, 신규 공격자 귀속 C2, 신규 해시, 신규 워터마크 값 없음.

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
- 네트워크 범위 확인: 이번 실행에서 "UNTESTED" 목록의 5개 도메인(unit42.paloaltonetworks.com, thedfirreport.com, recordedfuture.com 및 그 서브도메인 assets.recordedfuture.com, silentpush.com, group-ib.com)을 처음으로 시도 — 전부 ENOTFOUND로 차단 확인됨. 이 트래커가 장기적으로 1차 출처에 접근할 수 있는 도메인은 여전히 microsoft.com, cloud.google.com 뿐으로 확인됨. 37번째 연속 조용한 날 (검증된 공격자 C2/캠페인 수준 신규 발견 없음, 스트릭: 2026-10-13 ~ 2026-11-23).

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
- [Microsoft Security Blog — Photo ZIP campaign targeting hospitality industry](https://microsoft.com/en-us/security/blog/2026/06/25/photo-zip-campaign-targeting-hospitality-industry-delivers-node-js-implant-persistent-access) — 2026-06-25 — 검토함, Cobalt Strike 미언급으로 제외
- [Unit 42 — Cobalt Strike malleable C2](https://unit42.paloaltonetworks.com/cobalt-strike-malleable-c2/) — 2026-11-23 — blocked (ENOTFOUND)
- [The DFIR Report — Cobalt Strike and a Pair of SOCKS Lead to LockBit](https://thedfirreport.com/2024/12/09/cobalt-strike-and-a-pair-of-socks-lead-to-lockbit-ransomware/) — 2026-11-23 — blocked (ENOTFOUND)
- [Recorded Future — RedNovember targets government, defense and technology organizations](https://www.recordedfuture.com/research/rednovember-targets-government-defense-and-technology-organizations) — 2026-11-23 — blocked (ENOTFOUND)
- [Recorded Future Insikt — CTA-2026-0319](https://assets.recordedfuture.com/insikt-report-pdfs/2026/cta-2026-0319.pdf) — 2026-11-23 — blocked (ENOTFOUND)
- [Silent Push — No Place to Hide (The Gentlemen)](https://www.silentpush.com/blog/gentlemen-ransomware/) — 2026-11-23 — blocked (ENOTFOUND)
- [Group-IB — Stray Cat at the Network Edge](https://www.group-ib.com/blog/stray-cat-network-edge/) — 2026-11-23 — blocked (ENOTFOUND)
