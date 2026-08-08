# Ticket 01 — Alert Triage: Suspicious Executable (TryHackMe "Benign")

**Severity:** Initially flagged Medium/High — downgraded to benign after investigation
**Alert source:** Splunk — large volume of Windows event logs
**Analyst:** Veer Gokani

## Scenario

A large set of Windows event logs was provided in Splunk, with an initial alert pointing to a potentially malicious executable. The task: find the specific events that actually mattered inside a lot of noise, identify the executable, correlate timestamps to reconstruct the sequence of activity, and determine whether it was genuinely malicious.

## Initial triage

With that volume of logs, the first real problem wasn't technical — it was *where to even start looking*. Too much to review sequentially, so the first job was finding a filtering approach that could narrow the set down to an anchor point worth investigating further.

## Where I got stuck

Two related issues, both around the same root cause:

1. **Filtering.** I tried narrowing the logs down using several different fields, but for a long stretch none of them isolated the events that actually mattered — a lot of trial and error before landing on a combination that worked.
2. **Tracing the chain after the executable.** Once I'd identified the executable itself, following what happened next — specifically evidence of a payload download and a connection being established to another system — was hard to pin down. I could see *that* there was follow-on activity, but connecting "executable ran" to "payload downloaded, connection made" took much longer than it should have.

## Investigation

- Used the flagged executable as the anchor point rather than trying to review logs chronologically from the start
- Filtered in Splunk across multiple fields (process name, host, timestamp window) to narrow the working set
- Correlated timestamps around the executable's run time to surface related events — network activity, file writes — in the same window
- Worked through whether the full chain (execution → download → connection) held together as genuinely malicious, or had a legitimate explanation

## The twist — and why it's the actual point of the room

"Benign" is built around activity that *looks* suspicious on the surface — an executable running, a connection appearing right after — but turns out to be legitimate on closer inspection. This is arguably a more realistic and more valuable skill than finding an obvious IOC: most real SOC alerts are false positives, and confidently concluding "this is benign, and here's the evidence" without either missing a real threat or wasting an escalation is a core part of the job, not a lesser version of it.

## MITRE ATT&CK mapping (hypothesis, before ruling it out)

| Suspected stage | Tactic |
|---|---|
| Executable run | TA0002 Execution |
| Payload download | TA0011 Command and Control |
| Outbound connection | TA0011 Command and Control |

Since the final determination was benign, no technique applies to a confirmed incident — but working through this mapping as a hypothesis was still useful. It forced me to articulate exactly what *would* need to be true for this to be malicious, which is what actually let me rule it out with evidence instead of a guess.

## Containment / recommendation

No containment required — closed as benign / false positive. Recommendation: document the specific fields and evidence that ruled out malicious intent (expected process behavior, expected destination, consistency with baseline activity) so the same alert pattern can be triaged faster next time instead of starting from zero again.

## What I'd do differently

Build a faster, more repeatable filtering approach for large log dumps instead of testing fields by trial and error each time — start from a known anchor (the flagged executable, or its timestamp) and pivot outward by host, user, or Logon ID, rather than searching broadly and hoping a field narrows it down. This is the same gap I named in the SIEM triage section of the [learning journal](../../docs/learning-journal.md) — getting a lead and not immediately knowing how to pivot to the next step. This ticket is the concrete example of that gap actually happening.
