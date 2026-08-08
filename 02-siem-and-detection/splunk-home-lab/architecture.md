# Splunk home lab — build notes

## Setup

1. **Host:** Splunk Enterprise installed natively on M2 Mac (Apple Silicon build)
2. **VM:** Windows 11 ARM64 provisioned in UTM
3. **Networking:** UTM VM bridged/shared network so the VM can reach the host's Splunk management port
4. **Forwarder:** Splunk Universal Forwarder installed on the Windows VM, configured to monitor `WinEventLog://Security`, `WinEventLog://System`, and `WinEventLog://Application`, forwarding to the Splunk Enterprise indexer on the host

## Attack simulation

PowerShell scripts run on the VM to generate representative attack traffic:
- Repeated failed logons (simulating brute force) → generates 4625 volume
- `runas` with alternate credentials → generates 4648
- Scheduled task creation → generates 4698

## What I'd improve next

- Add Sysmon for process-tree and network-connection visibility beyond what native Windows auditing gives
- Automate the attack simulation with a scheduling script instead of running manually each session
- Build alerting (not just dashboard visualization) so triage practice includes the "did I get paged for the right thing" step
