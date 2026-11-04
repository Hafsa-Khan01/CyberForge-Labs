# Q8. Windows Event Log vs Sysmon vs Linux auditd

| Feature | Windows Event Log | Sysmon | Linux auditd |
|---|---|---|---|
| What it captures | Operating-system, application, and security events from Windows components and applications | Detailed Windows activity such as process creation, network connections, file creation, registry changes, and DNS queries | Configured Linux security/audit activity, including syscalls, executions, authentication, and watched file operations |
| Main purpose | General Windows event recording and security auditing | Enrich Windows endpoint visibility for monitoring and investigation | Record security-relevant actions according to audit rules |
| Log format | Windows Event Log records, commonly viewed as rendered events or XML | Windows Event Log records in the Sysmon Operational channel, with event-specific fields | Structured audit records, often multiple related records sharing one event serial |
| Typical location | Event Viewer channels such as Security, System, and Application | Applications and Services Logs → Microsoft → Windows → Sysmon → Operational | Commonly `/var/log/audit/audit.log` |
| Configuration | Windows logging policy, audit policy, and application settings | Sysmon installation and its XML configuration | Audit rules and audit daemon configuration |
| SOC use case | Logon investigation, account changes, policy and service events | Process trees, command lines, network activity, DNS and file/registry investigation | Linux command execution, identity/authentication, privileged activity, and file access |

## How they complement one another
- Windows Security logs can show a successful or failed logon.
- Sysmon can add process and network details around that logon.
- Linux auditd can provide comparable audit visibility for selected actions on Linux hosts.
- A SIEM can normalize and correlate these sources, while preserving source-specific fields for investigation.

## Caveats
Coverage depends on audit policy, Sysmon configuration, audit rules, retention, and forwarding health. No single source records every action. Analysts should understand the configuration and limitations before interpreting an absence of events.
