# Cobalt Strike Snapshot — 2026-09-03 UTC

## 수집 상태
- 페치 성공: cloud.google.com/blog (BREEZE COMET, UNC4393/SILENTNIGHT, M-Trends 2026 Executive Edition — 일부 잘림), microsoft.com (WDSI threat-search)
- 페치 차단: securelist.com, www.techtarget.com, hunt.io, unit42.paloaltonetworks.com
- 검증: 1 / 미검증: 4 / 검토 필요: 0

이번 실행은 첫 실행(run 1)으로 시드 데이터가 없습니다. 우선순위 소스(Talos, TheHackerNews, BleepingComputer, CISA 등)는 egress 프록시로 차단되어 있고, 신규로 시도한 securelist.com / techtarget.com / hunt.io / unit42.paloaltonetworks.com도 모두 차단되었습니다. Google Cloud(Mandiant)와 Microsoft 도메인만 접근 가능했습니다. 그 결과 검증된 신규 공격자 C2 도메인/IP는 없습니다 — 조용한 실행(quiet day)입니다.

## 최근 캠페인 (최근 60일)

### UNC4393 / BASTA 랜섬웨어 — Cobalt Strike BEACON이 침투 전 과정에 편재
- 대상: 20개 이상 산업군, 2024년 이후 헬스케어 비중 증가; BASTA 데이터 유출 사이트에 500+ 피해자 주장, Mandiant가 40+ 침해 조사
- 초기 침투: QAKBOT(UNC2633/UNC2500) 피싱, DARKGATE(UNC2500) 피싱, SILENTNIGHT 백도어(UNC5155) 멀버타이징, 또는 외부 노출 장비 대상 탈취 자격증명/무차별 대입
- Cobalt Strike 역할: DNS BEACON으로 거점 확보 → SMB BEACON으로 횡적 이동 → WMI로 100개 이상 시스템에 명령 실행/도구 배포 → BASTA 랜섬웨어 실행까지 주요 C2 채널로 지속 사용
- 관측 시점: Mandiant 보고서 게재일 2024-07 (그룹 자체는 이후에도 지속 활동 중인 것으로 알려짐 — 이번 실행에서 최신 활동 재확인은 못함, 최근 60일 신규 관측 아님을 명시)
- 출처: Mandiant/Google Cloud Blog "UNC4393 Goes Gently into the SILENTNIGHT" — fetched, verified

### StrikeShark — 커스텀 SharkLoader + Cobalt Strike Beacon ⚠️ (미검증)
- Securelist(Kaspersky) 기사(ID 120326)가 신규 SharkLoader 로더와 Cobalt Strike Beacon을 결합한 캠페인을 다룬다고 검색 스니펫에서 확인됨
- 정확한 대상/침투 경로/C2/해시는 원문 페치가 차단되어 확인 불가
- 출처: securelist.com/strikeshark-campaign/120326/ — blocked, unverified

### 구직자 대상 피싱 (미국·뉴질랜드) — CVE-2017-0199 → 유출판 Cobalt Strike ⚠️ (미검증)
- 정부/노동조합 채용 사칭 피싱 이메일 → 악성 Word 문서 → CVE-2017-0199 익스플로잇 → 스크립트 체인 → Cobalt Strike Beacon 설치 (일부 피해자는 RedLine 또는 Amadey로 대체 감염)
- 정확한 관측 월/피해 규모/C2는 원문 페치가 차단되어 확인 불가; 검색 스니펫 기반이며 과거 유사 보도(2023년경 Talos)와 동일 캠페인의 재보도일 가능성 있음 — 추가 검증 필요
- 출처: techtarget.com — blocked, unverified

## 공격자 C2 팀서버 (차단 대상) (0)
- 이번 실행에서 특정 악성 캠페인/행위자에 명시적으로 귀속된 신규 팀서버 도메인·IP 없음

## 검토 필요 — 스캐너 탐지만 된 팀서버 (차단 금지) (0)
- 이번 실행에서 신규 항목 없음

