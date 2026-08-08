# Linux log analysis for SOC

## Key log locations

| Log | Path (Debian/Ubuntu) | What it shows |
|---|---|---|
| Auth log | `/var/log/auth.log` | SSH logons, sudo usage, PAM events |
| Syslog | `/var/log/syslog` | General system events |
| Journal | `journalctl` | Systemd-based unified logging |

## Common detections

- **Brute force:** repeated `Failed password` entries in `auth.log` from one source IP within a short window — same pattern as Windows 4625, different log format
- **Privilege escalation:** unauthorized `sudo` usage — check `COMMAND=` field in auth.log sudo entries
- **Persistence:** new cron jobs (`/etc/cron.d/`, `crontab -l`), new systemd services, modified shell profile files (`.bashrc`, `.bash_profile`)

## Connects to SecureWatch

This is exactly the detection logic SecureWatch implements — `brute_force.py` and `priv_esc.py` parse these same auth-log patterns programmatically rather than manually grepping.
