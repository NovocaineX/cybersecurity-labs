# WPA2-PSK Handshake Capture & Analysis

> **Status:** Phase 1 complete (capture + analysis). Phase 2 (dictionary attack benchmark) deferred.
> **Date:** 24 May 2026
> **Scope:** Self-authorized audit of personally-owned access point.

---

## Authorization Statement

All activities documented here were performed against a **personally-owned access point** on a **personally-controlled client device**, in compliance with the Indian Information Technology Act, 2000 (Sections 43 & 66). No third-party network or device was targeted at any point.

---

## Objective

Gain practical, end-to-end experience in the WPA2-PSK handshake capture workflow using the `aircrack-ng` suite within a virtualized Kali Linux environment — while practicing **forensic discipline** (evidence hashing, chain-of-custody, timeline documentation) typical of a real investigation.

---

## What This Lab Demonstrates

| Skill Area | Demonstrated |
|---|---|
| **Toolchain Operation** | Full `airmon-ng` → `airodump-ng` → `aireplay-ng` → `aircrack-ng` workflow |
| **Protocol Understanding** | 4-way EAPOL handshake mechanics, PBKDF2-HMAC-SHA1 key derivation, MIC verification |
| **Hardware Troubleshooting** | Diagnosed and resolved VMware USB 3.x passthrough issue with Realtek RTL8812AU adapter |
| **Forensic Discipline** | Evidence hashing (SHA-256), chain-of-custody documentation, timeline-based reporting |
| **Threat Modeling** | Attacker evasion / defender counter matrix (MAC spoofing, randomization, passive sniffing, burst connections, VPN tunneling) |
| **Defensive Posture** | Mitigation recommendations across HIGH / MEDIUM / LOW priorities |
| **Legal Framing** | IT Act 2000 compliance + explicit scope-of-engagement documentation |

---

## Environment

| Component | Configuration |
|---|---|
| Host OS | Windows |
| Hypervisor | VMware Workstation / Player |
| Guest OS | Kali Linux (VM) |
| Wireless Adapter | Alfa AWUS036ACH (Realtek RTL8812AU) |
| Target AP | Personally-owned home router (WPA2-PSK) |
| Toolchain | aircrack-ng 1.7 suite |

---

## Methodology (Brief)

Each step's output was observed and verified before proceeding — standard forensic discipline:

1. **Pre-flight** — USB passthrough verified, adapter detected, monitor-mode capability confirmed
2. **Kill interfering processes** — `airmon-ng check kill`
3. **Enable monitor mode** — `airmon-ng start wlan0`
4. **Broad reconnaissance** — channel-hopping scan to identify target AP + connected client
5. **Locked targeted capture** — channel-locked, BSSID-filtered packet capture to disk
6. **Forced handshake** — targeted deauthentication via `aireplay-ng`
7. **Verification** — `aircrack-ng` confirmation of captured handshake
8. **Evidence sealing** — SHA-256 hash of capture file for integrity

Full command-level methodology and rationale is in the PDF report.

---

## Key Findings (Summary)

| Finding | Summary |
|---|---|
| **F-1** | WPA2-PSK handshake successfully captured using complete `aircrack-ng` chain |
| **F-2** | Realtek RTL8812AU driver required VMware USB controller downgrade (3.x → 2.0) to function |
| **F-3** | Spoofed deauthentication succeeded — target AP does not enforce 802.11w (PMF) |
| **F-4** | Channel-locked capture produced clean handshake within 5 deauth bursts |
| **F-5** | No prior MAC inventory existed for defender-side anomaly detection (queued for follow-up) |

---

## Top 3 Defensive Recommendations

1. **Upgrade to WPA3-SAE** if all clients support it — eliminates offline dictionary attack vector entirely.
2. **If WPA3 is not viable**, enforce a **16+ character random WPA2-PSK passphrase** absent from public leak corpora (`rockyou.txt` and equivalents).
3. **Enable 802.11w (Protected Management Frames)** to mitigate deauthentication-based handshake forcing.

Full prioritized recommendations (7 total, HIGH / MEDIUM / LOW) are in the PDF.

---

## Full Report

📄 **[WPA2 Handshake Lab Report (PDF)](./WPA2_Handshake_Lab_Report.pdf)**

The PDF contains:

- Cover page with authorization statement
- Lab environment specifications (incl. pre-lab troubleshooting narrative)
- Step-by-step methodology with command-level detail
- Technical deep-dive: EAPOL handshake math, `airodump-ng` output column anatomy, threat-modeling matrix
- Evidence artifacts list + chain-of-custody template
- Findings + 7 prioritized defensive recommendations
- Deferred work / queued follow-ups
- Legal & ethical framing (IT Act 2000)

---

## Deferred Work

Identified during this lab, queued for future sessions in this domain:

- **Custom wordlist generation** experiment (`crunch` + `cupp`) — graduated complexity tiers
- **Recapture handshake** against new test passphrase + dictionary attack benchmark across 3 tiers
- **Home network defense audit** — full MAC inventory, `nmap` sweep, `arpwatch` deployment
- **Threat-modeling matrix template** — applied per-tool for every subsequent wireless tool studied
- **Hashcat GPU acceleration test** — quantifying realistic attacker speeds (100x+ over CPU)

---

← [Back to wireless domain](../) | [Back to offensive-security](../../) | [Main repository](../../../)
