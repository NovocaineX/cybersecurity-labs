# Linux Deleted-File Recovery & Anti-Forensics Lab

> **Status:** ✅ Complete — evidence recovered against simulated anti-forensic deletion.
> **Date:** 24 May 2026
> **Scope:** Self-authored simulated forensic scenario on personally-owned Kali Linux VM.

---

## Authorization Statement

The simulated suspect, evidence files, and deletion activities documented here were all **created and executed by the analyst on a personally-owned Kali Linux VM**. No third-party system, user, or data was involved at any phase. Both the suspect actions and the investigation were performed by the analyst on the analyst's own host, in compliance with the Indian Information Technology Act, 2000.

---

## Objective

Simulate a hostile forensic scenario in which a "suspect" user creates incriminating evidence (a written plan, a malicious download command in shell history, and a debug log) and then performs anti-forensic cleanup using standard Linux tools (`rm`, `history -c`). Acting as the investigator with root access, recover the evidence using Linux forensic techniques — demonstrating that **deletion is not erasure** and that competent methodology produces defensible findings even against deliberate obstruction.

---

## What This Lab Demonstrates

| Skill Area | Demonstrated |
|---|---|
| **Anti-forensic resistance** | Recovered evidence after `rm`, `history -c`, and file deletion |
| **Raw-partition analysis** | `strings`, `grep`, length-filtered scans on `/dev/sda1` |
| **File carving** | `foremost` signature-based recovery — header detection (FF D8 FF, %PDF, PK) |
| **Correlated artifacts thinking** | Identified journal, swap, RAM, `/tmp`, logs as independent evidence sources |
| **Signal-to-noise filtering** | Length filters (`-n 30`), regex, keyword lists, redirection-to-file |
| **Forensic reporting discipline** | Negative findings documented as findings, not failures |
| **Linux internals** | Distinction between in-memory `history -c` and on-disk `.bash_history` |
| **Legal framing** | IT Act 2000 + DPDP Act 2023 scope-of-engagement awareness |

---

## Environment

| Component | Configuration |
|---|---|
| Host OS | Windows |
| Hypervisor | VMware Workstation / Player |
| Guest OS | Kali Linux (VM) |
| Toolchain | `bash`, `rm`, `history`, `df`, `strings`, `grep`, `foremost`, `scalpel`, `nano` |
| Target Partition | Personally-owned Kali VM root partition (identified via `df -h`) |

---

## Methodology (Brief)

The lab is structured in two phases — the analyst plays both roles in sequence:

### Phase 1: Constructing the Crime Scene (Suspect Role)
1. Create `suspect` user, switch to its shell
2. Plant 3 distinct evidence artifacts (text file in home, command in `.bash_history`, log in `/tmp`)
3. Anti-forensic cleanup: `rm`, `history -c`, exit shell

### Phase 2: Investigation (Investigator Role, as root)
1. Recover `.bash_history` despite `history -c` (key insight: `-c` clears memory, not disk)
2. Identify the raw partition (`df -h`)
3. String search on raw partition (initial naive attempt)
4. Refined precision search: `strings -n 30 /dev/sda1 | grep -i "CONFIDENTIAL"` → redirect to file
5. File carving fallback: `foremost -t txt -i /dev/sda1 -o /root/recovered`
6. Context search fallback: `grep -C 50 -i "CONFIDENTIAL"` for surrounding context

Full command-level methodology is in the PDF report.

---

## The Three Meta-Questions (Core Learning)

The most professionally significant part of this lab is the three challenges raised against the methodology mid-investigation. These mirror the exact obstacles real forensic investigators face:

### 1. "What if there is no trail — or `.bash_history` is fully deleted?"

**Reality:** Skilled subjects use `shred`, `srm`, or `rm` followed by `history -c` against the on-disk history file directly.

**Solution: never rely on a single artifact.** Look for correlated artifacts that survive deletion of the obvious one:
- **Swap files** (`/swapfile`, `/dev/sdaX`) — under memory pressure, deleted content may be paged to disk
- **Journaling FS (ext4)** — metadata (filename, size, timestamps) persists in `/var/log/journal` and ext4 journal
- **Temp & cache** (`/tmp`, `~/.cache`, `~/.local/share`) — apps cache before deleting main files
- **RAM (memory dump)** — content persists in memory pages even after disk deletion
- **Network & system logs** — `/var/log/syslog`, firewall logs, mail logs are independent of the filesystem

