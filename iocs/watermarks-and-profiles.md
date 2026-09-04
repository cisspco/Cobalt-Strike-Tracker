# Watermarks and Malleable C2 Profiles

Cumulative notes on Cobalt Strike license watermark IDs and malleable C2 profile characteristics tied to specific campaigns. This file is detection/attribution content, not a blocklist.

## Watermarks

- **0** — LOW SIGNAL. Default value baked into virtually every cracked/leaked copy of Cobalt Strike in circulation. Thousands of unrelated actors share it. Do not use to drive classification.
- **1** — LOW SIGNAL. Also commonly associated with cracked/leaked copies. Same caveat as watermark 0.
- **678358251** — ⚠️ (미검증/unverified, 2026-09-03) Reported (hunt.io, fetch blocked this run — search-snippet only) as associated with multiple threat actors including the Black Basta ransomware group. Needs verification against a fetched source before treating as a reliable pivot.
- **BeudtKgqnlm0Ruvf+VYxuw==** — verified 2026-09-04 (Mandiant/Google Cloud Blog, fetched). Cobalt Strike BEACON watermark hash tied specifically to APT24; the same watermark was previously observed in a separate APT24 campaign per the report's IOC section. Not a generic/shared value — treat as a genuine APT24 pivot. Source: "APT24's Pivot to Multi-Vector Attacks" (2025-11-20).

## Malleable C2 Profiles / Characteristics

- **UNC4393/BASTA DNS Beacon subdomain naming convention** — verified 2026-09-03 (Mandiant, fetched). DNS BEACON subhosts follow a distinctive pattern:
  - `h.dns.<C2 domain>`
  - `ridoj4.<8-char string>.dns.<C2 domain>`
  - `jzz.<8-char string>.dns.<C2 domain>`
  - `wnh.<8-char string>.dns.<C2 domain>`
  These are traffic-shaping/naming characteristics for detection content — not specific hostnames to block. Source: Mandiant/Google Cloud Blog, "UNC4393 Goes Gently into the SILENTNIGHT" (2024-07-29).

## Default / Public JARM Reference

- `07d14d16d21d21d00042d41d00041de5fb3038104f457d92ba02e9311512c2` — publicly documented default Cobalt Strike team server JARM (tied to OpenJDK 11 runtime commonly used by operators). Widely known value; legitimate services on the same Java stack can coincidentally share it. Hunting/pivoting use only — see `iocs/jarm.txt`.
