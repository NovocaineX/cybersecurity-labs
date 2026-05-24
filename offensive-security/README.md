# Offensive Security Labs

> Red-team practice: reconnaissance, exploitation, post-exploitation, and the offensive workflows underlying real-world attacks. Authorized scope only.

---

## What's Here

This folder contains labs where I take the **attacker's perspective** — understanding how exploitation works at the protocol, application, and system level. Every lab is performed against personally-owned or explicitly authorized targets.

The goal isn't to "be a hacker." It's to understand attack mechanics deeply enough to:

1. **Defend better** — you can't protect what you don't understand offensively
2. **Investigate competently** — forensic work requires knowing what attacker artifacts look like
3. **Communicate clearly** — security recommendations are credible only when they come with demonstrated technical depth

---

## Domain Index

| Domain | Description | Labs |
|---|---|---|
| **[`wireless/`](./wireless/)** | 802.11 attacks, monitor-mode capture, handshake analysis, WiFi defensive posture | 1 |
| **`web/`** | OWASP Top 10 exercises, authentication flaws, request manipulation | *(planned)* |
| **`network/`** | `nmap` reconnaissance, packet analysis, protocol-level investigation | *(planned)* |
| **`linux/`** | Privilege escalation, persistence, log evasion | *(planned)* |
| **`windows/`** | Local privilege escalation, AD basics, registry abuse | *(planned)* |

---

## Companion Folder

See [`../defensive-security/`](../defensive-security/) (when published) for the blue-team counterpart: forensics, incident response, SOC exercises, defensive tooling.

The two folders are designed to complement each other — most labs in either domain reference the other side (e.g. a wireless attack lab queues a wireless defense audit; a forensics lab references the attack patterns it's detecting).

---

## Authorization Reminder

Every technique in this folder is illegal to apply against systems you do not own or have explicit written authorization to test. India's Information Technology Act, 2000 (Sections 43 & 66) governs unauthorized access — fines up to ₹1 crore and/or imprisonment up to 3 years. The "it was just a lab" framing offers no legal defense.

---

← [Back to main repository](../)
