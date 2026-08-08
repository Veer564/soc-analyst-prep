# Capstone: Boogeyman (TryHackMe)

**Room:** SOC Level 1 — Capstone Challenges — Boogeyman
**Type:** End-to-end incident investigation, starting from a phishing entry point

## Scenario

Boogeyman starts with a phishing-based intrusion and continues through payload identification and persistence — a second full end-to-end incident, testing the same skill chain as Tempest but from a different entry point (phishing rather than direct compromise).

## What I completed independently

- **Phishing analysis** — identifying the malicious file and its associated indicators. This is where the earlier Greenholt Phish room and general phishing-triage practice paid off directly.
- After getting past the persistence/connection stage (with help — see below), I completed the later payload-identification steps on my own using the information already gathered.

## Where I got stuck

Same stage as Tempest: persistence and connection-tracing. Seeing this show up twice, in two different rooms with different entry points, is what makes me confident this is a real skill gap rather than a one-off miss. The final part of the challenge was also difficult enough that I needed help to close it out.

## MITRE ATT&CK mapping (tactic level)

| Stage | Tactic |
|---|---|
| Phishing delivery | TA0001 Initial Access |
| Malicious file execution | TA0002 Execution |
| Persistence + C2 | TA0003 Persistence / TA0011 Command and Control |

## What I'd do differently

Same fix as Tempest — check standard persistence locations as a default second step. Additionally: once I have a C2 indicator, work backward methodically from the connection itself (destination IP/domain, timing, protocol) rather than trying to jump straight to "what payload got installed." I think I was skipping a step in the middle rather than missing the skill entirely.

---

## The pattern across both capstones

Strong at the front end of an investigation — identifying files, IPs, hashes, and IOCs. Weaker at the middle-to-late stage: tracing persistence mechanisms and C2 activity once an attacker is already established. Naming this precisely (rather than "capstones were hard") is what tells me exactly what to drill next: persistence discovery and C2 backward-tracing, specifically.
