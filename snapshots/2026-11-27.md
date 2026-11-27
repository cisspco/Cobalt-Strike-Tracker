# Cobalt Strike Snapshot — 2026-11-27 UTC

## 수집 상태
- 페치 성공: cloud.google.com/blog/topics/threat-intelligence (신규 CS 콘텐츠 없음); www.microsoft.com/en-us/security/blog/?s=cobalt+strike (신규 CS 콘텐츠 없음, 2021 Solorigate/TEARDROP 글이 여전히 최상단)
- 페치 차단: securityarsenal.com, security.com (www/비-www 둘 다), www.zscaler.com, www.techradar.com, assets.recordedfuture.com (5개 모두 ENOTFOUND, 이번 실행 신규 시도)
- 검증: 누적 변경 없음 / 미검증: 2건 추가 (컨텍스트 전용, IOC 아님) / 검토 필요: 49건 (3건 추가)

## 최근 캠페인 (최근 60일)

캠페인 수준의 전적으로 새로운 보고는 이번 실행에서도 없음 (40일 연속 조용한 날, 스트릭: 2026-10-13 ~ 2026-11-26). 6개 필수 검색 쿼리는 대부분 기존에 기록된 캠페인/IOC만 재노출했으나, 두 건의 새로운 컨텍스트가 확인됨(둘 다 IOC 수준 미검증):

1. **Devmine 스푸핑 도메인 침해 (공격자 미귀속)** — security.com 보고(2026-03~07, 페치 차단, 검색 스니펫만). 아시아 기술 스타트업을 침해한 공격자가 AdaptixC2 에이전트와 Cobalt Strike Beacon을 반복 배포 시도했으나 대부분 피해 네트워크에서 차단됨. 초기 침투는 ClickFix → PowerShell. 2026-06-08 AdaptixC2 에이전트가 AI 소프트웨어 개발사 "Devmine"을 스푸핑한 C2 도메인("datalyerservice") 사용. 2026-06-19 `thread_indirect.exe`로 위장한 Cobalt Strike Beacon 배포. 구체적 IP/도메인/해시/워터마크 없음 — 컨텍스트만 기록.
2. **SNOWLIGHT/China-nexus — 구체적 IP 확인 (여전히 미검증)** — securityarsenal.com OTX-pulse 분석(2026-08-04, 페치 차단)이 CVE-2025-24813을 악용하는 중국계 "spray-and-check" 캠페인(크랙판 중국어 Cobalt Strike 재구현체 "GoCobaltStrike" 사용, 기존에 이미 기록된 SNOWLIGHT와 동일 선상)의 핵심 인프라로 130.94.17[.]180 / 130.94.30[.]168, 클라우드 호스팅 노드로 149.129.37[.]105 명시. 130.94.30[.]168은 SOCRadar의 SNOWLIGHT 보고서(China-nexus UNC5174/UNC6586, GTIG 추적)에서도 동일하게 전달 호스트로 지목되어 2개 독립 출처 간 교차 확인됨(둘 다 미페치). 다만 "GoCobaltStrike"는 정식 Cobalt Strike가 아닌 재구현체로 명시되어 있어, 본 트래커의 "Cobalt Strike 자체 확인" 기준을 명확히 만족하지 못함 — 차단 대상 아님, `iocs/needs-review.txt`에만 3건 추가.

기타 재확인된 기존 캠페인: StrikeShark/SharkLoader, The Gentlemen/CountLoader(워터마크 1473793097/1357776117, C2 91.107.247[.]163), Nitrogen 랜섬웨어, Aur0ra 랜섬웨어, Storm-0501/Embargo — 모두 기존과 동일, 신규 내용 없음.

## 공격자 C2 팀서버 (차단 대상) (6)
- 108.61.242[.]65 — KnowledgeDeliver/CVE-2026-5426 또는 BlackByte 관련 검증된 캠페인 C2 — verified
- 109.206.243[.]59 — 상동 — verified
- 146.70.78[.]43 — 상동 — verified
- 45.150.108[.]213 — 상동 — verified
- 87.120.254[.]39 — 상동 — verified
- 92.204.160[.]240 — 상동 — verified

(도메인 없음)

## 검토 필요 — 스캐너 탐지만 된 팀서버 (차단 금지) (49)
- 신규 3건 추가: 130.94.17[.]180, 130.94.30[.]168, 149.129.37[.]105 — SNOWLIGHT/China-nexus "spray-and-check" 캠페인(GoCobaltStrike 재구현체) 관련 미페치·단일/이중 소스 귀속, "정식 Cobalt Strike 확인" 기준 미충족으로 차단 보류. 나머지 46건은 변경 없음. 상세는 `iocs/needs-review.txt` 참조.

## JARM 헌팅 신호 (차단 용도 아님) (3)
- 변경 없음. `07d14d16d21d21d00042d41d00041de5fb3038104f457d92ba02e9311512c2`, `07d14d16d21d21d07c42d41d00041d24a458a375eef0c576d23a7bab9a9fb1`, `2ad2ad16d2ad2ad00042d42d00042ddb04deffa1705e2edc44cae1ed24a4da` — 모두 일반 헌팅 신호, 캠페인 특정 아님.

