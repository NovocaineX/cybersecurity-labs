# Defensive Security Labs

> Blue-team practice: forensics, incident response, detection engineering, and the defensive workflows that catch what the offensive side does. Authorized scope only.

---

## What's Here

This folder contains labs where I take the **defender's perspective** — recovering evidence, reconstructing timelines, building detection rules, and reasoning about what an attacker leaves behind even when they try to clean up.

The goal is to build the technical and methodological foundation for digital forensics and incident response work — ultimately toward a career in India's Police Cyber Crime Unit.

---

## Domain Index

| Domain | Description | Labs |
|---|---|---|
| **[`forensics/`](./forensics/)** | Disk forensics, deleted-file recovery, anti-forensic resistance, chain-of-custody discipline | 1 |
| **`incident-response/`** | Triage workflows, evidence collection, SOC playbooks | *(planned)* |
| **`soc/`** | Log analysis, SIEM exercises, detection rules | *(planned)* |
| **`hardening/`** | Defensive configuration, network segmentation, security posture audits | *(planned)* |

---

## Companion Folder

See [`../offensive-security/`](../offensive-security/) for the red-team counterpart: reconnaissance, exploitation, post-exploitation, and attack workflows.

The two folders are designed to complement each other. Most labs in either domain reference the other side — a wireless attack lab queues a wireless defense audit; a forensics lab references the attack patterns it's designed to detect.

---

## Operating Principles for Defensive Work

- **Evidence before conclusion.** Findings are supported by artifacts. Speculation is documented separately and labeled as such.
- **Negative findings are findings.** "No evidence recovered, methodology documented" is a defensible professional outcome — and often the truthful one.
- **Chain of custody, even in self-study.** Every artifact captured in a lab is hashed at capture time. The discipline is built before the stakes are real.
- **Patience is a tool.** Real investigations run scans overnight. The professional habit is to define the search, redirect output, queue the job, return to results.

---

## Legal Framing

Forensic recovery techniques are illegal to apply against devices the analyst does not own or have explicit authorization to investigate. The Indian Information Technology Act, 2000 (Sections 43, 66) and the DPDP Act, 2023 govern access to data and devices. Forensic capability is not a licence to apply it.

Every lab in this folder is performed against personally-owned virtual machines or simulated scenarios constructed by the analyst.

---

← [Back to main repository](../)
