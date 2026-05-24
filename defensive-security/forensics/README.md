# Forensics Labs

> Hands-on practice in Linux digital forensics: deleted-file recovery, anti-forensic resistance, raw-disk analysis, and the investigator's mindset.

---

## Domain Focus

Digital forensics is what separates "I think something happened" from "here is the evidence, here is the methodology, here is the timeline." These labs build practical fluency in:

- **Anti-forensic resistance** — recovering evidence after a subject has attempted cleanup (`rm`, `history -c`, `shred`)
- **Raw-disk analysis** — string searches, file carving, signature-based recovery from raw partitions
- **Correlated artifacts** — finding evidence in journal, swap, RAM, logs, and caches when the obvious source is gone
- **Signal-to-noise filtering** — length filters, keyword lists, pattern matching at scale
- **Chain-of-custody discipline** — evidence hashing, timeline documentation, negative-finding reporting
- **Linux forensic toolchain** — `strings`, `grep`, `foremost`, `scalpel`, `debugfs`, `extundelete`, Sleuth Kit

---

## Lab Index

| Lab | Date | Status | Highlights |
|---|---|---|---|
| [Linux Deleted-File Recovery & Anti-Forensics](./linux-deleted-file-recovery/) | 24 May 2026 | ✅ Complete | Simulated hostile scenario, three meta-questions on real-world challenges, raw-partition recovery, file carving with `foremost` |

---

## Toolchain

| Tool | Purpose |
|---|---|
| **`strings`** | Extract printable text from binary devices/partitions |
| **`grep`** (with `-a`, `-i`, `-E`, `-C`, `-B`, `-A`) | Filter and contextualize search results |
| **`foremost`** | Signature-based file carving — recover files by header (FF D8 FF, %PDF, PK, etc.) |
| **`scalpel`** | Alternative carving tool with custom signature support |
| **`debugfs` / `extundelete`** | ext4 metadata and journal-based recovery |
| **Sleuth Kit** (`fls`, `icat`, `mactime`) | Timeline reconstruction and inode-level analysis |
| **`nano` / `cat`** | Reviewing redirected output files |

---

## Forensic Principles Encoded in These Labs

1. **Deletion is not erasure.** Disk blocks remain until overwritten.
2. **Never rely on a single artifact.** If one source is gone, look for correlated ones — journal, swap, RAM, logs, caches.
3. **Filter aggressively.** Raw disk output is mostly noise. Length filters, regex patterns, and result-file redirection are mandatory.
4. **Patience is a tool.** Real scans run overnight against terabytes. Define, queue, return — don't stare at the terminal.
5. **Negative findings are valid.** "No evidence recovered, methodology documented" is a professional outcome.

---

## Planned / Queued

Identified during current labs as next forensic exercises:

- **Memory forensics with Volatility / Volatility3** — extract process lists, network connections, command-line args from RAM images
- **ext4 journal recovery** via `debugfs` / `extundelete` against an unmounted disk image
- **Sleuth Kit timeline reconstruction** — minute-by-minute activity record from `fls` + `mactime`
- **Defensive detection mirror** — `auditd` / Sysmon rules that would catch the offensive patterns these labs investigate
- **Reusable keyword-list / regex library** — the analyst's forensic dictionary for raw-partition searches

---

← [Back to defensive-security](../) | [Main repository](../../)
