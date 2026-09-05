# Cobalt Strike Tracker

Daily-updated tracker of **malicious** use of Cobalt Strike — named criminal/state-linked campaigns that deploy it, plus standalone infrastructure indicators (team servers, malleable C2 profiles, license watermarks, JARM fingerprints) — for defensive detection and blocking.

**Cobalt Strike is a commercial, legitimately-licensed red-team tool: a team server found by an internet scan is not, by itself, evidence of malicious infrastructure — authorized pentesters and red teams run servers that look identical in scans, so only hosts explicitly attributed to a specific malicious campaign, intrusion, or malware family by a source are treated as block-safe attacker C2.**

Last updated: 2026-09-05 UTC

## Counts
- C2 domains (attacker-attributed, block-safe): 0
- C2 IPs (attacker-attributed, block-safe): 5
- Needs-review (scanner-only / ambiguous, NOT block-safe): 0
- JARM hunting signals: 1
- File hashes: 1
- Unverified C2 candidates (domains + IPs): 0

## Files
- `latest.md` — most recent full snapshot report (overwritten daily)
- `snapshots/<YYYY-MM-DD>.md` — dated snapshot history
- `iocs/domains.txt` — attributed attacker C2 domains, block-safe
- `iocs/ips.txt` — attributed attacker C2 IPs, block-safe
- `iocs/unverified-domains.txt` / `iocs/unverified-ips.txt` — unverified attacker-C2 candidates, NOT block-safe until promoted
- `iocs/needs-review.txt` — scanner-flagged team servers or ambiguous attribution, deliberately NOT firewall-ready
- `iocs/jarm.txt` — TLS fingerprint hunting signals only, never block-safe on their own
- `iocs/watermarks-and-profiles.md` — cumulative watermark ID and malleable C2 profile notes
- `iocs/sha256.txt` — Cobalt Strike loader/beacon/stager file hashes

## Raw blocklist URLs
- Domains: https://raw.githubusercontent.com/cisspco/Cobalt-Strike-Tracker/main/iocs/domains.txt
- IPs: https://raw.githubusercontent.com/cisspco/Cobalt-Strike-Tracker/main/iocs/ips.txt

**Only `iocs/domains.txt` and `iocs/ips.txt` are safe to feed into a firewall or blocklist.** Every other file in this repo (needs-review, unverified-*, jarm.txt, watermarks-and-profiles.md) is detection/hunting content or explicitly unconfirmed, and must not be used to block traffic.
