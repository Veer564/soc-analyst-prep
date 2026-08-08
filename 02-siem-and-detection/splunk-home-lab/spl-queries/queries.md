# SOC dashboard — SPL queries

Five queries built for the home-lab dashboard, covering the detections the attack simulation is designed to trigger.

> Replace the placeholders below with your actual saved SPL — this file is the structure, drop your real queries in.

## 1. Failed logon volume (brute force indicator)
```spl
index=security EventCode=4625
| stats count by src_ip, Account_Name
| where count > 5
```

## 2. Explicit credential use (4648)
```spl
index=security EventCode=4648
| table _time, Subject_Account_Name, Account_Name, Target_Server_Name
```

## 3. New scheduled task creation (4698 — persistence)
```spl
index=security EventCode=4698
| table _time, Task_Name, Command
```

## 4. New service installed (7045 — persistence)
```spl
index=system EventCode=7045
| table _time, Service_Name, Service_File_Name
```

## 5. Logon ID pivot (session reconstruction)
```spl
index=security Logon_ID=$logon_id$
| sort _time
| table _time, EventCode, Account_Name, Logon_Type
```

## Notes

Query 5 is the one that actually matters most — it's the Logon ID correlation habit from the Windows event ID notes, implemented as a reusable dashboard drill-down rather than a manual pivot.
