# Q3. Linux auditd and syslog

## What is auditd?
The Linux Audit system records security-relevant activity through kernel audit mechanisms. The `auditd` daemon receives audit records and writes them to the configured audit log, commonly `/var/log/audit/audit.log`. Audit rules determine which activities are watched—for example, selected system calls, file access, identity changes, or command execution. Tools such as `ausearch` search records and `aureport` summarize them.

## How it works
1. An administrator configures audit rules using audit rule files or commands.
2. The kernel generates audit records when monitored activity occurs.
3. The audit subsystem sends records to the audit daemon.
4. `auditd` writes records to the audit log.
5. Analysts search and correlate records using timestamps, event serials, users, executable paths, and other fields.

An audit event can consist of multiple related records sharing the same audit timestamp/serial identifier. Interpret the complete event, not just one line.

## auditd compared with syslog

| Area | auditd | syslog |
|---|---|---|
| Primary purpose | Security auditing of configured system activity | General system, service, and application logging |
| Data source | Linux kernel audit subsystem and audit rules | Applications, services, daemons, and system components |
| Content | Audit record types, IDs, syscall/executable context, UID/GID, paths, results | Human-readable or structured messages with facility, severity, timestamp, and host context |
| Configuration | Audit rules and audit daemon settings | Syslog daemon rules, facilities, priorities, and destinations |
| Common location | `/var/log/audit/audit.log` | Often `/var/log/syslog` or distribution-specific locations |
| SOC use | Trace selected privileged actions, executions, authentication, and file access | Monitor service health, application messages, and general system events |

## Common audit fields

| Field | Meaning / value to an analyst |
|---|---|
| `type` | Record category, such as SYSCALL, EXECVE, PATH, USER_AUTH, or USER_LOGIN |
| `msg` | Includes audit timestamp and serial identifier used to correlate records |
| `exe` | Executable path involved in an event, when present |
| `comm` | Command name associated with the process |
| `uid`, `euid` | Real and effective user IDs |
| `gid`, `egid` | Real and effective group IDs |
| `auid` | Login/audit user identity, useful for tracing the original session |
| `success`, `exit` | Indicates operation outcome and return status, when present |
| `name` / PATH fields | File path involved in the audited operation, when present |

## Important practical note
`ausearch -k nano` only finds events tagged with the key `nano`. Installing nano does not automatically create that key. Configure a suitable audit rule first, or search recent EXECVE records and inspect the matching event. Availability and exact fields vary by distribution and audit rule.
