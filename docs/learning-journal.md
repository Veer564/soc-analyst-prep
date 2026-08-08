# Learning journal

Honest running notes on what actually happened while working through SOC Level 1 — what I could do on my own, what needed outside help, and what's still genuinely unfinished. Kept separate from the technical reference notes elsewhere in this repo because this is about the *process*, not the reference material itself.

## Phishing analysis

Completed the Greenholt Phish room independently — identified all the required indicators without help. The second phishing room went similarly well; comfortable using OSINT tools like VirusTotal to check a file's history and reputation from its hash.

**Gap at the time:** didn't have a solid grasp of SPF and DMARC, which made the header-authentication questions genuinely difficult — needed outside explanation (AI/YouTube) to get through them. Understanding has improved since.

**Tool that stuck:** CyberChef, mainly for Base64 decoding and similar transforms. Became a reflexive go-to rather than something I had to think about reaching for.

## Network traffic analysis

Solid on Wireshark fundamentals now — following streams per protocol to pull out packet-level detail is a skill that came directly from working through the room walkthroughs, not just reading about it.

**Honest note:** the NetworkMiner room I completed for the sake of finishing it rather than genuine engagement — did the basic tasks but didn't go deep. Worth revisiting properly rather than leaving it as a checkbox.

## Security monitoring (Web / Linux / Windows)

- **Web:** learned to read web traffic and server activity — HTTP requests, web logs, and SIEM data — to identify attacks in progress.
- **Linux:** log structure (auth logs, system logs), user activity tracing, command-line investigation, and mapping observed activity to MITRE techniques.
- **Windows:** Sysmon events in Event Viewer, and getting familiar with key event codes for logon activity and related account events.

**Honest note:** this was the hardest section overall, and still is. It requires holding a lot of context at once — connecting individual log events into a coherent picture of how an attack actually unfolded, as a defender working backward from evidence rather than forward from known steps. Needed outside help on several of these challenges and didn't solve everything independently. Still actively working on this.

## Threat intel tools

The most comfortable and genuinely enjoyable section so far. Investigating an IP, URL, or file hash using AbuseIPDB, VirusTotal, WHOIS, URLScan, and cross-referencing against MITRE felt intuitive rather than effortful. This ended up being the strongest area throughout the path — see the capstone writeups, where IOC identification was consistently the part I completed without help.

## SIEM triage

Got hands-on with both Splunk and Elastic Stack. Ended up preferring Elastic — found the information more directly surfaced compared to Splunk. KQL isn't a strength yet, and complex queries in either platform are still a genuine struggle.

**Honest note:** the hard part wasn't just writing queries — it was the "what next" moment after finding one piece of information. Getting a lead and then not being sure how to connect it to the next step happened more than once. That's a specific, nameable gap (query-to-investigation pivoting) rather than a vague "SIEM is hard" — worth practicing deliberately rather than just doing more rooms passively.

## Capstones

See [`../incident-tickets/capstone-tempest/`](../incident-tickets/capstone-tempest/) and [`../incident-tickets/capstone-boogeyman/`](../incident-tickets/capstone-boogeyman/) for the full writeups. Short version: strong at initial IOC identification in both, consistently stuck at persistence-location discovery and C2 connection tracing in both — a repeated pattern, not a one-off.

## Where I actually am right now

I haven't fully mastered the whole path — there are event types and log patterns I still don't recognize instantly, and the security-monitoring section in particular needs more practice before it feels automatic rather than effortful. That's the accurate picture, not a polished one. Next focus areas, in order: persistence/C2 tracing (from the capstone pattern), then KQL and query-to-investigation pivoting (from SIEM triage), then a proper second pass at NetworkMiner.
