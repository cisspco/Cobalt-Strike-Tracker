# Watermarks and Malleable C2 Profiles

Cumulative notes on Cobalt Strike license watermark IDs and malleable C2 profile characteristics tied to specific campaigns. This file is detection/attribution content, not a blocklist.

## Watermarks

- **0** — LOW SIGNAL. Default value baked into virtually every cracked/leaked copy of Cobalt Strike in circulation. Thousands of unrelated actors share it. Do not use to drive classification.
- **1** — LOW SIGNAL. Also commonly associated with cracked/leaked copies. Same caveat as watermark 0.
- **678358251** — ⚠️ (미검증/unverified, 2026-09-03) Reported (hunt.io, fetch blocked this run — search-snippet only) as associated with multiple threat actors including the Black Basta ransomware group. Needs verification against a fetched source before treating as a reliable pivot.
- **688983459** — ⚠️ (미검증/unverified, 2026-09-07) Reported (hunt.io, fetch blocked this run — search-snippet only) as tied to a cluster of infrastructure running the latest Cobalt Strike version. No specific campaign/actor attribution in the snippet — needs a fetched source before use as a pivot.
- **BeudtKgqnlm0Ruvf+VYxuw==** — verified 2026-09-04 (Mandiant/Google Cloud Blog, fetched). Cobalt Strike BEACON watermark hash tied specifically to APT24; the same watermark was previously observed in a separate APT24 campaign per the report's IOC section. Not a generic/shared value — treat as a genuine APT24 pivot. Source: "APT24's Pivot to Multi-Vector Attacks" (2025-11-20).

## Malleable C2 Profiles / Characteristics

- **UNC4393/BASTA DNS Beacon subdomain naming convention** — verified 2026-09-03 (Mandiant, fetched). DNS BEACON subhosts follow a distinctive pattern:
  - `h.dns.<C2 domain>`
  - `ridoj4.<8-char string>.dns.<C2 domain>`
  - `jzz.<8-char string>.dns.<C2 domain>`
  - `wnh.<8-char string>.dns.<C2 domain>`
  These are traffic-shaping/naming characteristics for detection content — not specific hostnames to block. Source: Mandiant/Google Cloud Blog, "UNC4393 Goes Gently into the SILENTNIGHT" (2024-07-29).

- **KnowledgeDeliver / CVE-2026-5426** — verified 2026-09-05 (Mandiant/Google Cloud Blog, fetched). No watermark or malleable C2 profile details were disclosed in the report for this campaign; noted here for completeness only. Source: "Exploitation of KnowledgeDeliver via ViewState Deserialization Vulnerability" (2026-05-25).

## Threat Actor Attribution Notes (not IOCs)

- **DEV-0243** — verified 2026-09-17 (Microsoft Security Insider, fetched). Named in Microsoft/Fortra/Health-ISAC's joint technical-and-legal disruption operation against cracked/leaked Cobalt Strike (enabled by a 2023-03-31 US District Court order), as an actor designation associated with deploying cracked Cobalt Strike ahead of Conti and LockBit ransomware. No specific watermark, IP, or domain disclosed in the source — recorded here as attribution context only, not an IOC. Cracked Cobalt Strike copies were linked to 68+ ransomware attacks across 19 countries' healthcare organizations per the same source. Source: "Stopping cybercriminals from abusing security tools" (microsoft.com/en-au/security/security-insider).
- **DEV-0243 (additional context)** — verified 2026-09-18 (Microsoft Security Blog, fetched, via search-result summary of "Raspberry Robin worm part of larger ecosystem facilitating pre-ransomware activity", 2022-10-27). DEV-0243 overlaps with the actor tracked elsewhere as EvilCorp; first observed deploying LockBit ransomware-as-a-service in November 2021. Background/attribution context only — no new watermark, IP, or domain.

## Default / Public JARM Reference

- `07d14d16d21d21d00042d41d00041de5fb3038104f457d92ba02e9311512c2` — publicly documented default Cobalt Strike team server JARM (tied to OpenJDK 11 runtime commonly used by operators). Widely known value; legitimate services on the same Java stack can coincidentally share it. Hunting/pivoting use only — see `iocs/jarm.txt`.

## Macro Trend Notes (not IOCs)

- **Cobalt Strike BEACON ransomware-incident share, declining** — verified 2026-09-14 (Google Cloud/Mandiant Blog, fetched). BEACON's share of ransomware intrusions fell from ~60% (2021) to ~38% (2022), 20% (2023), 11% (2024), and 2% (2025), attributed partly to actors adopting alternative post-exploitation frameworks (e.g. AdaptixC2). No specific campaign or IOC attached — informational context only, not a detection or blocklist signal. Source: "Ransomware Tactics, Techniques, and Procedures in a Shifting Threat Landscape" (2026-03-16).
- **M-Trends 2026: BEACON falls to 4th most-observed malware family** — ⚠️ (미검증/unverified, 2026-09-15). WebSearch snippet reports that after five consecutive years as Mandiant's most frequently observed malware family, Cobalt Strike BEACON fell to fourth place in M-Trends 2026, behind GOLDVEIN.JAVA (downloader) and REDBIKE (Akira ransomware). WebFetch of the source page (cloud.google.com/security/resources/m-trends-executive-edition) returned only a truncated title with no body content, so this could not be promoted to verified this run. No specific campaign or IOC attached — informational context only, consistent with the BEACON-decline trend already noted above.
