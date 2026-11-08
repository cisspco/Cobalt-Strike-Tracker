# Cobalt Strike Snapshot — 2026-11-08 UTC

## 수집 상태
- 페치 성공: cloud.google.com/blog/products/identity-security/making-cobalt-strike-harder-for-threat-actors-to-abuse (2022-11-18, GCTI 크랙판 카탈로그 — 이번 실행에서 처음으로 본문 전체 확인, 이전에는 블로그 인덱스 페이지만 확인됨)
- 페치 차단: unit42.paloaltonetworks.com (team-server / malleable-c2 두 URL 모두), www.silentpush.com/blog/gentlemen-ransomware, hunt.io (rare-watermark 글 및 part-3 automated-discovery 가이드), community.gurucul.com (StrikeShark), threatbook.io (Uzbekistan NK-linked), gbhackers.com, threatfox.abuse.ch (ioc/1832048/json) — 모두 ENOTFOUND, 기존 차단 목록과 일치
- 검증: 누적 9건 (C2 IP 6 + 해시 2 + GCTI 크랙판 배경자료 1) / 미검증: 누적 6건 (C2 IP 1 + 도메인 5) / 검토 필요: 42

## 최근 캠페인 (최근 60일)

캠페인 수준의 전적으로 새로운 보고는 이번 실행에서도 없음 (2026-10-13 이후 지속, 26일 연속 조용한 날). 검색 쿼리 6종 모두 기존에 기록된 캠페인(StrikeShark/SharkLoader, The Gentlemen/CountLoader, UNG0002, Ghostwriter, RedNovember)의 재확인 결과만 반환했음.

- 참고(신규 확인되지 않음, 기존 기록 유지): StrikeShark/SharkLoader (Gurucul 커뮤니티 리서치, 2026-06-25) — 이번 검색에서 재확인, 상세 변경 없음, 소스 페치 차단 지속.
- 참고(신규 확인되지 않음, 기존 기록 유지): The Gentlemen/CountLoader ransomware affiliate (Silent Push, 2026-02~) — watermark 1473793097/1357776117, C2 91.107.247.163(미검증) 재확인, 상세 변경 없음.
- 참고(신규 확인되지 않음, 기존 기록 유지): UNG0002 (Changzhou University, Seqrite, medium-high confidence, 2026-05) — 재확인, 상세 변경 없음.

## 공격자 C2 팀서버 (차단 대상) (6)
- 108.61.242[.]65 — KnowledgeDeliver/CVE-2026-5426 또는 BlackByte 관련 검증된 캠페인 C2 — verified
- 109.206.243[.]59 — 상동 — verified
- 146.70.78[.]43 — 상동 — verified
- 45.150.108[.]213 — 상동 — verified
- 87.120.254[.]39 — 상동 — verified
- 92.204.160[.]240 — 상동 — verified

(도메인 없음)

## 검토 필요 — 스캐너 탐지만 된 팀서버 (차단 금지) (42)
- 기존 41건 유지 + 신규 1건: 34.92.128[.]98 — ThreatFox 태그 Cobalt Strike C2, GCP ASN, 포트 80, 2026-06-09 탐지, 캠페인/조직 귀속 없음 — 스캐너 탐지만, 차단 금지 (상세는 `iocs/needs-review.txt` 참조)

## JARM 헌팅 신호 (차단 용도 아님)
- `07d14d16d21d21d00042d41d00041de5fb3038104f457d92ba02e9311512c2` — Cobalt Strike 기본 팀서버 JARM (OpenJDK 11), 일반 헌팅 신호
- `07d14d16d21d21d07c42d41d00041d24a458a375eef0c576d23a7bab9a9fb1` — 동일 기본값의 대체 보고값 (Java 11 SSL 스택), 2차 후보로 기록

## 워터마크 · 맬리어블 프로파일
- **0 / 1** — 크랙판 공통값, 차단 신호 아님 (LOW SIGNAL). 신규 배경자료(검증, Google Cloud GCTI, 2022-11-18, 이번 실행 처음 본문 확인): 버전 1.44~4.7, 34개 릴리스·275개 JAR 파일을 분석해 165개 YARA 탐지 시그니처 공개 — 수십만 개의 크랙판이 유통되고 있음을 뒷받침하는 규모 데이터이며, 워터마크 0/1이 저신뢰 신호인 근거를 보강함. 신규 캠페인/호스트 IOC는 없음.
- **100000000 / 666666666 / 987654321 / 678358251 / 688983459** — 크랙판/공유 클러스터 값, 개별 캠페인 귀속 없음 또는 약한 귀속, 차단 신호로 사용 금지
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
- 검토 필요 신규 추가: 34.92.128[.]98 (ThreatFox, GCP ASN, 2026-06-09, 스캐너 탐지만)
- 신규 검증 배경자료: Google Cloud GCTI "Making Cobalt Strike harder for threat actors to abuse" (2022-11-18) — 이번 실행 처음 본문 확인

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
- [Google Cloud — Making Cobalt Strike harder for threat actors to abuse](https://cloud.google.com/blog/products/identity-security/making-cobalt-strike-harder-for-threat-actors-to-abuse) — 2022-11-18 — fetched
- [Unit 42 — Cobalt Strike team server](https://unit42.paloaltonetworks.com/cobalt-strike-team-server/) — undated — blocked
- [Unit 42 — Cobalt Strike malleable C2](https://unit42.paloaltonetworks.com/cobalt-strike-malleable-c2/) — undated — blocked
- [Silent Push — No Place to Hide: The Gentlemen](https://www.silentpush.com/blog/gentlemen-ransomware/) — 2026-02 — blocked
- [Hunt.io — Rare Watermark Links Cobalt Strike 4.10 Team Servers](https://hunt.io/blog/rare-watermark-links-cobalt-strike-team-servers-to-ongoing-suspicious-activity) — 2026-10 — blocked
- [Hunt.io — Complete Guide to Hunting Cobalt Strike Part 3](https://hunt.io/blog/guide-hunting-cobalt-strike-part-3-automated-discovery) — undated — blocked
- [Gurucul — StrikeShark](https://community.gurucul.com/articles/ThreatResearch/StrikeShark-Investigating-a-New-25-6-2026) — 2026-06-25 — blocked
- [ThreatBook — Suspected North Korea-linked hackers vs Uzbekistan](https://threatbook.io/blog/suspected-north-korea-linked-hackers-conduct-targeted-attack-campaign-against-uzbekistan) — N/A — blocked
- [GBHackers — Hackers Deploy Cobalt Strike Beacon](https://gbhackers.com/hackers-deploy-cobalt-strike-beacon/) — 2026-09-13 — blocked
- [ThreatFox IOC #1832048](https://threatfox.abuse.ch/ioc/1832048/json/) — N/A — blocked
