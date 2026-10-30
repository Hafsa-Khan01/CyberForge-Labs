# Week 2 — Windows Security Event ID Cheat Sheet

| Event ID | Meaning | Investigation focus |
|---:|---|---|
| 4624 | Successful logon | Account, logon type, source, time |
| 4625 | Failed logon | Target account, failure reason, source |
| 4634 | Logoff | Session and timing |
| 4648 | Explicit credentials used | Process, account and target |
| 4672 | Special privileges assigned | Whether privileged logon is expected |
| 4688 | Process created | Image, parent process, command line if enabled |
| 4697 | Service installed (Security) | Service name, account, installer context |
| 4720 | User account created | Creator, new account, time |
| 4722 | User account enabled | Who enabled it and why |
| 4724 | Password reset attempt | Initiator and target account |
| 4732 | Member added to local security group | Group, member and actor |
| 4768 | Kerberos TGT requested | Account, client address, result |
| 4769 | Kerberos service ticket requested | Account, service, encryption and source |
| 4776 | NTLM credential validation | Account, workstation and result |
| 1102 | Security audit log cleared | Actor and surrounding activity |

**Related System event:** 7045 commonly records service installation in the System log. It is not the same event as Security event 4697.

## Logon Types
| Type | Description |
|---:|---|
| 2 | Interactive |
| 3 | Network |
| 4 | Batch |
| 5 | Service |
| 7 | Unlock |
| 10 | Remote interactive (RDP) |
| 11 | Cached interactive |

## Analyst Notes
Correlate event IDs with host, account, source IP, timestamp, logon type and related events. Establish a baseline before deciding an event is suspicious. Event IDs alone are not proof of malicious activity.
