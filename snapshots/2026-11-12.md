# Cobalt Strike Snapshot — 2026-11-12 UTC

## 수집 상태
- 페치 성공: cloud.google.com/blog/topics/threat-intelligence (신규 Cobalt Strike 콘텐츠 없음), www.microsoft.com/en-us/security/blog (검색, 신규 콘텐츠 없음 — 2021년 Solorigate/TEARDROP 게시물만 재노출)
- 페치 차단(신규 시도, 이번 실행에서 최초로 차단 확인): hivesecurity.gitlab.io, www.securityscientist.net, s4e.io, hermes-codex.vercel.app, intelinsights.substack.com — 모두 ENOTFOUND
- 페치 차단(기존 확인 도메인 재시도): www.silentpush.com — ENOTFOUND (기존 차단 목록과 일치)
- 검증: 누적 9건 (C2 IP 6 + 해시 2 + GCTI 크랙판 배경자료 1) / 미검증: 누적 6건 (C2 IP 1 + 도메인 5) / 검토 필요: 46

## 최근 캠페인 (최근 60일)

캠페인 수준의 전적으로 새로운 보고는 이번 실행에서도 없음 (2026-10-13 이후 지속, 30일 연속 조용한 날 — 차단 대상 기준). 검색 스니펫에서 2건의 신규(미검증) 단서가 노출되었으나 구체적 IOC 값이 없어 차단 목록에는 반영하지 않음:

- **INCRANSOM 랜섬웨어** — PsExec, Rclone, 쉐도우 카피 삭제 도구와 함께 Cobalt Strike를 사용한다고 보고됨 (securityarsenal.com, ~2026-08, 5일간 10건 피해자 게시). 60일 기준 초과, 구체적 C2 IOC 없음 — 배경 정보로만 기록.
- **Silent Push 2차 Gentlemen 보고서** ("What Recent Reporting Gets Right About The Gentlemen RaaS...") — 기존 C2 IP 91.107.247[.]163 외 추가 귀속 여부 확인 시도, 페치 차단되어 미확인.

- 참고(재확인, 변경 없음): SNOWLIGHT/GoCobaltStrike, Aur0ra 랜섬웨어, 가짜 KeePass→ESXi/Black Basta IAB 워터마크, Bumblebee→Cobalt Strike, FrostBeacon, Silver Dragon, UNG0002(Dragon Whistle/Cobalt Whisper/AmberMist), StrikeShark/SharkLoader, The Gentlemen/CountLoader, Ghostwriter, RedNovember — 이번 실행 검색에서 재노출, 상세 변경 없음.

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
- 참고: 이번 실행 검색 스니펫에서 socat/iptables로 리디렉션된 팀서버용 세 번째 JARM 해시(`2ad2ad16d2ad2ad00042d42d00042d...`)가 언급되었으나 값이 잘려 있고 출처(위키 미러)의 신뢰도가 낮아 기록하지 않음.

## 워터마크 · 맬리어블 프로파일
- **0 / 1** — 크랙판 공통값, 차단 신호 아님 (LOW SIGNAL)
- **100000000 / 666666666 / 987654321 / 678358251 / 688983459** — 크랙판/공유 클러스터 값, 개별 캠페인 귀속 없음 또는 약한 귀속, 차단 신호로 사용 금지.
- **1473793097 / 1357776117** — "The Gentlemen"/CountLoader 체인 특정 값 (미검증, Silent Push)
- **BeudtKgqnlm0Ruvf+VYxuw==** — APT24 특정 워터마크 해시 (검증됨, Mandiant)
- 전체 목록 및 이번 실행 신규 미검증 노트(INCRANSOM, Silent Push 2차 Gentlemen 보고서)는 `iocs/watermarks-and-profiles.md` 참조 (누적)

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
- 신규 미검증 캠페인/기법 노트 추가: INCRANSOM 랜섬웨어 (IOC 값 없음), Silent Push 2차 Gentlemen 보고서 참조 (페치 차단, 신규 IOC 없음) — `iocs/watermarks-and-profiles.md`에만 기록
- 네트워크 범위 확인: hivesecurity.gitlab.io, www.securityscientist.net, s4e.io, hermes-codex.vercel.app, intelinsights.substack.com — 이번 실행에서 신규로 차단 확인 (ENOTFOUND)

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
- [Google Cloud — Threat Intelligence Blog](https://cloud.google.com/blog/topics/threat-intelligence) — 2026-11-12 — fetched (신규 CS 콘텐츠 없음)
- [Microsoft Security Blog — "cobalt strike" 검색](https://www.microsoft.com/en-us/security/blog/?s=cobalt+strike) — 2026-11-12 — fetched (신규 CS 콘텐츠 없음)
- hivesecurity.gitlab.io — 2026-11-12 — blocked (ENOTFOUND, 신규 시도)
- www.securityscientist.net — 2026-11-12 — blocked (ENOTFOUND, 신규 시도)
- s4e.io — 2026-11-12 — blocked (ENOTFOUND, 신규 시도)
- hermes-codex.vercel.app — 2026-11-12 — blocked (ENOTFOUND, 신규 시도)
- intelinsights.substack.com — 2026-11-12 — blocked (ENOTFOUND, 신규 시도)
- www.silentpush.com — 2026-11-12 — blocked (ENOTFOUND, 기존 확인)
