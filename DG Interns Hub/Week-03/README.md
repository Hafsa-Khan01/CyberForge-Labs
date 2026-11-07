# Week 03 — Linux Logs, Sysmon, auditd & Snort

**Programme:** DG Interns Hub  
**Focus:** Endpoint telemetry · Windows Sysmon · Linux auditd · Snort IDS · MITRE ATT&CK · SIEM

## Overview
This portfolio brings together the Week 03 work on endpoint, operating-system and network security telemetry. It includes ten theory notes, individual training write-ups, practical documentation, local Snort rules, a detection reference sheet and supporting screenshots.

## Repository structure
| Directory | Contents |
|---|---|
| [Notes](Notes/) | Ten theory topics covering endpoint and network monitoring |
| [Writeups](Writeups/) | TryHackMe room reports and LetsDefend course status/write-ups |
| [Practicals](Practicals/) | Hands-on Windows, Ubuntu and Kali lab documentation |
| [Evidence](Evidence/) | Original practical screenshots and evidence index |
| [Cheat-Sheet](Cheat-Sheet/) | Sysmon, Windows events, auditd and Snort reference |
| [Snort-Rules](Snort-Rules/) | Local detection rules and configuration notes |
| [Reports](Reports/) | Consolidated technical lab report |

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

### TryHackMe
- [Linux Logging for SOC](https://tryhackme.com/room/linuxloggingforsoc)
- [Intro to Logs](https://tryhackme.com/room/introtologs)
- [Intro to Log Analysis](https://tryhackme.com/room/introtologanalysis)
- [Snort](https://tryhackme.com/room/snort)

Individual room reports are available in [Writeups/TryHackMe](Writeups/TryHackMe/).

### LetsDefend
The assigned lessons were reviewed for access availability. The listed lessons prompted for Premium access and were not completed; their status is recorded transparently in [Writeups/LetsDefend](Writeups/LetsDefend/).

## Practical coverage
- **Windows:** Sysmon installation/configuration and review of process, network, file, registry and DNS events.
- **Ubuntu:** Linux audit logging, auditd service/rule concepts and record interpretation.
- **Ubuntu:** Snort configuration, local rules and alert analysis.
- **Kali:** Network connectivity checks and authorized Nmap service/version testing.
- **Detection mapping:** MITRE ATT&CK T1046 — Network Service Discovery.

## Detection considerations
- Sysmon event coverage depends on the active configuration.
- Linux audit events can span multiple records sharing one serial identifier.
- Snort only inspects traffic visible to the sensor.
- A threshold-based SYN alert is an investigative indicator, not proof of Nmap attribution or malicious intent.
- Correlation across endpoint, host-audit and network telemetry improves investigative confidence.

## Evidence integrity
The [Evidence index](Evidence/README.md) describes the original screenshots currently published with this portfolio. Each description is limited to what the corresponding capture visibly demonstrates. Configuration, installation and service-inventory screenshots are not presented as proof of successful event collection unless the relevant output is visible.

## Report
- [Week 03 Technical Lab Report](Reports/Week-03-Final-Report.md)

## References
- [Microsoft Sysmon](https://learn.microsoft.com/sysinternals/downloads/sysmon)
- [Linux Audit documentation](https://github.com/linux-audit/audit-documentation)
- [Snort documentation](https://docs.snort.org/)
- [Nmap Reference Guide](https://nmap.org/book/man.html)
- [MITRE ATT&CK T1046](https://attack.mitre.org/techniques/T1046/)
- [Wazuh documentation](https://documentation.wazuh.com/)
- [Splunk documentation](https://docs.splunk.com/)
