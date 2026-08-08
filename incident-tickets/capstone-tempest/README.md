# Capstone: Tempest (TryHackMe)

**Room:** SOC Level 1 — Capstone Challenges — Tempest
**Type:** End-to-end incident investigation pulling together every skill area from the path

## Scenario

Tempest is a full incident investigation — starting from initial file/IOC identification and continuing through to tracing persistence and command-and-control activity. It's designed to test everything covered across the SOC Level 1 path in one continuous scenario, rather than one skill in isolation.

## What I completed independently

- Identified the initial malicious file, along with its associated IPs and hashes — the IOC-identification stage, which lines up with Threat Intel Tools being my strongest area throughout the path

## Where I got stuck

Two distinct points:

1. **Locating the secondary persistence location.** Once I'd found the initial file, I had no clear indicators pointing to where the attacker had placed a second copy or a persistence mechanism elsewhere on the system. I could tell *that* something had happened, but not *where* to look next without help.
2. **C2 connection tracing.** The room modeled a C2 connection and payload installation. I found some of the answers independently, but authenticating which credentials were legitimate vs attacker-controlled is where I got stuck and needed outside help.

## MITRE ATT&CK mapping (tactic level)

| Stage | Tactic |
|---|---|
| Initial file/IOC identification | TA0043 Reconnaissance / TA0007 Discovery |
| Persistence mechanism | TA0003 Persistence |
| C2 connection + payload | TA0011 Command and Control |

## What I'd do differently

Build a habit of checking common persistence locations (startup folders, scheduled tasks, registry run keys, alternate service installs) as a standard *second step* immediately after confirming an initial compromise — right now I only think to look once I already suspect persistence exists, rather than checking as a matter of course.
