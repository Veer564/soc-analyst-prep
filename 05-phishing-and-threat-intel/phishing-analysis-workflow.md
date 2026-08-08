# Phishing email analysis — my workflow

## Triage order

1. **Headers first, body second.** Check `Return-Path`, `Received` chain, and `Authentication-Results` (SPF/DKIM/DMARC pass or fail) before reading a single word of the email body — spoofed sender identity is often visible here before any content analysis.
2. **URLs — inspect, never click.** Hover/extract the actual destination, check against the display text. Mismatched display-vs-actual URL is one of the highest-signal indicators.
3. **Attachments — hash before opening.** Get the file hash and check it against threat intel (VirusTotal, AbuseIPDB-style lookups) before any sandboxing.
4. **Urgency/authority language** — a text-level signal, but the weakest one in isolation. Pair with the header/URL evidence, don't lead with it.

## IOC extraction checklist

- Sender domain + any lookalike/typosquat pattern
- All URLs (not just the "main" one — phishing kits often have secondary redirect chains)
- Attachment hash(es)
- Any IP addresses in headers (originating mail server)

## Where this connects to SecureWatch

The IOC confidence-scoring logic in SecureWatch (recency decay + multi-source weighting) is directly relevant here — a single IOC hit from one feed is weaker evidence than the same IOC confirmed across multiple sources, and that distinction matters when deciding whether to escalate a phishing report or close it as a false positive.
