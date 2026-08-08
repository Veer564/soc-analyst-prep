# Wireshark / network traffic analysis notes

## Core workflow

1. Apply a display filter to cut noise before eyeballing anything (`ip.addr==`, `tcp.port==`, `http.request`)
2. Follow TCP/UDP stream on anything suspicious to see full conversation context, not just one packet
3. Check `Statistics > Conversations` for volume outliers before diving into individual packets — this is the fastest way to spot exfiltration or scanning at a glance

## Filters I use most

| Filter | Use |
|---|---|
| `tcp.flags.syn==1 && tcp.flags.ack==0` | Isolate SYN packets — useful for spotting port scans |
| `dns.qry.name contains ""` | DNS query inspection — pair with entropy checks for tunneling |
| `http.request.method=="POST"` | Find data being sent out, not just requested |
| `tcp.analysis.retransmission` | Network issues vs deliberate slow-scan behavior |

## Connects to PacketHawk

This is the same detection logic I implemented programmatically in PacketHawk — port-scan detection via port-count-per-window, DNS tunneling via Shannon entropy on subdomains. Doing it manually in Wireshark first is what made writing the automated detector make sense.
