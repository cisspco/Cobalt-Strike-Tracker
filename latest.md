# Cobalt Strike Snapshot — 2026-11-11 UTC

## 수집 상태
- 페치 성공: cloud.google.com/blog/topics/threat-intelligence (신규 Cobalt Strike 콘텐츠 없음 — 최신 게시물 2건 모두 무관: "Shutting the Door on the XCPE Botnet", "ARTEX and Friends: Enter Agentic Offensive Frameworks"), www.microsoft.com/en-us/security/blog (검색, 신규 콘텐츠 없음 — 2021년 Solorigate/TEARDROP 게시물만 재노출)
- 페치 차단(신규 시도, 이번 실행에서 최초로 차단 확인): www.darktrace.com, redcanary.com, www.trellix.com, community.advania.co.uk, www.securitylab.ru, cybercentaurs.com — 모두 ENOTFOUND
- 페치 차단(기존 목록, 재확인 없음): thehackernews.com, medium.com, securityweek.com, bleepingcomputer.com, socradar.io, unit42.paloaltonetworks.com 등 기존 차단 도메인 리스트 그대로 (이번 실행 미시도)
- 검증: 누적 9건 (C2 IP 6 + 해시 2 + GCTI 크랙판 배경자료 1) / 미검증: 누적 6건 (C2 IP 1 + 도메인 5) / 검토 필요: 46

## 최근 캠페인 (최근 60일)

캠페인 수준의 전적으로 새로운 보고는 이번 실행에서도 없음 (2026-10-13 이후 지속, 29일 연속 조용한 날 — 차단 대상 기준). 다만 검색 스니펫에서 5건의 신규(미검증) 공격 기법/귀속 단서가 노출됨 — 구체적 IOC(IP/도메인/해시) 값은 없어 차단 목록에는 반영하지 않음:

- **SNOWLIGHT** (중국계) — 크랙판 중국산 Cobalt Strike 재구현체 "GoCobaltStrike" 사용, 정부 인프라 대상. 출처: socradar.io (차단됨, 스니펫만).
- **Aur0ra 랜섬웨어** — AI 지원 테스트/실행 인프라가 Cobalt Strike도 호스팅했다고 Sophos 보고 (스니펫만, 미페치).
- **가짜 KeePass 설치파일 → ESXi 랜섬웨어** — WithSecure가 관측한 워터마크를 Black Basta 연계 IAB(Initial Access Broker)에 연결 (출처 bleepingcomputer.com, 차단됨).
- **Bumblebee → Cobalt Strike** — Darktrace의 침해 체인 분석 글, Bumblebee 로더가 Cobalt Strike를 후속 페이로드로 전달 (darktrace.com, 이번 실행에서 신규 차단 확인).
- **FrostBeacon** (Seqrite) — 러시아 B2B 기업 대상, 2025-11부터 활동 — 60일 기준 초과, 배경 정보로만 기록.

- 참고(재확인, 변경 없음): Silver Dragon, UNG0002(Dragon Whistle/Cobalt Whisper/AmberMist), StrikeShark/SharkLoader, The Gentlemen/CountLoader(이번 실행 Check Point DFIR 보고서로 C2 IP 91.107.247.163 2차 귀속 — 여전히 미검증), Ghostwriter, RedNovember — 이번 실행 검색에서 재노출, 상세 변경 없음.

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
- 이번 실행에서 두 값 모두 재확인(RST Cloud, HiveSecurity 스니펫) — 신규 변경 없음.

## 워터마크 · 맬리어블 프로파일
- **0 / 1** — 크랙판 공통값, 차단 신호 아님 (LOW SIGNAL)
- **100000000 / 666666666 / 987654321 / 678358251 / 688983459** — 크랙판/공유 클러스터 값, 개별 캠페인 귀속 없음 또는 약한 귀속, 차단 신호로 사용 금지.
- **1473793097 / 1357776117** — "The Gentlemen"/CountLoader 체인 특정 값 (미검증, Silent Push)
- **BeudtKgqnlm0Ruvf+VYxuw==** — APT24 특정 워터마크 해시 (검증됨, Mandiant)
- 전체 목록 및 이번 실행 신규 미검증 캠페인 노트(SNOWLIGHT, Aur0ra, KeePass/Black Basta IAB, Bumblebee, FrostBeacon)는 `iocs/watermarks-and-profiles.md` 참조 (누적)

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
- 신규 미검증 캠페인/기법 노트 추가: SNOWLIGHT/GoCobaltStrike, Aur0ra 랜섬웨어, KeePass→ESXi/Black Basta IAB 워터마크, Bumblebee→Cobalt Strike, FrostBeacon (IOC 값 없음, `iocs/watermarks-and-profiles.md`에만 기록)
- 네트워크 범위 확인: www.darktrace.com, redcanary.com, www.trellix.com, community.advania.co.uk, www.securitylab.ru, cybercentaurs.com — 이번 실행에서 신규로 차단 확인 (ENOTFOUND)

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
- [Google Cloud — Threat Intelligence Blog](https://cloud.google.com/blog/topics/threat-intelligence) — 2026-11-11 — fetched (신규 CS 콘텐츠 없음)
- [Microsoft Security Blog — "cobalt strike" 검색](https://www.microsoft.com/en-us/security/blog/?s=cobalt+strike) — 2026-11-11 — fetched (신규 CS 콘텐츠 없음)
- www.darktrace.com — 2026-11-11 — blocked (ENOTFOUND, 신규 시도)
- redcanary.com — 2026-11-11 — blocked (ENOTFOUND, 신규 시도)
- www.trellix.com — 2026-11-11 — blocked (ENOTFOUND, 신규 시도)
- community.advania.co.uk — 2026-11-11 — blocked (ENOTFOUND, 신규 시도)
- www.securitylab.ru — 2026-11-11 — blocked (ENOTFOUND, 신규 시도)
- cybercentaurs.com — 2026-11-11 — blocked (ENOTFOUND, 신규 시도)