> *"If one door is closed, look for the window, the chimney, or the air vent. Never rely on a single artifact."*

### 2. "What if the keyword is not 'CONFIDENTIAL' — what if I don't know what I'm looking for?"

**Reality:** Real investigations don't come with magic words. Searching for a specific keyword was a training-convenience handle.

**Solutions:**
- **Keyword lists** — 500+ case-relevant terms (money, password, attack, transfer, crypto, wallet) run against the partition
- **File carving by signature** — search for file *headers* instead of text (FF D8 FF for JPEG, %PDF, PK for ZIP) using `foremost` / `photorec` / `scalpel`
- **String analysis by pattern** — `strings /dev/sda1 > all_strings.txt`, then regex-filter for IP addresses, email patterns, URLs, base64 blobs

### 3. "The raw scan returns enormous noise. Do I just wait and read terabytes manually?"

**Reality:** Yes — raw disks produce megabytes of garbage. Line-by-line review is impossible.

**Solution: filter aggressively, redirect to file, prioritize, automate.**

| Tool/Flag | What It Does |
|---|---|
| `grep -i` | Case-insensitive — catches "Confidential" and "CONFIDENTIAL" in one pass |
| `grep -E` | Regex — catch all email-like or IPv4-like patterns |
| `strings -n 30` | Only strings ≥30 chars — eliminates ~90% of binary noise |
| `foremost` | Carves files automatically — review extracted files, not raw stream |
| `fls` (Sleuth Kit) | Timeline of accesses/modifications — focus on time of suspected activity |

**Behavioural rule:** ❌ `strings /dev/sda1 | grep "word"` and stare at scrolling text. ✅ `strings -n 20 /dev/sda1 | grep -iE "password|attack|money" > results.txt` then `nano results.txt`.

> *"Patience is a tool. Real scans run overnight. Define the search, redirect output, queue the job, return to results."*

---

## Key Findings (Summary)

| # | Finding |
|---|---|
| **F-1** | Shell history file persists on disk after `history -c` — `-c` clears memory only |
| **F-2** | Deleted files leave recoverable traces in raw partition sectors when not overwritten |
| **F-3** | Single-keyword raw-partition search is unworkable without length + regex filters |
| **F-4** | `foremost` may fail to reconstruct very small or non-signature-bearing files |
| **F-5** | A negative finding ("no evidence recovered"), with documented methodology, is professionally stronger than a fabricated positive |

---

## Anti-Forensic Mindset (Documented Resilience)

| Suspect's Belief | Actual Forensic Reality |
|---|---|
| "I deleted the file with `rm`." | Disk blocks remain until overwritten. String search of the partition recovers content. |
| "I cleared bash history with `history -c`." | Only the active-shell memory buffer is cleared. `.bash_history` on disk is unaffected unless explicitly removed. |
| "There is no record of my actions anywhere." | Correlated artifacts persist independently: journal, swap, RAM, `/tmp`, application caches, syslog, firewall logs. Defeating all simultaneously is hard. |

---

## Full Report

📄 **[Linux Deleted-File Recovery Lab Report (PDF)](./Linux_Forensics_Lab_Report.pdf)**

The PDF contains:

- Cover with authorization statement
- Lab environment + rationale for the simulated-scenario approach
- Phase 1 — full crime scene construction (commands + reasoning per artifact)
- Phase 2 — investigation methodology with command-level detail
- Section 4 — the three meta-questions with full analysis tables
- Refined precision investigation (combined filters)
- File carving methodology + fallback strategies
- 5 numbered findings + anti-forensic mindset matrix
- 5 queued follow-up labs
- Legal framing (IT Act 2000, DPDP Act 2023)

---

## Deferred Work

Identified during this lab, queued for future sessions:

- **Memory forensics with Volatility/Volatility3** — RAM image analysis for process lists, network connections, command-line args
- **ext4 journal recovery** with `debugfs` / `extundelete` against an unmounted disk image
- **Sleuth Kit timeline reconstruction** — `fls`, `icat`, `mactime` for minute-by-minute activity records
- **Defensive detection mirror** — `auditd` / Sysmon rules that would have caught the suspect's actions in real time
- **Reusable keyword-list and pattern-regex library** — the analyst's forensic dictionary

---

← [Back to forensics domain](../) | [Back to defensive-security](../../) | [Main repository](../../../)
