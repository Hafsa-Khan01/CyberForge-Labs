# Week 2 — Practical Lab Guide

## 1. Wireshark Protocol Observation
In an authorized isolated lab:
1. Start a capture on the correct lab interface.
2. From the Kali test VM, perform permitted ping, DNS lookup and HTTP request activity against the Ubuntu lab host.
3. Identify DNS query/response, ICMP echo traffic, TCP handshake packets and HTTP request/response where applicable.
4. Save the capture as PCAP/PCAPNG and note the exact display filters used.

Do not claim a packet was observed unless it appears in the saved capture.

## 2. Nmap Evidence
Run only against the assigned Ubuntu and Windows lab targets. Where permitted, practice host discovery, SYN/connect scanning, service detection and OS detection. Save normal and XML outputs. For a SYN scan, the Wireshark display filter is:
`tcp.flags.syn == 1 && tcp.flags.ack == 0`

Record actual target addresses, command lines, timestamps, discovered ports and service/version output. Never fabricate scan results.

## 3. Windows Event Review
Use a disposable, authorized Windows VM to review successful/failed logons, account creation, group membership changes and service installation events. Event 1102 indicates the Security audit log was cleared; do not clear logs on production or third-party systems. Any deliberate log-clear demonstration must be limited to an explicitly authorized disposable VM.

## 4. PowerShell Event Export
Example query pattern (run elevated if required and permitted):
```powershell
$events = Get-WinEvent -FilterHashtable @{
  LogName = 'Security'
  Id = 4625
} -ErrorAction SilentlyContinue

$events | Select-Object TimeCreated, Id, ProviderName, MachineName, Message |
  Export-Csv -Path .\failed-logons.csv -NoTypeInformation
```
Review the exported data and group failures by account only after validating the event message fields. Preserve the original export and document any parsing limitations.

## 5. Evidence Checklist
- Wireshark PCAP/PCAPNG and screenshots of relevant packets.
- Nmap normal and XML outputs, commands and target scope.
- Windows Event Viewer screenshots with sensitive values redacted.
- PowerShell CSV export and analysis notes.
- Separate room writeups and completion evidence.
