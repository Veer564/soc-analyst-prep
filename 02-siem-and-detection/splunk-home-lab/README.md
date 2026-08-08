# Splunk home lab

A self-built detection lab — set up to practice against traffic and logs I generate myself, rather than only working with pre-packaged TryHackMe room data.

## Why I built this

TryHackMe's SIEM rooms give you data that's already been shaped for the exercise. I wanted a lab where I control the attack simulation and have to build my own detections from scratch — closer to what SOC L1 actually involves.

## Architecture

- **Host:** M2 MacBook, running Splunk Enterprise natively
- **Guest VM:** Windows 11 ARM64, via UTM (Apple Silicon virtualization)
- **Log shipping:** Splunk Universal Forwarder on the Windows VM, forwarding `WinEventLog` sources (Security, System, Application) to Splunk Enterprise on the host
- **Attack simulation:** PowerShell scripts on the VM to generate realistic Windows Security event traffic (failed logons, privilege use, process creation) for detection testing

See [`architecture.md`](./architecture.md) for the full setup notes and troubleshooting.

## What's in this folder

- `architecture.md` — full build notes, UTM networking config, Universal Forwarder setup
- `spl-queries/` — the SPL queries built for the SOC dashboard

## Status

Core pipeline working: VM → Universal Forwarder → Splunk Enterprise → dashboard. Next: expanding detections beyond the initial 5 queries, adding a Sysmon source for richer process-tree visibility.
