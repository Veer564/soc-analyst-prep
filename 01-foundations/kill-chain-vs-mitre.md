# Cyber Kill Chain vs MITRE ATT&CK — when to use which

Both describe the stages of an attack. They're not competitors — they're different resolutions of the same map.

## Lockheed Martin Cyber Kill Chain (7 stages)

Reconnaissance → Weaponization → Delivery → Exploitation → Installation → Command & Control → Actions on Objectives

Linear, sequential, high-level. Good for **communicating an incident to non-technical stakeholders** — a manager understands "they got in, then they moved to control the system" faster than a list of technique IDs.

## MITRE ATT&CK (14 tactics, hundreds of techniques)

Not strictly linear — tactics can repeat, loop, or run in parallel (e.g. Discovery and Lateral Movement often alternate). Built from real observed adversary behavior, constantly updated.

Good for **the actual triage/investigation work** — mapping a specific log entry or alert to a specific technique is what makes a ticket defensible and searchable later.

## How I use them together in a ticket

1. Kill Chain gives the incident summary a shape a manager can skim in 10 seconds.
2. ATT&CK tactic/technique IDs go in the technical body — this is what lets someone else search "have we seen T1003.001 before" across past tickets.

## Where they disagree

Kill Chain assumes a fairly linear malware-delivery attack (its origins are in Lockheed Martin's work on APT intrusions). It doesn't map cleanly onto attacks that don't need "weaponization" — insider threats, misconfigurations, living-off-the-land attacks using only built-in tools. ATT&CK's Defense Evasion and Living off the Land techniques (LOLBins) don't have a clean Kill Chain stage — this is a known limitation worth naming in a ticket rather than forcing a bad fit.
