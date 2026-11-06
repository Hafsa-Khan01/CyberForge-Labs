# Practical Write-up — Windows Sysmon

**Platform:** Windows VM  
**Tool:** Microsoft Sysmon 15.22  
**Configuration:** SwiftOnSecurity Sysmon configuration  
**Status:** Practical execution and event generation confirmed.

## Objective
Collect endpoint telemetry and inspect process, network, file, registry and DNS activity using Sysmon's Operational event channel.

## Setup and verification
- Sysmon was installed using the 64-bit Sysmon executable and the SwiftOnSecurity configuration.
- The Sysmon64 service was verified as running.
- The event channel `Microsoft-Windows-Sysmon/Operational` was available.
- Configuration SHA-256 recorded during setup: `055FEBC600E6D7448CDF3812307275912927A62B1F94D0D933B64B294BC87162`.

## Verified event observations

| Event ID | Event type | Observation | SOC relevance |
|---|---|---|---|
| 1 | ProcessCreate | Process creation events included Notepad and other Windows/Edge processes. | Establish process lineage and inspect image, command line, user and parent process. |
| 3 | NetworkConnect | PowerShell made a TCP connection to `142.250.202.142:443`; the observed source address was `192.168.100.33`. | Correlate a process with remote network activity. |
| 11 | FileCreate | PowerShell created `C:\Users\hiras\Desktop\Week3-Sysmon-Test.ps1`. | Identify file drops and associate them with the creating process and user. |
| 13 | RegistryEvent / SetValue | Microsoft Edge set a Run-key value for `MicrosoftEdgeAutoLaunch`; process was `msedge.exe`. | Review startup configuration changes. This event was consistent with a legitimate Edge auto-launch entry and is not proof of compromise. |
| 22 | DNS query | PowerShell queried `google.com`; query status was 0. | Link DNS activity to the process and investigate unusual domains. |

## Event ID 13 detail
The event recorded a SetValue operation under the user's Run registry key. The value data launched Microsoft Edge with `--win-session-start`. Run-key modifications can be relevant to ATT&CK T1547.001 (Registry Run Keys / Startup Folder), but this observed vendor application entry is not, by itself, malicious.

## Configuration lesson
The initial plain-text test file did not trigger Event ID 11 under the selected SwiftOnSecurity filters. A PowerShell `.ps1` test file did trigger Event ID 11. FileCreate coverage depends on the active configuration and file-type filters; absence of an event for an excluded extension is not evidence that Sysmon is broken.

## Verification commands
```powershell
Get-Service *Sysmon*
Get-WinEvent -LogName 'Microsoft-Windows-Sysmon/Operational' -MaxEvents 20
Get-WinEvent -FilterHashtable @{
    LogName = 'Microsoft-Windows-Sysmon/Operational'
    Id = 13
    StartTime = (Get-Date).AddMinutes(-15)
} -MaxEvents 5 | Format-List TimeCreated, Id, Message
```

## Evidence
Attach the original screenshots for service status and Event IDs 1, 3, 11, 13 and 22 in the repository's `Findings/Windows/` folder. Screenshots must be captured from the actual VM and must not expose credentials or unrelated personal data.
