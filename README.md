# SOC Analyst Prep

A working record of my journey into SOC analysis and blue team security — log analysis, SIEM tooling, incident triage, and network security monitoring, built through TryHackMe's SOC Level 1 path, a self-built Splunk home lab, and CTF practice.

**Status:** SOC Level 1 certified · TryHackMe Top 2% globally · actively building toward SOC Analyst / Security Engineer roles

This isn't a notes dump. Every writeup here follows the same format — **Problem → What I tried → Where I got stuck → How I fixed it → What I'd do differently** — because the mistakes are the useful part. Anyone can post a clean answer after the fact; this repo is meant to show the actual reasoning process.

---

## Skills matrix

| Area | Tools / Concepts | Status |
|---|---|---|
| Windows log analysis | Event IDs 4624/4625/4648/4672/4688/4698/7045/5140, Logon ID correlation | Working proficiency |
| SIEM | Splunk (home lab built), SPL queries, dashboarding | Building |
| Frameworks | MITRE ATT&CK (TA vs T codes), Cyber Kill Chain | Working proficiency |
| Network monitoring | Wireshark, packet analysis, IDS concepts | Learning |
| Incident triage | Alert classification, escalation, reporting | Practicing via tickets below |
| Threat intel | IOC lookup, phishing analysis | Learning |

## Repo structure

| Folder | What's in it |
|---|---|
| [`01-foundations/`](./01-foundations) | SOC role, MITRE ATT&CK, Kill Chain — the mental models everything else builds on |
| [`02-siem-and-detection/`](./02-siem-and-detection) | My Splunk home lab (architecture, attack simulation, SPL queries) |
| [`03-endpoint-monitoring/`](./03-endpoint-monitoring) | Windows/Linux log analysis — the event ID cheat sheet lives here |
| [`04-network-monitoring/`](./04-network-monitoring) | Wireshark, traffic analysis, IDS notes |
| [`05-phishing-and-threat-intel/`](./05-phishing-and-threat-intel) | Phishing triage workflow, IOC/threat intel notes |
| [`incident-tickets/`](./incident-tickets) | **Flagship folder.** Full incident triage writeups, including TryHackMe capstone rooms (Tempest, Boogeyman) written up as real tickets, not walkthroughs |
| [`ctf-writeups/`](./ctf-writeups) | OverTheWire Bandit → picoCTF, mapping blue-team skills to CTF categories |
| [`docs/course-mapping.md`](./docs/course-mapping.md) | How this repo maps to TryHackMe's SOC Level 1 path structure |
| [`docs/learning-journal.md`](./docs/learning-journal.md) | Honest, unpolished notes on what came easily, what needed help, and what's still a work in progress |

## Why this structure

I didn't mirror TryHackMe's 14 course sections 1:1 — that reads as a course transcript, not a portfolio. Instead I grouped by SOC skill domain, and the `incident-tickets/` folder is where the real depth lives: that's where judgment gets tested, not just room completion.

## Background

Final-year B.Tech IT student. Started with foundational security tooling (port scanner, SSH log analyzer), moved into structured SOC training via TryHackMe, and built a home Splunk lab (M2 Mac + UTM + Windows 11 ARM64 VM + Universal Forwarder) to practice against simulated attacks rather than just canned lab data.

Other projects: [PacketHawk](https://github.com/Veer564/PacketHawk) (network anomaly detection), [SecureWatch](https://github.com/Veer564/SecureWatch) (threat intel platform).