## 워터마크 · 맬리어블 프로파일
- **0 / 1** — 크랙판 공통값, 차단 신호 아님 (LOW SIGNAL)
- **100000000 / 666666666 / 987654321 / 678358251 / 688983459** — 크랙판/공유 클러스터 값, 개별 캠페인 귀속 없음 또는 약한 귀속, 차단 신호로 사용 금지.
- **1473793097 / 1357776117** — "The Gentlemen"/CountLoader 체인 특정 값 (미검증, Silent Push)
- **BeudtKgqnlm0Ruvf+VYxuw==** — APT24 특정 워터마크 해시 (검증됨, Mandiant)
- **666** — Storm-0501 고유 변조 워터마크 (검증됨, Microsoft, 2024-09-26)
- Manatee Tempest/EvilCorp — Cobalt Strike 로더 공급자 역할 (검증됨, Microsoft, IOC 값 없음)
- **신규 (미검증, 컨텍스트만)**: Devmine 스푸핑 도메인 침해(AdaptixC2+CS Beacon, 공격자 미귀속); SNOWLIGHT/China-nexus GoCobaltStrike 캠페인의 구체적 IP 3건(위 참조, 차단 대상 아님)
- 전체 목록은 `iocs/watermarks-and-profiles.md` 참조 (누적, 이번 실행 2건 추가)

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
- Cobalt Strike Beacon이 `thread_indirect.exe`로 위장 (Devmine 스푸핑 침해, 미검증, DB 서버 프로세스로 오인시키는 의도로 추정)
- 팀서버 기본 TCP 50050 포트, 기본 spawn_to `rundll32.exe`, 기본 차단 User-Agent curl/wget (Mandiant 팀서버 아키텍처 참조 문서, 재확인)
- 자세한 내용은 `iocs/watermarks-and-profiles.md` 참조

## 이번 실행 변경사항
- 신규 C2 (검증, 차단 대상): 없음
- 신규 C2 (미검증, 차단 대상 아님): 없음
- 신규 해시: 없음
- 승격(미검증→검증): 없음
- 분류 변경: 없음
- 검토 필요 신규 추가: 3건 (130.94.17.180, 130.94.30.168, 149.129.37.105 — SNOWLIGHT/China-nexus, GoCobaltStrike 재구현체 캐비엇)
- 신규 JARM 후보: 없음
- 신규 워터마크/배경 귀속 노트: 2건 추가 (Devmine/AdaptixC2 침해, SNOWLIGHT IP 보강) — 둘 다 IOC 아님, 컨텍스트만
- 네트워크 범위 확인: 이번 실행에서 신규 시도한 5개 도메인(securityarsenal.com, security.com, www.zscaler.com, www.techradar.com, assets.recordedfuture.com) 모두 ENOTFOUND로 신규 차단 확인. 1차 출처 접근 가능 도메인은 여전히 microsoft.com, cloud.google.com 뿐으로 재확인됨. 40번째 연속 조용한 날 (검증된 공격자 C2/캠페인 수준 신규 발견 없음, 스트릭: 2026-10-13 ~ 2026-11-26).

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
- [Google Cloud Blog — Threat Intelligence](https://cloud.google.com/blog/topics/threat-intelligence) — 2026-11-27 — fetched (신규 CS 콘텐츠 없음)
- [Microsoft Security Blog search: cobalt strike](https://www.microsoft.com/en-us/security/blog/?s=cobalt+strike) — 2026-11-27 — fetched (신규 CS 콘텐츠 없음, 최상단은 2021년 Solorigate/TEARDROP)
- [Security Arsenal — China-nexus spray-and-check campaign (GoCS/SNOWLIGHT/Neo-Regeorg)](https://securityarsenal.com/blog/china-nexus-spray-and-check-campaign-gocs-snowlight-neo-regeorg-infrastructure-otx-pulse-analysis) — 2026-08-04 — blocked (ENOTFOUND, 신규 시도)
- [Security.com — Node.js: Old Technique Makes a Comeback](https://www.security.com/blog-post/node-js-returns-ransomware) — 2026 — blocked (ENOTFOUND, 신규 시도, www/비-www 둘 다)
- [Zscaler — Tropic Trooper pivots AdaptixC2 and custom Beacon listener](https://www.zscaler.com/blogs/security-research/tropic-trooper-pivots-adaptixc2-and-custom-beacon-listener) — 2026 — blocked (ENOTFOUND, 신규 시도)
- [TechRadar Pro — Chinese organizations hit by Cobalt Strike malware from within China](https://www.techradar.com/pro/security/chinese-organizations-are-being-hit-by-cobalt-strike-malware-from-within-china) — 2026 — blocked (ENOTFOUND, 신규 시도)
- [Recorded Future Insikt — CTA-CN-2025-0924 PDF](https://assets.recordedfuture.com/insikt-report-pdfs/2025/cta-cn-2025-0924.pdf) — 2025 — blocked (ENOTFOUND, 신규 시도, recordedfuture.com 레지스터블 도메인 전체 차단 확인)
