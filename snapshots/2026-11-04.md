# Cobalt Strike Snapshot — 2026-11-04 UTC

## 수집 상태
- 페치 성공: cloud.google.com/blog/topics/threat-intelligence, microsoft.com/en-us/security/blog (검색)
- 페치 차단: dailysecurityreview.com, vectra.ai, reliaquest.com, securitricks.com, techtarget.com, malpedia.caad.fkie.fraunhofer.de (모두 신규 DNS 해석 실패 확인 — 기존 차단 목록에 추가됨)
- 검증: 2 / 미검증: 5 / 검토 필요: 39

## 최근 캠페인 (최근 60일)

이번 실행에서 새로 확인된 "최근 60일" 공격자-C2-귀속 캠페인 없음(호스트 IOC 기준). 아래는 검색 스니펫에서만 확인된 미검증 캠페인/귀속 맥락 — 어떤 것도 구체적인 C2 IP/도메인/해시를 포함하지 않음:

### UNG0002 (창저우대학교 대상) ⚠️ (미검증)
- 대상: 중국 창저우대학교
- Cobalt Strike 역할: macOS 폴더 구조 내 은닉(상세 체인 미확인)
- 귀속: Seqrite, medium-high confidence (검색 스니펫)
- 출처: dailysecurityreview.com (페치 차단, 신규)

### Ghostwriter (업데이트) ⚠️ (미검증)
- 대상: 우크라이나/폴란드 정부기관
- 신규 귀속: ESET이 "Belarus-aligned"로 귀속(moderate-to-high confidence), 2026-03부터 활동 — 기존 기록된 지오펜싱 PDF 전달 체인과 일치
- 출처: 검색 스니펫 (ESET, 미페치)

### "The Gentlemen" / CountLoader (업데이트) ⚠️ (미검증)
- 신규 맥락: CountLoader는 크랙 소프트웨어 배포 사이트를 통해 확산되며 Cobalt Strike와 AdaptixC2를 모두 전달; 이 광범위한 배포의 운영자는 미귀속
- 출처: 검색 스니펫

## 공격자 C2 팀서버 (차단 대상) (6)
변경 없음 — 기존 6개 IP 유지 (도메인 0건). 상세는 `iocs/ips.txt` / `iocs/domains.txt` 참고.

## 검토 필요 — 스캐너 탐지만 된 팀서버 (차단 금지) (39)
변경 없음 — 이번 실행에서 구체적인 신규 호스트 값 확보 실패(ThreatFox 검색 스니펫은 IOC ID만 노출, 실제 IP/도메인 값은 threatfox.abuse.ch 페치 차단으로 확인 불가). 전체 목록은 `iocs/needs-review.txt` 참조.

## JARM 헌팅 신호 (차단 용도 아님)
변경 없음 (2건). `iocs/jarm.txt` 참조.

## 워터마크 · 맬리어블 프로파일
- **0** — LOW SIGNAL. 크랙판 공통 기본값, 차단 신호 아님.
- 신규 캠페인 맥락(UNG0002, Ghostwriter/ESET 업데이트, CountLoader/AdaptixC2 확장)이 `iocs/watermarks-and-profiles.md`에 기록됨 — 구체적 워터마크 값은 확인되지 않음.
- Middle East 인프라 보고서(securitricks.com, 2026-02~05, 1,350+ C2, 98 provider) — Cobalt Strike는 Tactical RMM/Sliver와 함께 언급된 프레임워크 중 하나; 집계 스캐너 수치일 뿐 개별 귀속 없음 — 트렌드 맥락으로만 기록.
- Fox-IT Cobalt Strike Beacon Corpus(2026-10, 데이터셋 공개) — 캠페인 아님, 참고용으로만 기록.
- 상세 내용은 `iocs/watermarks-and-profiles.md` 참조 (누적 기록).

## 파일 해시 (2)
### SHA-256
- 5f37b85687780c089607670040dbb3da2749b91b8adc0aa411fd6280b5fa7103 — beacon — BlackByte 랜섬웨어 침해(ProxyShell Exchange 익스플로잇) — verified
- 7c1f99dca8e5a7897892f9d224a6495023a2cfd2671697d229d355978c415ed2 — loader — KnowledgeDeliver/CVE-2026-5426 — verified

## 호스트 IOC · 행위
변경 없음. 기존 UNC4393/BASTA, UNC2628/DarkSide 행위 패턴 참조 (`iocs/watermarks-and-profiles.md`).

## 이번 실행 변경사항
- 신규 C2: 없음
- 신규 해시: 없음
- 승격(미검증→검증): 없음
- 분류 변경: 없음
- 신규 미검증 캠페인 맥락: UNG0002(창저우대학교), Ghostwriter ESET 귀속 업데이트, CountLoader/AdaptixC2 확산 맥락, Middle East 인프라 집계 보고서, Fox-IT Beacon Corpus 데이터셋 — 모두 `iocs/watermarks-and-profiles.md`에만 기록, 차단 가능 호스트 없음
- 신규 차단 확인 도메인: dailysecurityreview.com, vectra.ai, reliaquest.com, securitricks.com, techtarget.com, malpedia.caad.fkie.fraunhofer.de
- 조용한 날 지속 (캠페인/검토 항목 기준 2026-10-13 이후 변동 없음 연속)

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
- [Google Cloud Blog — Threat Intelligence](https://cloud.google.com/blog/topics/threat-intelligence) — 2026-11-04 — fetched (Cobalt Strike 관련 신규 콘텐츠 없음)
- [Microsoft Security Blog search](https://www.microsoft.com/en-us/security/blog/?s=cobalt+strike) — 2026-11-04 — fetched (2021 Solorigate/TEARDROP 글 외 신규 CS 콘텐츠 없음)
- dailysecurityreview.com/?p=39938 (UNG0002) — blocked (DNS, 신규 확인)
- vectra.ai/topics/cobalt-strike — blocked (DNS, 신규 확인)
- reliaquest.com/blog/cobalt-strike-servers-ransomware — blocked (DNS, 신규 확인)
- securitricks.com (Middle East infra report) — blocked (DNS, 신규 확인)
- techtarget.com (job seekers campaign) — blocked (DNS, 신규 확인)
- malpedia.caad.fkie.fraunhofer.de/actor/cobalt — blocked (DNS, 신규 확인)
