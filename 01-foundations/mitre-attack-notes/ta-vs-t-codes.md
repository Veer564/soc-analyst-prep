# MITRE ATT&CK: Tactics (TA-codes) vs Techniques (T-codes)

The single most common mix-up when starting with MITRE ATT&CK — and the one that costs the most points in a graded ticket. Tactics answer "why," techniques answer "how."

## The distinction

| | Tactic (TA-code) | Technique (T-code) |
|---|---|---|
| Answers | *Why* is the attacker doing this? | *How* are they doing it? |
| Format | `TA00XX` | `T1XXX` (and `T1XXX.XXX` for sub-techniques) |
| Count | 14 total, fixed | Hundreds, growing |
| Example | TA0001 — Initial Access | T1566 — Phishing |
| Granularity | Category / goal | Specific method |

**Rule of thumb:** a tactic is a *stage* of the attack. A technique is the *specific move* used at that stage. One tactic can be achieved by many different techniques.

## The 14 tactics (kill-chain order)

1. TA0043 — Reconnaissance
2. TA0042 — Resource Development
3. TA0001 — Initial Access
4. TA0002 — Execution
5. TA0003 — Persistence
6. TA0004 — Privilege Escalation
7. TA0005 — Defense Evasion
8. TA0006 — Credential Access
9. TA0007 — Discovery
10. TA0008 — Lateral Movement
11. TA0009 — Collection
12. TA0011 — Command and Control
13. TA0010 — Exfiltration
14. TA0040 — Impact

## Worked example — a phishing-to-persistence chain

| Stage | Tactic | Technique |
|---|---|---|
| Attacker sends malicious attachment | TA0001 Initial Access | T1566.001 Phishing: Spearphishing Attachment |
| Macro runs on open | TA0002 Execution | T1204.002 User Execution: Malicious File |
| Attacker adds registry run key | TA0003 Persistence | T1547.001 Registry Run Keys / Startup Folder |
| Attacker dumps LSASS | TA0006 Credential Access | T1003.001 OS Credential Dumping: LSASS Memory |

Notice: four different tactics, four different techniques, one continuous attack. This is the mapping skill a real ticket write-up needs — not just "this was a phishing attack" but which tactic-technique pair applies to *each individual observed action*.

## Skill gap I'm actively working on

Recalling specific T-codes under time pressure (mid-ticket, not with the ATT&CK site open). Current approach: rebuild this table from memory weekly rather than just re-reading it — recognition isn't the same as recall.
