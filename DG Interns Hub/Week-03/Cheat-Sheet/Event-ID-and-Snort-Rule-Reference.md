# Week 03 — Event ID & Rule Cheat Sheet

| Event ID / Rule | Source | What It Means | When to Use It |
|---|---|---|---|
| 4624 | Windows Security | Successful logon | Establish normal access and investigate unusual logons |
| 4625 | Windows Security | Failed logon | Identify password guessing or brute-force patterns |
| 4688 | Windows Security | Process creation, when auditing is enabled | Review executable launches and parent/child activity |
| 4720 | Windows Security | User account created | Investigate unexpected account creation; correlate actor and host |
| 1 | Sysmon | Process Create | Review image, command line, parent process, user and hashes |
| 3 | Sysmon | Network Connection | Associate a process with network endpoints; config-dependent |
| 11 | Sysmon | File Create | Track created files and possible payload staging |
| 22 | Sysmon | DNS Query | Investigate queried domains and requesting process |
| 13 | Sysmon | Registry Value Set | Review selected registry value modifications |
| EXECVE | Linux audit | Executed command arguments | Reconstruct command execution with related audit records |
| USER_LOGIN | Linux audit | Login-related event | Review login outcome and identity context |
| USER_AUTH | Linux audit | Authentication attempt | Investigate authentication success/failure |
| 1000001 | Snort | ICMP Ping Detected | Observe ICMP traffic directed to HOME_NET |
| 1000002 | Snort | SSH Connection Attempt | Observe TCP traffic destined for port 22 |
| 1000003 | Snort | HTTP Traffic | Observe TCP traffic destined for port 80 |
| 1000004 | Snort | Thresholded SYN scan-like activity | Investigate scan behavior mapped to T1046 |

## Analyst cautions
- Windows Security event availability depends on Advanced Audit Policy settings.
- Sysmon coverage depends on its active configuration; missing events do not prove no activity.
- Linux audit events may span multiple records sharing one serial number; correlate them.
- The starter Snort rules are broad indicators, not proof of malicious activity.
- A SYN threshold can identify scan-like behavior but cannot uniquely identify Nmap.

## MITRE references
- T1046 — Network Service Discovery: https://attack.mitre.org/techniques/T1046/
- T1110 — Brute Force: https://attack.mitre.org/techniques/T1110/
- T1136 — Create Account: https://attack.mitre.org/techniques/T1136/
