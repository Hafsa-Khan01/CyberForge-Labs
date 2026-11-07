# Week 03 — Event ID & Snort SID Lookup

A compact lookup table for triage. Use the main [SOC Analyst Quick Reference](./Week-03-Endpoint-and-Network-Detection-Cheat-Sheet.md) for commands, auditd queries, Nmap validation and investigation workflow.

## Windows Security

| Event ID | Meaning | First fields to inspect |
|---|---|---|
| 4624 | Successful logon | Target account, logon type, source address, workstation |
| 4625 | Failed logon | Account, failure reason/status, source address |
| 4688 | Process creation (audit policy dependent) | New process, creator process, command line if enabled |
| 4720 | User account created | New account, actor/subject, host, timestamp |

## Sysmon

| Event ID | Meaning | First fields to inspect |
|---|---|---|
| 1 | Process creation | Image, command line, parent image, user, hashes |
| 3 | Network connection | Process, protocol, source/destination IP and port |
| 7 | Image/DLL load | Image, loaded module, process |
| 11 | File creation | Target filename, process, timestamp |
| 12 | Registry object create/delete | Event type, registry target, process |
| 13 | Registry value set | Target object, value name, writing process |
| 22 | DNS query | Query name, requesting process, query status/results |

Sysmon coverage is configuration-dependent. An absent event is not proof that the activity did not occur.

## Linux auditd

| Record type | Meaning |
|---|---|
| SYSCALL | System-call metadata and process/identity context |
| EXECVE | Command and arguments |
| PATH | Filesystem object involved |
| CWD | Working directory |
| USER_AUTH | Authentication-related activity |
| USER_LOGIN | Login/session-related activity |
| CONFIG_CHANGE | Audit configuration/rule change |

Correlate records with the same audit serial identifier; one logical event can contain several record types.

## Snort local lab SIDs

| SID | Rule purpose | Do not overstate |
|---|---|---|
| 1000001 | ICMP echo traffic | Does not establish hostile intent |
| 1000002 | TCP traffic destined for SSH/22 | Does not prove an SSH login succeeded |
| 1000003 | TCP traffic destined for HTTP/80 | Does not prove an HTTP exploit |
| 1000004 | Thresholded SYN scan-like activity | Does not uniquely identify Nmap |

## MITRE ATT&CK

| ID | Technique |
|---|---|
| T1046 | Network Service Discovery |
| T1110 | Brute Force |
| T1136 | Create Account |
| T1547.001 | Registry Run Keys / Startup Folder |

Map techniques only when observed behavior supports the mapping. An event ID or alert alone is not a complete finding.

## Triage reminders

1. Confirm timestamp, timezone, host and data source.
2. Identify the account, process and network endpoints.
3. Correlate related events using process identifiers, timestamps and audit serials.
4. Check configuration and telemetry coverage before treating missing events as meaningful.
5. Preserve evidence and document confidence, benign explanations and limitations.
