# Practical Write-up — Ubuntu auditd

**Platform:** Ubuntu VM  
**Tool:** Linux Audit daemon (auditd)  
**Status:** User reports the practical was completed; preserve the VM's original command output and screenshots as the evidence of execution.

## Objective
Capture security-relevant Linux activity through kernel audit records and inspect the resulting events.

## Setup and service verification
Typical installation and service checks:
```bash
sudo apt-get update
sudo apt-get install -y auditd audispd-plugins
sudo systemctl enable auditd --now
sudo systemctl status auditd
```

## Example targeted execution rule
A key-based search only returns events associated with a rule carrying that key. Installing a package alone does not automatically create an audit key named `nano`.

Example rule to monitor execution of the nano binary (confirm the binary path with `command -v nano`):
```bash
command -v nano
sudo auditctl -w /usr/bin/nano -p x -k nano_exec
sudo ausearch -k nano_exec -i
```

Alternatively, inspect recent execution records:
```bash
sudo ausearch -m EXECVE -ts recent -i
```

## What to inspect
- `type`: record type, such as SYSCALL, EXECVE, PATH or CWD.
- `msg`: audit event identifier and timestamp.
- `exe`: executable path.
- `comm`: command name.
- `uid`, `euid`, `auid`: real, effective and audit login identities.
- `pid`, `ppid`: process and parent process identifiers.
- `success` and `exit`: syscall outcome.

## Analysis
An audit event may comprise multiple records with the same audit event serial. Correlate those records to reconstruct the action. Use the login identity (auid) and effective identity (euid) together when investigating privilege changes.

## Evidence
Place the actual Ubuntu screenshots in `Findings/Ubuntu/auditd/`: service status, active audit rule, generated test action and corresponding `ausearch` result. Replace example paths or commands in this document if the executed lab used a different rule.
