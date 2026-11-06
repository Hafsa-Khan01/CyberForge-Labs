# Week 3 Cheat Sheet — Endpoint and Network Detection

## Windows Security and Sysmon

| Event ID / Record | Source | Meaning | SOC use |
|---|---|---|---|
| 4624 | Windows Security | Successful logon | Establish normal and suspicious logon patterns |
| 4625 | Windows Security | Failed logon | Detect password guessing and account misuse |
| 4688 | Windows Security | Process creation (when auditing is enabled) | Investigate process execution and parent-child context |
| 4720 | Windows Security | User account created | Review unexpected account creation |
| 1 | Sysmon | Process creation | Inspect image, command line, parent, user, hashes |
| 3 | Sysmon | Network connection | Correlate process-to-destination network activity |
| 7 | Sysmon | Image/DLL loaded (when configured) | Investigate unusual module loading |
| 11 | Sysmon | File created | Track suspicious file drops and staging |
| 12 | Sysmon | Registry object create/delete | Review registry persistence-related changes |
| 13 | Sysmon | Registry value set | Investigate Run-key and other registry modifications |
| 22 | Sysmon | DNS query | Correlate process with queried domains and DNS results |

## Linux auditd record types

| Record type | Meaning | SOC use |
|---|---|---|
| SYSCALL | System call details | Identify executable, syscall, success, UID and process |
| EXECVE | Executed command arguments | Reconstruct command execution |
| PATH | File/path object associated with an event | Identify affected files and inode details |
| CWD | Current working directory | Add execution context |
| USER_AUTH | User authentication activity | Investigate authentication attempts |
| USER_LOGIN | Login/session activity | Track session creation and identity |
| CONFIG_CHANGE | Audit configuration/rule changes | Detect changes to audit coverage |

Audit events can consist of multiple records sharing the same audit event serial number. Correlate records by the common audit message identifier rather than treating each line as a separate action.

## Snort rule IDs used in the lab

| SID | Rule purpose | Interpretation |
|---|---|---|
| 1000001 | ICMP echo traffic | Visibility of ping activity |
| 1000002 | TCP traffic to SSH port 22 | SSH connection attempt indicator |
| 1000003 | TCP traffic to HTTP port 80 | HTTP traffic indicator |
| 1000004 | SYN scan threshold | Possible network service discovery / T1046 |

## Quick investigation workflow

1. Validate the alert source, timestamp, sensor, and rule.
2. Identify the endpoint, account, process, source and destination.
3. Correlate Windows/Sysmon, auditd, DNS, firewall and network telemetry.
4. Establish whether the activity is expected and authorized.
5. Preserve relevant event records and document evidence.
6. Map behavior to MITRE ATT&CK only when the observed behavior supports the mapping.
7. Record conclusion, confidence, false-positive considerations and follow-up.

## Interpretation cautions

- A single Sysmon Event ID 13 does not prove malicious persistence. Legitimate software also writes Run-key values.
- Sysmon Event ID 3 is configuration-dependent; absence of an event does not prove no connection occurred.
- auditd records may be split across SYSCALL, EXECVE, PATH and CWD lines.
- A SYN-based Snort rule can detect scan-like behavior but cannot uniquely identify Nmap.
- Tune thresholds to the lab's traffic rate and validate rule compatibility with the installed Snort version.
