# Wireless Security Labs

> Hands-on practice in 802.11 protocol analysis, monitor-mode capture, attack workflows, and defensive WiFi posture.

---

## Domain Focus

Wireless networks remain one of the most accessible attack surfaces in any environment — and one of the most misunderstood by users. These labs build practical fluency in:

- **802.11 protocol mechanics** — beacons, probes, association, the 4-way EAPOL handshake
- **Monitor-mode capture** — putting wireless adapters into receive-all mode for analysis
- **Tool fluency** — the full `aircrack-ng` suite, `wireshark`, `kismet`
- **Cryptographic understanding** — what WPA2-PSK actually protects, where it fails, what WPA3 changed
- **Defensive posture** — what configurations actually mitigate real-world attacks (vs. security theater)

---

## Lab Index

| Lab | Date | Status | Highlights |
|---|---|---|---|
| [WPA2-PSK Handshake Capture & Analysis](./wpa2-handshake-capture/) | 24 May 2026 | ✅ Complete | Full `aircrack-ng` chain, EAPOL deep-dive, threat model matrix, defensive recommendations |

---

## Hardware Used

| Component | Notes |
|---|---|
| **Alfa AWUS036ACH** (Realtek RTL8812AU) | Primary wireless adapter — supports monitor mode + packet injection on 2.4 GHz and 5 GHz |
| **Kali Linux VM** (VMware) | Lab environment for all wireless work |
| **Personally-owned home router** | Authorization target for self-audits |

---

## Planned / Queued

Items identified during current labs that are queued for future sessions:

- **Custom wordlist generation** — `crunch` + `cupp` for targeted dictionary attacks
- **Hashcat GPU acceleration** — quantify attacker speeds vs. CPU-bound `aircrack-ng`
- **WPS PIN attack analysis** — `reaver` / `bully` against PIN-based WPS
- **Evil twin / rogue AP** — capture credentials from misconfigured client devices (in isolated lab)
- **Defender-side audit** — full MAC inventory, `arpwatch`, `kismet` for unauthorized client detection
- **WPA3-SAE analysis** — what changed, what didn't, what new attacks emerged (Dragonblood)

---

← [Back to offensive-security](../) | [Main repository](../../)
