# Incident tickets

This is the flagship folder — full triage writeups, not walkthroughs. Each one follows the same format on purpose, so the mistakes and corrections are as visible as the final answer.

## Format every ticket follows

1. **Scenario** — what alert/data came in
2. **Initial triage** — first read of the evidence, first hypothesis
3. **Where I got stuck / got it wrong** — the actual mistake, not a cleaned-up version
4. **Investigation** — what I checked next, and why
5. **MITRE mapping** — tactic + technique for each confirmed action
6. **Containment / recommendation** — what I'd actually do about it
7. **What I'd do differently** — the retrospective

## Tickets

| Ticket | Scenario type | Status |
|---|---|---|
| [`ticket-01-benign-alert-triage/`](./ticket-01-benign-alert-triage) | Splunk log triage — suspicious executable that turned out benign | Complete |
| [`capstone-tempest/`](./capstone-tempest) | TryHackMe Tempest — full incident, persistence + C2 | Complete |
| [`capstone-boogeyman/`](./capstone-boogeyman) | TryHackMe Boogeyman — phishing entry point, full incident | Complete |

Add one new ticket every 1–2 weeks — consistency here matters more than volume.
