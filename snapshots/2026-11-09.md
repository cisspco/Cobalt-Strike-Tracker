# Cobalt Strike Snapshot — 2026-11-09 UTC

## 수집 상태
- 페치 성공: cloud.google.com/blog/topics/threat-intelligence (신규 Cobalt Strike 콘텐츠 없음), www.microsoft.com/en-us/security/blog (검색, 신규 콘텐츠 없음)
- 페치 차단: research.checkpoint.com (Silver Dragon 1차 출처, 신규 확인), www.seqrite.com (UNG0002/Dragon Whistle 백서, 신규 확인), securityaffairs.com (신규 확인), assets.kpmg.com (Silver Dragon CTIP PDF, 신규 확인), dev.to (신규 확인), aviatrix.ai (신규 확인) — 모두 ENOTFOUND
- 검증: 누적 9건 (C2 IP 6 + 해시 2 + GCTI 크랙판 배경자료 1) / 미검증: 누적 6건 (C2 IP 1 + 도메인 5) / 검토 필요: 46

## 최근 캠페인 (최근 60일)

캠페인 수준의 전적으로 새로운 보고는 이번 실행에서도 없음 (2026-10-13 이후 지속, 27일 연속 조용한 날 — 차단 대상 기준). 다만 이번 실행에서 두 건의 기존 미기록 캠페인/명칭이 검색 스니펫으로 새로 확인되었으나, 모두 60일 기준을 벗어나거나 구체적 IOC가 없어 차단 목록에는 반영되지 않음(아래 참고 참조).

- 참고(신규 명칭 확인, 미검증, 60일 기준 초과): **Silver Dragon** (APT41 연계, Check Point, 2026-03-03 발표) — 유럽·동남아 정부기관 대상, 2024년 중반부터 활동. 보고된 모든 사례에서 최종 페이로드로 Cobalt Strike 전달 확인. 특징은 Google Drive를 C2 채널로 쓰는 .NET 백도어 **GearDoor**; 후속 도구로 스크린샷용 SilverScreen, SSH 명령 실행용 SSHcmd(KPMG 요약). Cobalt Strike 단계의 구체적 C2 IP/도메인/해시/워터마크는 어떤 스니펫에도 없음 — 귀속/기법 맥락으로만 기록, IOC 아님. 1차 출처(research.checkpoint.com) 및 5개 보조 출처 모두 이번 실행에서 페치 차단 확인.
- 참고(기존 기록 보강, 미검증): **UNG0002 — Operation Dragon Whistle** (Changzhou University, Seqrite, medium-high confidence, 2026-05) — 이번 실행에서 캠페인 공식 명칭("Operation Dragon Whistle") 확인, 전신인 "Operation Cobalt Whisper"(2024-05~09, LNK/VBScript로 Cobalt Strike 비콘 전달, 중국/홍콩/파키스탄 국방·전기공학·민항 분야 대상)와 "Operation AmberMist"(2025-01~05, Shadow RAT/INET RAT 자체 임플란트로 전환)까지 계보 확인. 구체적 IOC는 여전히 없음.
- 참고(신규 확인되지 않음, 기존 기록 유지): StrikeShark/SharkLoader, The Gentlemen/CountLoader, Ghostwriter, RedNovember — 이번 실행 검색에서 재확인, 상세 변경 없음.

## 공격자 C2 팀서버 (차단 대상) (6)
- 108.61.242[.]65 — KnowledgeDeliver/CVE-2026-5426 또는 BlackByte 관련 검증된 캠페인 C2 — verified
- 109.206.243[.]59 — 상동 — verified
- 146.70.78[.]43 — 상동 — verified
- 45.150.108[.]213 — 상동 — verified
- 87.120.254[.]39 — 상동 — verified
- 92.204.160[.]240 — 상동 — verified

(도메인 없음)

## 검토 필요 — 스캐너 탐지만 된 팀서버 (차단 금지) (46)
- 기존 42건 유지 + 신규 4건 (ThreatFox, watermark 987654321 클러스터, 캠페인/행위자 귀속 없음 — 스캐너/피드 분류만, 차단 금지):
  - 124.156.200[.]252 (포트 4444, record #1614783)
  - 135.136.178[.]226 (포트 80, record #1795514, First Server Europe ASN/RU, 2026-04-20/21 탐지)
  - 139.196.126[.]161 (포트 443, record #1352876)
  - 158.160.193[.]205 (포트 8888, record #1667539)
- 상세는 `iocs/needs-review.txt` 참조

## JARM 헌팅 신호 (차단 용도 아님)
- `07d14d16d21d21d00042d41d00041de5fb3038104f457d92ba02e9311512c2` — Cobalt Strike 기본 팀서버 JARM (OpenJDK 11), 일반 헌팅 신호
- `07d14d16d21d21d07c42d41d00041d24a458a375eef0c576d23a7bab9a9fb1` — 동일 기본값의 대체 보고값 (Java 11 SSL 스택), 2차 후보로 기록

## 워터마크 · 맬리어블 프로파일
- **0 / 1** — 크랙판 공통값, 차단 신호 아님 (LOW SIGNAL)
- **100000000 / 666666666 / 987654321 / 678358251 / 688983459** — 크랙판/공유 클러스터 값, 개별 캠페인 귀속 없음 또는 약한 귀속, 차단 신호로 사용 금지. 이번 실행에서 987654321 클러스터에 신규 호스트 4건 확인(위 검토 필요 섹션 참조).
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
- 신규 C2 (미검증, 차단 대상 아님): 없음
- 신규 해시: 없음
- 승격(미검증→검증): 없음
- 분류 변경: 없음
- 검토 필요 신규 추가(4): 124.156.200[.]252, 135.136.178[.]226, 139.196.126[.]161, 158.160.193[.]205 (ThreatFox, watermark 987654321 클러스터, 스캐너 탐지만)
- 신규 캠페인 명칭/배경(미검증, IOC 없음): Silver Dragon (APT41 연계, Check Point 2026-03-03), UNG0002 "Operation Dragon Whistle"/"Operation Cobalt Whisper"/"Operation AmberMist" 계보

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
- [Google Cloud — Threat Intelligence Blog](https://cloud.google.com/blog/topics/threat-intelligence) — 2026-11-09 — fetched (신규 CS 콘텐츠 없음)
- [Microsoft Security Blog — "cobalt strike" 검색](https://www.microsoft.com/en-us/security/blog/?s=cobalt+strike) — 2026-11-09 — fetched (신규 CS 콘텐츠 없음)
- [Check Point Research — Silver Dragon targets organizations in Southeast Asia and Europe](https://research.checkpoint.com/2026/silver-dragon-targets-organizations-in-southeast-asia-and-europe/) — 2026-03-03 — blocked
- [Seqrite — UNG0002: Regional Threat Operations](https://www.seqrite.com/whitepaper/ung0002-regional-threat-operations-tracked-across-multiple-asian-jurisdictions/) — undated — blocked
- [Security Affairs — From phishing to Google Drive C2: Silver Dragon expands APT41 playbook](https://securityaffairs.com/188895/apt/from-phishing-to-google-drive-c2-silver-dragon-expands-apt41-playbook.html) — 2026-03 — blocked
- [KPMG — CTIP Silver Dragon (PDF)](https://assets.kpmg.com/content/dam/kpmgsites/in/pdf/2026/03/kpmh-ctip-silver-dragon-10-mar-2026.pdf.coredownload.inline.pdf) — 2026-03-10 — blocked
- [ThreatFox IOC #1795514](https://threatfox.abuse.ch/ioc/1795514/) — 2026-04-21 — blocked (snippet only)