## JARM 헌팅 신호 (차단 용도 아님)
- 07d14d16d21d21d00042d41d00041de5fb3038104f457d92ba02e9311512c2 — Cobalt Strike 팀서버 기본(OpenJDK 11) JARM으로 공개적으로 널리 문서화된 값. 정상 서비스도 동일 JARM을 가질 수 있어 헌팅/피벗 용도로만 사용 — ⚠️ (미검증, 페치 차단으로 원문 확인 불가)

## 워터마크 · 맬리어블 프로파일
- 워터마크 0 — 크랙판 공통 기본값. 수천 개의 무관한 행위자가 공유하는 값으로 그 자체는 차단/귀속 신호가 아님
- 워터마크 1 — 크랙/유출판에서 흔히 관측되는 값. 마찬가지로 단독으로는 귀속 신호 아님
- 워터마크 678358251 — Black Basta 등 다수 행위자와의 연관이 보고됨 ⚠️ (미검증, hunt.io 페치 차단, 검색 스니펫 기반)
- UNC4393/BASTA DNS Beacon 서브도메인 명명 패턴 (맬리어블 프로파일 특성, Mandiant 검증) — `h.dns.<C2도메인>`, `ridoj4.<8자리문자열>.dns.<C2도메인>`, `jzz.<8자리문자열>.dns.<C2도메인>`, `wnh.<8자리문자열>.dns.<C2도메인>`. 탐지 콘텐츠로만 사용 — 도메인 자체가 아니라 명명 패턴임에 유의

## 파일 해시 (0)
- 이번 실행에서 Cobalt Strike 자체(로더/비콘/스테이저)로 확인된 신규 해시 없음. BREEZE COMET 및 UNC4393 보고서에서 언급된 해시는 각각 자체 개발 프레임워크(XWORM/COBALTSPIN 등) 및 BASTA 랜섬웨어/보조 도구로, Cobalt Strike 자체 구성요소가 아니어서 제외함

## 호스트 IOC · 행위
- UNC4393: SMB BEACON을 통한 내부망 횡적 이동, WMI를 이용한 100개 이상 시스템에 대한 원격 명령 실행/도구 전개 — Mandiant 검증

## 이번 실행 변경사항
- 신규 C2: 없음
- 신규 해시: 없음
- 승격(미검증→검증): 없음 (첫 실행)
- 분류 변경: 없음 (첫 실행, 시드 없음)

## 차단 운영 포맷 (복붙용)

### Domain/IP blocklist (un-defanged, one per line — attributed attacker C2 only)
```
(이번 실행 기준 귀속된 항목 없음)
```

## 출처
- [UNC4393 Goes Gently into the SILENTNIGHT](https://cloud.google.com/blog/topics/threat-intelligence/unc4393-goes-gently-into-silentnight) — 2024-07-29 — fetched
- [Financially Motivated Threat Actor BREEZE COMET Targets Brazil](https://cloud.google.com/blog/topics/threat-intelligence/financially-motivated-threat-actor-breeze-comet-targets-brazil) — 2026-09-01 — fetched (Cobalt Strike 미언급, 참고용)
- [M-Trends 2026 Report: Executive Edition](https://cloud.google.com/security/resources/m-trends-executive-edition) — 2026 — fetched (내용 잘림, 활용 제한적)
- [Microsoft Security Intelligence — CobaltStrike threat search](https://www.microsoft.com/en-us/wdsi/threats/threat-search?query=CobaltStrike) — fetched (일반 정보만, 신규 IOC 없음)
- [StrikeShark campaign — Securelist](https://securelist.com/strikeshark-campaign/120326/) — blocked
- [Cobalt Strike malware campaign targets job seekers — TechTarget](https://www.techtarget.com/searchsecurity/news/252525560/Cobalt-Strike-malware-campaign-targets-job-seekers) — blocked
- [Rare Watermark Links Cobalt Strike 4.10 Team Servers — hunt.io](https://hunt.io/blog/rare-watermark-links-cobalt-strike-team-servers-to-ongoing-suspicious-activity) — blocked
- [Attackers Exploiting Public Cobalt Strike Profiles — Unit 42](https://unit42.paloaltonetworks.com/attackers-exploit-public-cobalt-strike-profiles/) — blocked
