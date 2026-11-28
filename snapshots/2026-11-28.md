# Cobalt Strike Snapshot — 2026-11-28 UTC

## 수집 상태
- 페치 성공: cloud.google.com/security/resources/m-trends-executive-edition (JS 렌더링, 본문 텍스트 추출 안 됨); www.microsoft.com/security/blog/?p=86932 (2018년 YTTRIUM/APT29 스피어피싱 글, 신규 CS 콘텐츠 아님)
- 페치 차단: thedfirreport.com, sophos.com, www.recordedfuture.com, unit42.paloaltonetworks.com (4개 모두 ENOTFOUND, 이번 실행 신규 확인 — 프롬프트가 지정한 "untested" 목록 전부 차단 확인됨)
- 검증: 누적 변경 없음 / 미검증: 0건 (신규 IOC 값 없음) / 검토 필요: 51건 (2건 추가)

## 최근 캠페인 (최근 60일)

캠페인 수준의 전적으로 새로운 보고는 이번 실행에서도 없음 (41일 연속 조용한 날, 스트릭: 2026-10-13 ~ 2026-11-27). 6개 필수 검색 쿼리는 모두 기존에 기록된 캠페인/IOC만 재노출함 (The Gentlemen/CountLoader, SNOWLIGHT/GoCobaltStrike, StrikeShark/SharkLoader, Nitrogen, Aur0ra, Storm-0501/Embargo).

이번 실행에서 처음 접근을 시도한 www.microsoft.com/security/blog/?p=86932가 성공적으로 페치됨: 2018-12-03 Microsoft Defender Security Research Team 글로, 미국 싱크탱크/비영리단체를 겨냥한 OneDrive 테마 스피어피싱 캠페인을 다루며 2단계 페이로드로 Cobalt Strike를 사용(제3자 연구자들이 APT29/CozyBear로 연결, Microsoft 자체 YTTRIUM 귀속은 미확정). SHA-1 해시, 도메인 pandorasong[.]com, IP 95.216.59.92 확인됨 — 그러나 8년 전 자료이고 해시가 SHA-1(본 트래커는 SHA-256만 기록)이며 인프라가 거의 확실히 재할당되었을 것으로 판단되어, 기존에 ~5년 지난 UNC2628/DarkSide 2021 인프라를 처리한 방식과 동일하게 **어떤 IOC 파일에도 추가하지 않음** — 참고용 기록만 남김 (`iocs/watermarks-and-profiles.md` 참조).

## 공격자 C2 팀서버 (차단 대상) (6)
- 108.61.242[.]65 — KnowledgeDeliver/CVE-2026-5426 또는 BlackByte 관련 검증된 캠페인 C2 — verified
- 109.206.243[.]59 — 상동 — verified
- 146.70.78[.]43 — 상동 — verified
- 45.150.108[.]213 — 상동 — verified
- 87.120.254[.]39 — 상동 — verified
- 92.204.160[.]240 — 상동 — verified

(도메인 없음)

## 검토 필요 — 스캐너 탐지만 된 팀서버 (차단 금지) (51)
- 신규 2건 추가: 8.152.2[.]86, 158.247.194[.]144 — SocRadar IOC Radar 피드가 "Cobalt Strike" 악성코드 패밀리로 태깅(고신뢰도), 캠페인/공격자 귀속 없음 — 스캐너/피드 분류만, 차단 금지. 나머지 49건은 변경 없음. 상세는 `iocs/needs-review.txt` 참조.

## JARM 헌팅 신호 (차단 용도 아님) (3)
- 변경 없음. `07d14d16d21d21d00042d41d00041de5fb3038104f457d92ba02e9311512c2`, `07d14d16d21d21d07c42d41d00041d24a458a375eef0c576d23a7bab9a9fb1`, `2ad2ad16d2ad2ad00042d42d00042ddb04deffa1705e2edc44cae1ed24a4da` — 모두 일반 헌팅 신호, 캠페인 특정 아님.

