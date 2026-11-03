# Cobalt Strike Snapshot — 2026-11-03 UTC

## 수집 상태
- 페치 성공: cloud.google.com/blog/topics/threat-intelligence
- 페치 차단: unit42.paloaltonetworks.com, hunt.io, silentpush.com, threatbook.io, netlas.io, socradar.io (모두 DNS 해석 실패, 기존 run들과 동일)
- 검증: 2 / 미검증: 5 / 검토 필요: 39

## 최근 캠페인 (최근 60일)

이번 실행에서 새로 확인된 "최근 60일" 캠페인 없음. 기존에 기록된 StrikeShark/SharkLoader, The Gentlemen/CountLoader, Ghostwriter, RedNovember 등은 모두 2026-10-25 이전 보고서 기준으로 60일 창을 벗어났거나 이미 기록됨 — 아래 "이번 실행 변경사항" 참조.

## 공격자 C2 팀서버 (차단 대상) (6)
변경 없음 — 기존 6개 IP 유지 (도메인 0건). 상세는 `iocs/ips.txt` / `iocs/domains.txt` 참고.

(참고: UNC2628/DarkSide 귀속 호스트(athaliaoriginals.com, ctxinit.azureedge.net, lagrom.com, 104.193.252.197, 162.244.81.253, 185.180.197.86)는 Mandiant 보고서로 귀속이 verified 상태이나 2021년 인프라로 ~5년 경과해 재할당 가능성이 높아 `iocs/needs-review.txt`에 "do not block"으로 분류되어 있음 — block-safe 버킷(`iocs/ips.txt`/`iocs/domains.txt`)과는 별개.)

## 검토 필요 — 스캐너 탐지만 된 팀서버 (차단 금지) (39)
기존 38건에 신규 1건 추가:
- 45.67.229.97 — ThreatFox(abuse.ch) IOC #642546, 범용 "Cobalt Strike C2 URL" 태그, 2026-04-01 만료, 캠페인/행위자 귀속 없음 — 스캐너/피드 분류만, 차단 금지

전체 목록은 `iocs/needs-review.txt` 참조 (39건, 모두 스캐너 탐지 또는 귀속 불명확).

## JARM 헌팅 신호 (차단 용도 아님)
- `07d14d16d21d21d00042d41d00041de5fb3038104f457d92ba02e9311512c2` — Cobalt Strike 기본 팀서버(OpenJDK 11) — 일반 헌팅 신호, 캠페인 특정 아님 — ⚠️ (미검증)
- `07d14d16d21d21d07c42d41d00041d24a458a375eef0c576d23a7bab9a9fb1` — 동일 기본값의 대체 보고치(Java 11 SSL stack) — ⚠️ (미검증)

## 워터마크 · 맬리어블 프로파일
- **0** — LOW SIGNAL. 크랙판 공통 기본값, 차단 신호 아님.
- **987654321** — "rogue" Cobalt Strike C2 서버 클러스터(스캐너 탐지만, `needs-review`에 등재) 공유 워터마크. ThreatBook이 북한 연계 우즈베키스탄 캠페인과 낮은 신뢰도로 연계 — ⚠️ (미검증)
- **1473793097 / 1357776117** — Silent Push "The Gentlemen" 랜섬웨어 제휴 조직(CountLoader → Cobalt Strike 체인)의 워터마크값 — ⚠️ (미검증, 1차 출처 미확보)
- **BeudtKgqnlm0Ruvf+VYxuw==** — APT24 전용 BEACON 워터마크 해시, Mandiant 검증 — verified
- 상세 내용은 `iocs/watermarks-and-profiles.md` 참조 (누적 기록).

## 파일 해시 (2)
### SHA-256
- 5f37b85687780c089607670040dbb3da2749b91b8adc0aa411fd6280b5fa7103 — beacon — BlackByte 랜섬웨어 침해(ProxyShell Exchange 익스플로잇) — verified
- 7c1f99dca8e5a7897892f9d224a6495023a2cfd2671697d229d355978c415ed2 — loader — KnowledgeDeliver/CVE-2026-5426 — verified

## 호스트 IOC · 행위
- UNC4393/BASTA DNS BEACON 서브도메인 명명 규칙: `h.dns.<C2도메인>`, `ridoj4.<8자>.dns.<C2도메인>`, `jzz.<8자>.dns.<C2도메인>`, `wnh.<8자>.dns.<C2도메인>` — Mandiant 검증
- UNC2628/DarkSide: SMB BEACON named pipe `\.\pipe\UIA_PIPE_*`, Windows 서비스명 `CitrixInit`, 도메인 계정 `spservice` — Mandiant 검증

## 이번 실행 변경사항
- 신규 C2: 없음
- 신규 해시: 없음
- 승격(미검증→검증): 없음
- 분류 변경: 없음
- 신규 검토 필요 항목: 45.67.229.97 (ThreatFox IOC #642546, 만료 2026-04-01, 귀속 없음)
- 참고: unit42.paloaltonetworks.com, hunt.io가 이번 run에서 처음으로 DNS 해석 실패가 재확인되어 차단된 도메인으로 공식 분류됨 (이전에는 "untested"였음)

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

(`iocs/domains.txt`는 현재 공란.)

## 출처
- [Google Cloud Blog — Threat Intelligence](https://cloud.google.com/blog/topics/threat-intelligence) — 2026-11-03 — fetched (Cobalt Strike 관련 신규 콘텐츠 없음)
- unit42.paloaltonetworks.com/cobalt-strike-team-server/ — blocked (DNS)
- unit42.paloaltonetworks.com/cobalt-strike-malleable-c2/ — blocked (DNS)
- hunt.io/blog/guide-hunting-cobalt-strike-part-4-c2-feeds-api — blocked (DNS)
- silentpush.com/blog/gentlemen-ransomware/ — blocked (DNS)
- threatbook.io/blog/suspected-north-korea-linked-hackers... — blocked (DNS)
- netlas.io/blog (RST Cloud JARM hunting) — blocked (DNS)
- socradar.io (StrikeShark IOC Radar report) — blocked (DNS)
