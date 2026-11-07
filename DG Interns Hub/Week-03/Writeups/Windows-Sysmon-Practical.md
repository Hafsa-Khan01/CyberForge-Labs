# Windows Endpoint Telemetry with Sysmon

**Platform:** Windows 64-bit VM  
**Tool:** Microsoft Sysmon 15.22  
**Configuration:** SwiftOnSecurity Sysmon configuration  
**Event channel:** `Microsoft-Windows-Sysmon/Operational`

## Objective
Establish endpoint visibility with Sysmon and examine selected process, network, file, registry and DNS telemetry in the Windows Event Log.

## Deployment and validation
Sysmon was installed with the 64-bit executable and the selected SwiftOnSecurity configuration. The Sysmon64 service and the Operational event channel were checked.

**Configuration SHA-256**

`055FEBC600E6D7448CDF3812307275912927A62B1F94D0D933B64B294BC87162`

## Event review

| Event ID | Event type | Observed record | SOC investigation value |
|---|---|---|---|
| 1 | ProcessCreate | Records included Notepad and Windows/Edge processes. | Review image, command line, parent process, user and hashes. |
| 3 | NetworkConnect | PowerShell initiated a TCP connection to `142.250.202.142:443`; source address was `192.168.100.33`. | Associate outbound connections with the originating process. |
| 11 | FileCreate | PowerShell created `C:\Users\hiras\Desktop\Week3-Sysmon-Test.ps1`. | Establish file path, creating process and event time. |
| 13 | RegistryEvent / SetValue | Microsoft Edge set a user Run-key value for its auto-launch command. | Review startup changes in application and user context. |
| 22 | DNS query | PowerShell queried `google.com`; query status was `0`. | Correlate DNS activity with the requesting process and subsequent connections. |

## Registry event assessment
Event ID 13 recorded a SetValue operation under the user's Run registry key. The value data referenced Microsoft Edge with the `--win-session-start` argument. Run-key changes can be relevant to MITRE ATT&CK T1547.001 investigations, but this observed Edge auto-launch value is not, by itself, evidence of malicious persistence. Validate the executable path, signer, writing process, user and surrounding activity.

## Configuration observation
The plain-text test file did not generate the expected Event ID 11 under the active SwiftOnSecurity filters, while the PowerShell test file did. Sysmon visibility depends on the active configuration and its filters. An event excluded by configuration must not be interpreted as proof that the underlying activity did not occur.

## Useful verification commands
These are repeatable reference commands; output should be captured from the target VM when reproducing the checks.

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
Original screenshots are stored in [Evidence](../Evidence/):

- [01 — Sysmon installation and configuration](../Evidence/01-Windows-Sysmon-Installation-and-Configuration.jpeg)
- [02 — Process creation and DNS event view](../Evidence/02-Sysmon-Event-ID-1-Process-Creation-and-DNS-Events.jpeg)
- [03 — Event ID 1 and 22 details](../Evidence/03-Sysmon-Event-ID-1-and-22-Event-Details.jpeg)
- [04 — Event ID 11 file creation](../Evidence/04-Sysmon-Event-ID-11-File-Creation.jpeg)
- [05 — Event ID 13 registry value set](../Evidence/05-Sysmon-Event-ID-13-Registry-Value-Set.jpeg)
- [06 — Sysmon service and configuration verification](../Evidence/06-Sysmon-Service-and-Configuration-Verification.jpeg)

Interpret each capture only for the event or status visible in that image.