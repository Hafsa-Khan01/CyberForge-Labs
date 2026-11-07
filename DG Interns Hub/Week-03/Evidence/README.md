# Week 03 — Practical Evidence

This directory contains the original screenshots retained for the Week 03 practical work. The descriptions below identify what is visible in each capture; they do not extend beyond the evidence shown.

## Evidence index

| File | Visible evidence |
|---|---|
| `01-Windows-Sysmon-Installation-and-Configuration.jpeg` | Sysmon installation and configuration activity |
| `02-Sysmon-Event-ID-1-Process-Creation-and-DNS-Events.jpeg` | Sysmon process-creation and DNS-related event view |
| `03-Sysmon-Event-ID-1-and-22-Event-Details.jpeg` | Event detail views for process creation and DNS query activity |
| `04-Sysmon-Event-ID-11-File-Creation.jpeg` | Sysmon file-creation event |
| `05-Sysmon-Event-ID-13-Registry-Value-Set.jpeg` | Sysmon registry value-set event |
| `06-Sysmon-Service-and-Configuration-Verification.jpeg` | Sysmon service and configuration verification |
| `07-Kali-Network-Connectivity-Verification.jpeg` | Kali network connectivity checks |
| `08-Kali-Nmap-Service-Version-Scan.jfif` | Nmap service/version scan output |
| `09-Linux-strace-System-Call-Output.png` | Linux strace system-call output |
| `10-Snort-Local-Rules-Configuration.png` | Local Snort rule configuration |
| `11-Snort-TCP-Port-Scan-Detection-Alerts.png` | Snort TCP SYN/port-scan alert output |
| `12-Ubuntu-auditd-Service-Unit-Status.png` | auditd service-unit status output |
| `13-Ubuntu-auditd-Package-Installation-Output.jpeg` | auditd package installation output |
| `14-Ubuntu-Systemd-Service-Inventory.jfif` | Ubuntu systemd service inventory |
| `16-Ubuntu-Systemd-Active-Units-Listing.png` | Ubuntu systemd active-unit inventory |

## Evidence interpretation

- **Sysmon:** The screenshots show service/configuration activity and selected event records, including Event IDs 1, 11, 13 and 22. Use the individual event details when discussing the corresponding activity.
- **Kali/Nmap:** The captures show network connectivity checks and service/version scan output from the lab.
- **Snort:** The rule screenshot documents local rule configuration; the alert screenshot shows TCP scan-like alerts. The alert pattern is not unique to Nmap and should be treated as a detection lead rather than tool attribution.
- **Linux/auditd:** The captures show package installation output and service/systemd status information. The service-unit screenshot reports that `auditd.service` was not found at the time of that capture. The currently published set does not include a clear `ausearch` result or audit event record, so those screenshots should not be described as proof of successful audit-event collection.
- **strace:** The Linux strace capture is system-call tracing evidence, not Snort or auditd event evidence.

Original screenshot content has been retained; filenames are descriptive. Unrelated, duplicate and irrelevant captures were excluded from this evidence set.
