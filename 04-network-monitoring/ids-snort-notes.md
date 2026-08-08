# IDS / Snort fundamentals

## Signature vs anomaly-based detection

- **Signature-based** (Snort's default mode): matches known patterns — fast, low false-positive rate, but blind to novel attacks
- **Anomaly-based**: flags deviation from a learned baseline — catches novel attacks, but needs tuning to avoid alert fatigue from legitimate traffic changes

## Basic Snort rule anatomy

```
alert tcp any any -> $HOME_NET 22 (msg:"Possible SSH brute force"; flags:S; threshold:type threshold, track by_src, count 5, seconds 60; sid:1000001;)
```

- `alert` — action taken
- `tcp any any -> $HOME_NET 22` — protocol and traffic direction
- `msg` — what shows in the alert
- `threshold` — the actual detection logic (5 SYNs from one source in 60s)
- `sid` — unique rule ID (custom rules start at 1,000,000+ to avoid colliding with the official ruleset)

## Note

This threshold-based brute-force logic is conceptually identical to the `brute_force` detector in SecureWatch — same idea (N events from one source in a time window), different implementation layer (network IDS vs log-based detection).
