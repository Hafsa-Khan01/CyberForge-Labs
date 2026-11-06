# Week 03 — Linux Logs, Sysmon, auditd & Snort

**Programme:** DG Interns Hub  
**Focus:** Endpoint telemetry · Windows Sysmon · Linux auditd · Snort IDS/IPS · MITRE ATT&CK · SIEM

## Overview
This technical portfolio covers security telemetry across endpoint, operating-system and network layers. It includes ten theory notes, separate training reports, hands-on lab documentation, local Snort rules, an event cheat sheet, and an evidence index.

## Repository structure
| Directory | Contents |
|---|---|
| [Notes](Notes/) | Ten separate theoretical answers |
| [Writeups](Writeups/) | Individual TryHackMe, LetsDefend and practical reports |
| [Findings](Findings/) | Original screenshots and evidence index |
| [Cheat-Sheet](Cheat-Sheet/) | Windows Security, Sysmon, auditd and Snort reference |
| [Snort-Rules](Snort-Rules/) | Starter rules, T1046 rule and deployment notes |
| [Reports](Reports/) | Technical report and exactly-10-slide presentation outline |

## Theory coverage
1. EDR and endpoint telemetry.
2. Sysmon and key Event IDs.
3. Linux auditd compared with syslog.
4. Snort IDS/IPS operation.
5. Snort rule structure and options.
6. Signature-based vs anomaly-based detection.
7. MITRE ATT&CK T1046 — Network Service Discovery.
8. Windows Event Log vs Sysmon vs auditd.
9. Key Linux log files.
10. Log ingestion and SIEM workflow.

## Training assignments

### TryHackMe — assigned free rooms
- [Linux Logging for SOC](https://tryhackme.com/room/linuxloggingforsoc)
- [Intro to Logs](https://tryhackme.com/room/introtologs)
- [Intro to Log Analysis](https://tryhackme.com/room/introtologanalysis)
- [Snort](https://tryhackme.com/room/snort)

### LetsDefend
- [How to Investigate a SIEM Alert](https://app.letsdefend.io/training/lessons/how-to-investigate-a-siem-alert)
- Security Solutions
- Network Log Analysis
- SIEM 101
- Incident Management
- Incident Response on Linux

Each assigned room/course has its own report under `Writeups/TryHackMe/` or `Writeups/LetsDefend/`. Session completion details must reflect the actual platform activity.

## Practical coverage
- Windows: Sysmon installation/configuration and Event IDs 1, 3, 11, 13 and 22.
- Ubuntu: auditd service, ausearch and audit record interpretation.
- Ubuntu: Snort configuration, local rules, validation and alert monitoring.
- Kali: authorized Nmap SYN scan against a lab target.
- MITRE mapping: T1046 — Network Service Discovery.

## Detection engineering considerations
- Sysmon event coverage depends on the active configuration.
- Linux audit events can span multiple records sharing one serial identifier.
- Snort only inspects traffic visible to the sensor.
- Starter rules are broad indicators; an alert is not a verdict.
- A SYN threshold detects scan-like behavior, not proof of Nmap attribution.

## Evidence integrity
Only original screenshots from actual Windows, Ubuntu, Kali, TryHackMe and LetsDefend sessions belong in `Findings/`. No fabricated outputs, stock screenshots, invented timestamps or unsupported completion claims. Redact personal identifiers and sensitive network details before public sharing.

## Reports
- [Week 03 Technical Report](Reports/Week-03-Technical-Report.md)
- [Exactly-10-slide Presentation Outline](Reports/Presentation-Outline-10-Slides.md)

## References
- [Microsoft Sysmon](https://learn.microsoft.com/sysinternals/downloads/sysmon)
- [Linux Audit](https://linux.die.net/man/8/auditd)
- [Snort documentation](https://www.snort.org/documents)
- [MITRE ATT&CK T1046](https://attack.mitre.org/techniques/T1046/)
- [Wazuh documentation](https://documentation.wazuh.com/)
- [Splunk documentation](https://docs.splunk.com/)
