# Windows Endpoint Telemetry with Sysmon

**Platform:** Windows 64-bit VM  
**Tool:** Microsoft Sysmon 15.22  
**Configuration:** SwiftOnSecurity Sysmon configuration  
**Event channel:** `Microsoft-Windows-Sysmon/Operational`

## Objective
Configure Sysmon to collect detailed endpoint telemetry and examine process, network, file, registry and DNS activity through the Windows event channel.

## Deployment and validation
Sysmon was installed with the 64-bit executable and the selected SwiftOnSecurity configuration. The Sysmon64 service was verified as running, and the Operational event channel was available.

**Configuration SHA-256**

`055FEBC600E6D7448CDF3812307275912927A62B1F94D0D933B64B294BC87162`

## Event analysis

| Event ID | Event type | Observed telemetry | Investigation value |
|---|---|---|---|
| 1 | ProcessCreate | Process creation records included Notepad and Windows/Edge processes. | Review image path, command line, user, parent process and hashes. |
| 3 | NetworkConnect | PowerShell initiated a TCP connection to `142.250.202.142:443`; source address recorded as `192.168.100.33`. | Associate outbound network activity with the originating process. |
| 11 | FileCreate | PowerShell created `C:\Users\hiras\Desktop\Week3-Sysmon-Test.ps1`. | Identify file creation, process attribution and file path. |
| 13 | RegistryEvent / SetValue | Microsoft Edge set a user Run-key value for its auto-launch command. | Review startup configuration changes and validate the owning application. |
| 22 | DNS query | PowerShell queried `google.com`; query status was `0`. | Correlate domain lookups with process and network activity. |

## Registry event assessment
Event ID 13 recorded a SetValue operation under the user's Run registry key. The value data referenced Microsoft Edge with the `--win-session-start` argument. Run-key changes can be relevant to persistence investigations, including MITRE ATT&CK T1547.001; however, this specific Edge auto-launch entry is not, by itself, evidence of malicious activity.

## Configuration observation
The plain-text test file did not generate the expected Event ID 11 under the active SwiftOnSecurity filters, while the PowerShell `.ps1` test file did. Sysmon event coverage depends on the active configuration and its file-type filters. An event that is not collected by a filter should not be interpreted as proof that the underlying activity did not occur.

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
Store the original service-status and Event Viewer captures under `Findings/Windows/Sysmon/`. Retain the event ID, timestamp and relevant event fields in each capture.
