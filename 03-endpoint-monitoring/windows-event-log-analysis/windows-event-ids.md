# Windows Event ID cheat sheet — the ones I actually use

Not a copy of Microsoft's full list — just the IDs I've found myself reaching for repeatedly during triage, with the context that matters for each.

| Event ID | Name | Why it matters |
|---|---|---|
| **4624** | An account was successfully logged on | Baseline for all logon analysis. Useless alone — the **Logon Type** field is what makes it meaningful (see below). |
| **4625** | An account failed to log on | Brute-force / password-spray indicator when volume is high from one source. Check the **Failure Reason** subcode, not just the count. |
| **4648** | A logon was attempted using explicit credentials | Fires on `runas`, scheduled tasks running as another user, or lateral movement using stolen creds. Legit admin activity looks identical to an attacker doing this — context (time, source, target) is everything. |
| **4672** | Special privileges assigned to new logon | Fires whenever an admin-equivalent account logs on. Correlate with 4624 using the same Logon ID to confirm *which* logon got the elevated rights. |
| **4688** | A new process has been created | Process-creation visibility — pairs with command-line auditing (must be enabled separately via GPO) to see what was actually run, not just that something ran. |
| **4698** | A scheduled task was created | Common persistence mechanism. Legit software installs create these too — check the task's action/command, not just the fact it exists. |
| **7045** | A new service was installed | Another persistence favorite. Watch for services with random-looking names or binaries running from `%TEMP%` / `AppData`. |
| **5140** | A network share object was accessed | SMB share access — useful for spotting lateral movement or data staging (e.g. repeated access to `ADMIN$` or `C$` from a workstation that has no business touching them). |

## The habit that actually matters: Logon ID correlation

Every logon event gets a **Logon ID** (a hex value, e.g. `0x3e7`) that's shared across every event tied to that specific session — the 4624, any 4672 special-privilege assignment, any 4688 process creations under that session, and the eventual 4634 logoff.

**Why this is the skill, not the event IDs themselves:** a single 4624 tells you almost nothing in isolation. Pivoting on the Logon ID across the full session tells you the actual story — what logged on, what it did, what it touched, when it left. This is the difference between "I saw a suspicious logon" and "I can show you everything that logon did."

Current gap I'm closing: making this pivot automatic during triage instead of remembering to do it after the fact.

## Logon types (goes with 4624/4625)

| Type | Meaning |
|---|---|
| 2 | Interactive (console logon) |
| 3 | Network (e.g. accessing a share) |
| 4 | Batch |
| 5 | Service |
| 7 | Unlock |
| 8 | NetworkCleartext |
| 9 | NewCredentials (e.g. `runas /netonly`) |
| 10 | RemoteInteractive (RDP) |
| 11 | CachedInteractive |

Type 10 (RDP) combined with an off-hours timestamp and an unfamiliar source IP is one of the highest-signal combinations for initial triage.