## 워터마크 · 맬리어블 프로파일
- **0 / 1** — 크랙판 공통값, 차단 신호 아님 (LOW SIGNAL)
- **100000000 / 666666666 / 987654321 / 678358251 / 688983459** — 크랙판/공유 클러스터 값, 개별 캠페인 귀속 없음 또는 약한 귀속, 차단 신호로 사용 금지.
- **1473793097 / 1357776117** — "The Gentlemen"/CountLoader 체인 특정 값 (미검증, Silent Push)
- **BeudtKgqnlm0Ruvf+VYxuw==** — APT24 특정 워터마크 해시 (검증됨, Mandiant)
- **666** — Storm-0501 고유 변조 워터마크 (검증됨, Microsoft, 2024-09-26)
- Manatee Tempest/EvilCorp — Cobalt Strike 로더 공급자 역할 (검증됨, Microsoft, IOC 값 없음)
- 이번 실행 신규 워터마크/프로파일 값 없음. 2018년 YTTRIUM/APT29 글은 참고 기록만 남김 (IOC 아님).
- 전체 목록은 `iocs/watermarks-and-profiles.md` 참조 (누적)

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

(2018년 YTTRIUM/APT29 글의 4개 SHA-1 해시는 본 트래커 형식상 제외됨 — SHA-256만 기록)

## 호스트 IOC · 행위
- SMB BEACON named pipe `\\.\pipe\UIA_PIPE_*` (UNC2628/DarkSide)
- DNS BEACON 서브도메인 패턴 `h.dns.<C2 domain>`, `ridoj4.<8자>.dns.<C2 domain>` 등 (UNC4393/BASTA)
- Beacon이 `rundll32.exe`(.dll)/`regsvr32.exe`(.ocx)로 실행됨 (Storm-0501)
- Cobalt Strike Beacon이 `thread_indirect.exe`로 위장 (Devmine 스푸핑 침해, 미검증)
- 팀서버 기본 TCP 50050 포트, 기본 spawn_to `rundll32.exe`, 기본 차단 User-Agent curl/wget (Mandiant 팀서버 아키텍처 참조 문서)
- 자세한 내용은 `iocs/watermarks-and-profiles.md` 참조

## 이번 실행 변경사항
- 신규 C2 (검증, 차단 대상): 없음
- 신규 C2 (미검증, 차단 대상 아님): 없음
- 신규 해시: 없음
- 승격(미검증→검증): 없음
- 분류 변경: 없음
- 검토 필요 신규 추가: 2건 (8.152.2.86, 158.247.194.144 — SocRadar IOC Radar 피드, 스캐너 분류만)
- 신규 JARM 후보: 없음
- 신규 워터마크/배경 귀속 노트: 1건 추가 (2018 YTTRIUM/APT29 참고 기록, IOC 아님)
- 네트워크 범위 확인: 프롬프트가 지정한 "untested" 4개 도메인(thedfirreport.com, sophos.com, recordedfuture.com, unit42.paloaltonetworks.com) 전부 ENOTFOUND로 신규 차단 확인됨 — 더 이상 "untested" 목록에 남은 후보 없음. 1차 출처 접근 가능 도메인은 여전히 microsoft.com, cloud.google.com 뿐으로 재확인됨. 41번째 연속 조용한 날 (검증된 공격자 C2/캠페인 수준 신규 발견 없음, 스트릭: 2026-10-13 ~ 2026-11-27).

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
- [Microsoft Security Blog — spear-phishing campaign (2018-12-03)](https://www.microsoft.com/security/blog/?p=86932) — 2018-12-03 — fetched (2018년 캠페인, 신규 IOC 미채택)
- [Google Cloud — M-Trends 2026 Executive Edition](https://cloud.google.com/security/resources/m-trends-executive-edition) — 2026 — fetched (JS 렌더링, 본문 없음)
- [The DFIR Report — Cobalt Strike and a Pair of SOCKS Lead to LockBit Ransomware](https://thedfirreport.com/?p=41604) — 2025-01-27 — blocked (ENOTFOUND, 신규 확인)
- [Sophos — AI used in Aur0ra ransomware testing and execution](https://sophos.com/en-us/blog/ai-used-in-aur0ra-ransomware-testing-and-execution) — 2026 — blocked (ENOTFOUND, 신규 확인)
- [Recorded Future — 2025 Year in Review: Malicious Infrastructure](https://www.recordedfuture.com/research/2025-year-in-review-malicious-infrastructure) — 2025 — blocked (ENOTFOUND, 신규 확인)
- [Unit 42 — Cobalt Strike Team Server](https://unit42.paloaltonetworks.com/cobalt-strike-team-server/) — N/A — blocked (ENOTFOUND, 신규 확인)
- [SocRadar IOC Radar — Cobalt Strike](https://socradar.io/free-tools/ioc-radar/malware/cobalt-strike) — 2026-07 — search-snippet only (socradar.io, known-blocked)
