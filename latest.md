# Cobalt Strike Snapshot — 2026-11-26 UTC

## 수집 상태
- 페치 성공: cloud.google.com/blog/products/identity-security/making-cobalt-strike-harder-for-threat-actors-to-abuse (2022-11-18 원문, 크랙판 탐지용 YARA 시그니처 배경 설명 — 기존에 이미 반영된 동일 내용, 신규 캠페인/IOC 없음); cloud.google.com/security/resources/m-trends-executive-edition (페이지는 열렸으나 JS 렌더링으로 텍스트 추출 실패 — 내용은 WebSearch 스니펫으로만 확인, 미검증 처리)
- 페치 차단: securelist.com, community.gurucul.com, threatfox.abuse.ch, any.run, services.google.com (5개 모두 ENOTFOUND, 이번 실행 신규 시도)
- 검증: 누적 변경 없음 / 미검증: 1건 추가 (M-Trends 2026 BEACON 순위 하락, IOC 아님) / 검토 필요: 46건 (변경 없음)

## 최근 캠페인 (최근 60일)

캠페인 수준의 전적으로 새로운 보고는 이번 실행에서도 없음 (40일 연속 조용한 날, 스트릭: 2026-10-13 ~ 2026-11-26). 6개 필수 검색 쿼리는 모두 기존에 기록된 캠페인/IOC만 재노출함: StrikeShark/SharkLoader(Securelist/Gurucul, 2026-06), The Gentlemen/CountLoader(Silent Push·Check Point, 2026-02~04, 워터마크 1473793097/1357776117, C2 91.107.247[.]163 — 기존과 동일 미검증), Nitrogen 랜섬웨어(2026-09), SNOWLIGHT/GoCobaltStrike(China-nexus, 기존과 동일), Aur0ra 랜섬웨어(AI 테스트 인프라, 기존과 동일). 새로 확인된 배경 정보 한 건: Google Cloud/Mandiant M-Trends 2026 보고서(2025년 1~12월 Mandiant 조사 기준)에 따르면 Cobalt Strike BEACON이 5년 연속 1위였던 "가장 많이 관측된 악성코드 패밀리" 순위에서 4위로 하락, GOLDVEIN.JAVA 다운로더(신규 1위)와 REDBIKE/Akira 랜섬웨어(2위)에 뒤처짐 — 단 페이지 직접 페치가 JS 렌더링 문제로 텍스트를 추출하지 못해 미검증(WebSearch 스니펫)으로 기록. 신규 캠페인명, 신규 공격자 귀속 C2, 신규 해시, 신규 워터마크 값 없음.

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
- 참고: 이번 실행에서도 신규 JARM 값 없음 (RST Cloud 2026-03 자료가 동일 3개 후보값을 재확인함, 기존과 동일).

## 워터마크 · 맬리어블 프로파일
- **0 / 1** — 크랙판 공통값, 차단 신호 아님 (LOW SIGNAL)
- **100000000 / 666666666 / 987654321 / 678358251 / 688983459** — 크랙판/공유 클러스터 값, 개별 캠페인 귀속 없음 또는 약한 귀속, 차단 신호로 사용 금지.
- **1473793097 / 1357776117** — "The Gentlemen"/CountLoader 체인 특정 값 (미검증, Silent Push)
- **BeudtKgqnlm0Ruvf+VYxuw==** — APT24 특정 워터마크 해시 (검증됨, Mandiant)
- **666** — Storm-0501 고유 변조 워터마크 (검증됨, Microsoft, 2024-09-26)
- Manatee Tempest/EvilCorp — Cobalt Strike 로더 공급자 역할 (검증됨, Microsoft, IOC 값 없음)
- **신규 (미검증)**: M-Trends 2026 — BEACON이 Mandiant 최다 관측 악성코드 5년 연속 1위에서 4위로 하락 (일반 트렌드, IOC 아님)
- 전체 목록은 `iocs/watermarks-and-profiles.md` 참조 (누적, 이번 실행 1건 추가)

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
- 팀서버 기본 TCP 50050 포트, 기본 spawn_to `rundll32.exe`, 기본 차단 User-Agent curl/wget (Mandiant 팀서버 아키텍처 참조 문서, 재확인)
- 자세한 내용은 `iocs/watermarks-and-profiles.md` 참조

## 이번 실행 변경사항
- 신규 C2 (검증, 차단 대상): 없음
- 신규 C2 (미검증, 차단 대상 아님): 없음
- 신규 해시: 없음
- 승격(미검증→검증): 없음
- 분류 변경: 없음
- 검토 필요 신규 추가: 없음
- 신규 JARM 후보: 없음
- 신규 워터마크/배경 귀속 노트: 1건 추가 (M-Trends 2026 BEACON 순위 하락 — IOC 아님, 미검증)
- 네트워크 범위 확인: 이번 실행에서 시도한 6개 URL 중 cloud.google.com 2개(1개는 전문 수집, 1개는 JS 렌더링으로 텍스트 추출 실패)만 접근 가능했고, 나머지 5개(securelist.com, community.gurucul.com, threatfox.abuse.ch, any.run, services.google.com)는 모두 ENOTFOUND로 신규 차단 확인됨. 1차 출처 접근 가능 도메인은 여전히 microsoft.com, cloud.google.com 뿐으로 재확인됨. 40번째 연속 조용한 날 (검증된 공격자 C2/캠페인 수준 신규 발견 없음, 스트릭: 2026-10-13 ~ 2026-11-26).

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
- [Google Cloud Blog — Making Cobalt Strike harder for threat actors to abuse](https://cloud.google.com/blog/products/identity-security/making-cobalt-strike-harder-for-threat-actors-to-abuse) — 2022-11-18 — fetched (기존 수집 자료와 동일, 신규 내용 없음)
- [Google Cloud / Mandiant — M-Trends 2026 Report: Executive Edition](https://cloud.google.com/security/resources/m-trends-executive-edition) — 2026 — fetched (텍스트 추출 실패, JS 렌더링 — WebSearch 스니펫으로만 내용 확인, 미검증)
- [Kaspersky Securelist — StrikeShark Campaign](https://securelist.com/strikeshark-campaign/120326/) — 2026-11-26 — blocked (ENOTFOUND, 신규 시도)
- [Gurucul Community — StrikeShark Investigation](https://community.gurucul.com/articles/ThreatResearch/StrikeShark-Investigating-a-New-25-6-2026) — 2026-11-26 — blocked (ENOTFOUND, 신규 시도)
- [ThreatFox — win.cobalt_strike](https://threatfox.abuse.ch/browse/malware/win.cobalt_strike/) — 2026-11-26 — blocked (ENOTFOUND, 신규 시도)
- [ANY.RUN — Cobalt Strike malware trends](https://any.run/malware-trends/cobaltstrike) — 2026-11-26 — blocked (ENOTFOUND, 신규 시도)
- [Google — M-Trends 2026 Executive Edition PDF](https://services.google.com/fh/files/misc/m-trends-2026-executive-edition-en.pdf) — 2026-11-26 — blocked (ENOTFOUND, 신규 시도)
