# Q9. Key Linux log files for SOC monitoring

Linux log paths vary by distribution, logging daemon, and service configuration. The following are common paths on Debian/Ubuntu-style systems; a file may be absent or replaced by journald or another configured destination.

| Log file path | Purpose | Common events / SOC value |
|---|---|---|
| `/var/log/auth.log` | Authentication and authorization messages on many Debian/Ubuntu systems | SSH logins, sudo activity, authentication failures, session events |
| `/var/log/syslog` | General system and service messages on many Debian/Ubuntu systems | Daemon messages, scheduled jobs, service warnings, system activity |
| `/var/log/audit/audit.log` | Linux Audit subsystem records when auditd is configured | Syscalls, command execution, authentication records, watched file activity |
| `/var/log/kern.log` | Kernel-related messages on systems configured to write this file | Kernel warnings, driver/device messages, firewall or network-stack messages |
| `/var/log/apache2/access.log` | Apache HTTP access requests on common Debian/Ubuntu layouts | Client address, request, status code, user agent, request timing depending on format |

## SOC monitoring priorities
- Authentication failures followed by success from the same source.
- Unexpected sudo use or privilege changes.
- New or unusual services and scheduled tasks.
- Repeated HTTP errors, suspicious paths, unusual user agents, and request bursts.
- Kernel or network errors that coincide with suspicious endpoint activity.
- Audit events for unexpected command execution or sensitive file access.

## Verify actual paths
Use the system's logging configuration and commands such as:

```bash
ls -l /var/log
sudo journalctl --since "1 hour ago"
sudo systemctl status rsyslog
sudo systemctl status auditd
```

Do not assume every listed file exists. Record the distribution and actual logging configuration in the practical writeup.
