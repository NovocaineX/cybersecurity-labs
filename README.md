# cybersecurity-labs

> Hands-on cybersecurity lab portfolio.
> Authorized self-audits, academic exercises, and forensic-discipline practice — documented in the open.

---

## What This Repository Is

A growing collection of practical cybersecurity labs conducted as part of my independent learning alongside formal B.Tech (Cybersecurity Specialization) coursework. Each lab is documented as a complete, standalone artifact: methodology, findings, evidence handling, defensive recommendations, and legal scope.

This is not a tutorial collection. It's a record of **work I actually did, on systems I was authorized to test, with the same rigor I'd apply to a real engagement.**

---

## Why Public

1. **Verifiability.** Anyone evaluating my technical depth can read exact methodology, command sequences, and findings — not just a resume bullet that says "familiar with Wireshark."
2. **Discipline forcing function.** Knowing my work is public makes me document better, scope cleaner, and avoid shortcuts.
3. **Resource for others.** If you're on a similar path — self-taught, zero budget — these labs show what's achievable with free tools, authorized targets, and patience.

---

## Authorization & Scope

**Every lab in this repository was performed against systems I personally own or had explicit written authorization to test.** No third-party network, device, or system was targeted at any point. All work complies with the Indian Information Technology Act, 2000.

This repository contains analytical methodology, redacted findings, and defensive recommendations. It does **not** contain credentials, exploitation tooling against specific targets, or material that could be misused against unauthorized systems.

---

## Lab Index

| Track | Domain | Lab | Date | Status |
|---|---|---|---|---|
| 🔴 Offensive | Wireless | [WPA2-PSK Handshake Capture & Analysis](./offensive-security/wireless/wpa2-handshake-capture/) | 24 May 2026 | ✅ Complete |
| 🔵 Defensive | Forensics | [Linux Deleted-File Recovery & Anti-Forensics](./defensive-security/forensics/linux-deleted-file-recovery/) | 24 May 2026 | ✅ Complete |

*This index will grow as new labs are added. Each entry links to a self-contained lab folder with its own README and supporting artifacts.*

---

## Track Coverage

Labs are organized by **track** (offensive vs. defensive) and then by **domain** within each track.

### 🔴 [`offensive-security/`](./offensive-security/)

Red-team practice — reconnaissance, exploitation, post-exploitation, attack workflows. Authorized scope only.

| Domain | Description | Labs |
|---|---|---|
| `wireless/` | 802.11 attacks, monitor-mode capture, handshake analysis | 1 |
| `web/` | OWASP Top 10, authentication flaws, request manipulation | *(planned)* |
| `network/` | `nmap` reconnaissance, packet analysis | *(planned)* |
| `linux/` | Privilege escalation, persistence | *(planned)* |
| `windows/` | Local privesc, AD basics, registry abuse | *(planned)* |

### 🔵 [`defensive-security/`](./defensive-security/)

Blue-team practice — forensics, incident response, detection engineering, SOC workflows, hardening.

| Domain | Description | Labs |
|---|---|---|
| `forensics/` | Deleted-file recovery, anti-forensic resistance, raw-disk analysis, chain-of-custody | 1 |
| `incident-response/` | Triage workflows, evidence collection, SOC playbooks | *(planned)* |
| `soc/` | Log analysis, SIEM exercises, detection rules | *(planned)* |
| `hardening/` | Defensive configuration, network segmentation, security posture audits | *(planned)* |

---

## Repository Structure

~~~
cybersecurity-labs/
├── README.md                                     # This file
├── LICENSE
│
├── offensive-security/                           # 🔴 Red-team labs
│   ├── README.md
│   └── wireless/
│       ├── README.md
│       └── wpa2-handshake-capture/
│           ├── README.md
│           └── WPA2_Handshake_Lab_Report.pdf
│
└── defensive-security/                           # 🔵 Blue-team labs
    ├── README.md
    └── forensics/
        ├── README.md
        └── linux-deleted-file-recovery/
            ├── README.md
            └── Linux_Forensics_Lab_Report.pdf
~~~

---

## Operating Principles

- **Authorization first.** No technique applied outside explicitly owned or sanctioned scope.
- **Forensic discipline by default.** Evidence hashed at capture time. Chain-of-custody documented. Timelines preserved.
- **Defensive framing.** Every offensive finding ends with mitigation. Demonstrating an attack without proposing a defense is incomplete work.
- **Honest reporting.** What worked, what failed, what got skipped — documented as-is. Inflated writeups serve no one.
- **Negative findings are findings.** "No evidence recovered, methodology documented" is a defensible professional outcome — often the truthful one.

---

## About the Author

**Aadarsh Bonthula**
B.Tech Computer Science (Cybersecurity Specialization), 2nd Year
Manav Rachna International Institute of Research and Studies

Independent security researcher building toward digital forensics and incident response work. Long-term goal: contribute to India's Police Cyber Crime Unit and eventually lead a cybersecurity & digital forensics firm focused on protecting under-served populations (hospitals, abuse victims, the elderly).

**Other work:**
- [`vortex-hackathon26`](https://github.com/NovocaineX/vortex-hackathon26) — Forensica AI, document forgery detection
- More cross-links as projects ship publicly

---

## License

MIT License. See [LICENSE](./LICENSE) for full terms.

Documentation and methodology are shared for educational and portfolio purposes. Techniques described are illegal to apply against networks or systems the reader does not own or have explicit written authorization to test.
