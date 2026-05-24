# cybersecurity-labs

> Hands-on cybersecurity lab portfolio.
> Authorized self-audits, academic exercises, and forensic-discipline practice — documented in the open.

---

## What This Repository Is

A growing collection of practical cybersecurity labs I've conducted as part of my independent learning alongside formal B.Tech (Cybersecurity Specialization) coursework. Each lab is documented as a complete, standalone artifact: methodology, findings, evidence handling, defensive recommendations, and legal scope.

This is not a tutorial collection. It's a record of **work I actually did, on systems I was authorized to test, with the same rigor I'd apply to a real engagement.**

---

## Why Public

Three reasons:

1. **Verifiability.** Anyone evaluating my technical depth can read exact methodology, command sequences, and findings — not just a resume bullet that says "familiar with Wireshark."
2. **Discipline forcing function.** Knowing my work is public makes me document better, scope cleaner, and avoid shortcuts.
3. **Resource for others.** If you're on a similar path — self-taught, zero budget — these labs show what's achievable with free tools, authorized targets, and patience.

---

## Authorization & Scope

**Every lab in this repository was performed against systems I personally own or had explicit written authorization to test.** No third-party network, device, or system was targeted at any point. All work complies with the Indian Information Technology Act, 2000.

This repository contains analytical methodology, redacted findings, and defensive recommendations. It does **not** contain credentials, exploitation tooling against specific targets, or material that could be misused against unauthorized systems.

---

## Lab Index

| Domain | Lab | Date | Status |
|---|---|---|---|
| **Wireless** | [WPA2-PSK Handshake Capture & Analysis](./wireless/wpa2-handshake-capture/) | 24 May 2026 | ✅ Complete |

*This index will grow as new labs are added. Each entry links to a self-contained lab folder with its own README and supporting artifacts.*

---

## Domain Coverage

The labs are organized by domain. Domains marked with a labs count are active; others are planned and will populate over time.

| Domain | Description | Labs |
|---|---|---|
| **`wireless/`** | 802.11 attacks, monitor-mode capture, handshake analysis, defensive WiFi posture | 1 |
| **`web/`** | OWASP Top 10 exercises, request manipulation, authentication flaws | *(planned)* |
| **`network/`** | `nmap` reconnaissance, packet analysis, protocol-level investigation | *(planned)* |
| **`forensics/`** | Disk imaging, memory analysis, timeline reconstruction, chain-of-custody practice | *(planned)* |
| **`linux/`** | Privilege escalation, log forensics, persistence detection | *(planned)* |
| **`windows/`** | Event log analysis, registry forensics, Active Directory basics | *(planned)* |

---

## Repository Structure

~~~
cybersecurity-labs/
├── README.md                              # This file
├── LICENSE
├── wireless/
│   ├── README.md                          # Wireless domain overview
│   └── wpa2-handshake-capture/
│       ├── README.md                      # Lab writeup
│       └── WPA2_Handshake_Lab_Report.pdf  # Full forensic-style report
├── web/                                   # planned
├── network/                               # planned
├── forensics/                             # planned
├── linux/                                 # planned
└── windows/                               # planned
~~~

---

## Operating Principles

- **Authorization first.** No technique applied outside explicitly owned or sanctioned scope.
- **Forensic discipline by default.** Evidence hashed at capture time. Chain-of-custody documented. Timelines preserved.
- **Defensive framing.** Every offensive finding ends with mitigation. Demonstrating an attack without proposing a defense is incomplete work.
- **Honest reporting.** What worked, what failed, what got skipped — documented as-is. Inflated writeups serve no one.

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
