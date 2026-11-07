# Linux Security Auditing with auditd

**Platform:** Ubuntu VM  
**Component:** Linux Audit daemon (`auditd`)  
**Default log location:** `/var/log/audit/audit.log`

## Objective
Review the Linux Audit subsystem, its service/package state, audit rule workflow and the structure of records used to investigate security-relevant host activity.

## Installation and service checks
The following commands are useful when setting up and validating auditd on a compatible Ubuntu system:

```bash
sudo apt-get update
sudo apt-get install -y auditd audispd-plugins
sudo systemctl enable auditd --now
sudo systemctl status auditd
```

Package installation, service availability, service state, loaded rules and recorded events are separate validation points. A package-installation message does not establish that the daemon is active, and a service status alone does not prove that a particular event was recorded.

## Targeted execution monitoring — reference workflow
The example below adds a temporary execution watch for the `nano` binary. Confirm the actual executable path first; the watch must match the path returned by `command -v`.

```bash
command -v nano
sudo auditctl -w /usr/bin/nano -p x -k nano_exec
nano
sudo ausearch -k nano_exec -i
```

Remove the temporary rule after testing:

```bash
sudo auditctl -W /usr/bin/nano -k nano_exec
```

These commands describe a repeatable workflow. They should only be reported as completed when the corresponding terminal output and matching audit record have been captured.

## Useful audit inspection commands

```bash
sudo auditctl -s
sudo auditctl -l
sudo ausearch -ts recent
sudo ausearch -m USER_AUTH,USER_LOGIN
sudo ausearch -m EXECVE -ts recent -i
sudo less /var/log/audit/audit.log
```

## Important audit fields

| Field | Description |
|---|---|
| `type` | Record type, such as SYSCALL, EXECVE, PATH or CWD |
| `msg` | Audit timestamp and event serial identifier |
| `exe` | Executable path |
| `comm` | Command name |
| `uid` / `euid` | Real and effective user IDs |
| `auid` | Login identity associated with the audit session |
| `pid` / `ppid` | Process and parent process identifiers |
| `success` / `exit` | System-call outcome |

## Record correlation
One logical audit event can contain multiple records sharing the same audit event serial number. Correlate SYSCALL, EXECVE, PATH and CWD records by their event identifier before interpreting the operation. The `auid` field can help identify the original login identity when a process performs actions after a privilege change.

## Evidence and scope
The currently published [Evidence](../Evidence/) captures show:

- [12 — auditd service-unit status](../Evidence/12-Ubuntu-auditd-Service-Unit-Status.png)
- [13 — auditd package installation output](../Evidence/13-Ubuntu-auditd-Package-Installation-Output.jpeg)
- [14 — systemd service inventory](../Evidence/14-Ubuntu-Systemd-Service-Inventory.jfif)
- [16 — active systemd units](../Evidence/16-Ubuntu-Systemd-Active-Units-Listing.png)

The service-unit capture reports that `auditd.service` was not found at the time of that capture. The published screenshots do not include a clear matching `ausearch` result or audit event record; therefore, they are not presented as proof of successful audit-event collection.