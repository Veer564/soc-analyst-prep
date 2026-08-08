# TryHackMe SOC Level 1 → repo mapping

TryHackMe's SOC Level 1 path (14 sections) is the backbone of my learning here, but I grouped my notes by SOC skill domain instead of mirroring all 14 sections as separate folders — easier to navigate and closer to how the skills actually get used on the job.

| TryHackMe section | Rooms | Where it lives in this repo |
|---|---|---|
| 1. Blue Team Introduction | Junior Security Analyst Intro, SOC Role in Blue Team, Humans/Systems as Attack Vectors | `01-foundations/` |
| 2. SOC Team Internals | Alert Triage, Alert Reporting, Workbooks/Lookups, SOC Metrics | `01-foundations/` + `incident-tickets/` |
| 3. Core SOC Solutions | EDR, SIEM, Splunk Basics, Elastic Basics, SOAR | `02-siem-and-detection/splunk-home-lab/` |
| 4. Cyber Defence Frameworks | Pyramid of Pain, Cyber Kill Chain, Unified Kill Chain, MITRE, Eviction | `01-foundations/mitre-attack-notes/` |
| 5. Phishing Analysis | Fundamentals, Tools, Prevention, Greenholt Phish, Snapped Phish-ing Line | `05-phishing-and-threat-intel/` |
| 6. Network Traffic Analysis | Wireshark Basics/Packet Ops/Traffic Analysis, NetworkMiner | `04-network-monitoring/` |
| 7. Network Security Monitoring | Discovery/Exfil/MITM Detection, IDS Fundamentals, Snort | `04-network-monitoring/` |
| 8. Web Security Monitoring | Detecting Web Attacks/Web Shells/Web DDoS | `04-network-monitoring/` |
| 9. Windows Security Monitoring | Windows Logging + Threat Detection 1–3 | `03-endpoint-monitoring/windows-event-log-analysis/` |
| 10. Linux Security Monitoring | Linux Logging + Threat Detection 1–3 | `03-endpoint-monitoring/` |
| 11. Malware Concepts for SOC | Classification, Malware Analysis Intro, LOTL Attacks, Shadow Trace | `03-endpoint-monitoring/` |
| 12. Threat Analysis Tools | CTI Intro, File/Hash Intel, IP/Domain Intel | `05-phishing-and-threat-intel/` |
| 13. SIEM Triage for SOC | Log Analysis, Alert Triage w/ Splunk & Elastic, ItsyBitsy, Benign | `02-siem-and-detection/` |
| 14. Capstone Challenges | Tempest, Boogeyman 1–3, SOC-SIM scenarios | `incident-tickets/capstone-*` |

Note: TryHackMe revamped this path in Nov 2025. If you're comparing against an older SOC Level 1 completion, room names may differ slightly — the skill groupings above still hold.
