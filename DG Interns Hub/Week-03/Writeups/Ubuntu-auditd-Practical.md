# Linux Security Auditing with auditd

**Platform:** Ubuntu VM  
**Component:** Linux Audit daemon (`auditd`)  
**Log location:** `/var/log/audit/audit.log`

## Objective
Use the Linux Audit subsystem to record selected security-relevant activity and inspect the resulting audit records.

## Service installation and validation
```bash
sudo apt-get update
sudo apt-get install -y auditd audispd-plugins
sudo systemctl enable auditd --now
sudo systemctl status auditd
```

## Targeted execution monitoring
The following example monitors execution of the `nano` binary. Confirm the executable path on the system before adding the rule.

```bash
command -v nano
sudo auditctl -w /usr/bin/nano -p x -k nano_exec
nano
sudo ausearch -k nano_exec -i
```

The watch path must match the executable path returned by `command -v`. A key-based search returns events associated with a rule carrying that key; installing a package alone does not create an audit key.

## Inspecting recent execution records
```bash
sudo ausearch -m EXECVE -ts recent -i
sudo tail -n 40 /var/log/audit/audit.log
```

## Important audit fields

| Field | Description |
|---|---|
| `type` | Record type, such as SYSCALL, EXECVE, PATH or CWD |
| `msg` | Audit event identifier and timestamp |
| `exe` | Executable path |
| `comm` | Command name |
| `uid` / `euid` | Real and effective user IDs |
| `auid` | Login identity associated with the audit session |
| `pid` / `ppid` | Process and parent process identifiers |
| `success` / `exit` | System-call outcome |

## Analysis
A single audit event can be represented by several records sharing the same audit event serial number. SYSCALL, EXECVE, PATH and CWD records should therefore be correlated before drawing conclusions about a command or file operation. The audit login identity (`auid`) is useful when examining actions performed after privilege changes.

## Evidence
Retain the original terminal captures for auditd service status, the active rule, the test action and its corresponding `ausearch` output in `Findings/Ubuntu/auditd/`.
