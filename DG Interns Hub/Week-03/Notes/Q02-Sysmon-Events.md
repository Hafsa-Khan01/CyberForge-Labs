# Q2. Sysmon and Windows Event Logging

## What is Sysmon?
System Monitor (Sysmon), part of Microsoft Sysinternals, is a Windows system service and driver that records detailed system activity into the Windows Event Log. It is designed to provide richer telemetry for security monitoring and investigations. A configuration file controls which event categories are collected and filtered.

Standard Windows Event Logs already record operating-system, application, and security events. Sysmon complements them with more detailed event records for process creation, network connections, file creation, DNS queries, and other activity. Sysmon does not replace the Security, System, or Application logs.

## Important Sysmon Event IDs

| Event ID | Event name | What it records | SOC value |
|---:|---|---|---|
| 1 | Process Create | New process, image, command line, hashes (when configured), parent process, user, and process identifiers | Investigate suspicious execution and process chains |
| 3 | Network Connection | TCP/UDP network connection associated with a process, including source/destination details where available | Correlate a process with remote communication |
| 11 | File Create | File creation activity, including target filename and process context | Investigate dropped files and unexpected writes |
| 13 | Registry Value Set | Registry value modification | Investigate configuration changes and possible persistence |
| 22 | DNS Query | DNS query activity, including queried name and process context | Investigate unusual domains and possible DNS-based command-and-control |

## Important configuration caveat
Sysmon event collection depends on its active configuration. Event ID 3 (Network Connection), for example, may be disabled or filtered by a configuration. A missing event does not automatically prove that the activity did not occur. Check the configuration, service state, event channel, and time window.

## Where to find events
Event Viewer → Applications and Services Logs → Microsoft → Windows → Sysmon → Operational.

PowerShell can also query the channel, for example:

```powershell
Get-WinEvent -LogName 'Microsoft-Windows-Sysmon/Operational' -MaxEvents 20
```

## SOC example
If a suspicious executable launches PowerShell and then contacts an unfamiliar external address, Event ID 1 can show process context while Event ID 3 may show network activity. Analysts correlate timestamps, process GUIDs, users, and destination information rather than treating each event in isolation.
