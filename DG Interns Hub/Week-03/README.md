# Week 03 — Linux Logs, Sysmon, auditd & Snort

**Programme:** DG Interns Hub  
**Technical areas:** Endpoint telemetry · Linux auditing · Network intrusion detection · MITRE ATT&CK · SIEM operations

## Overview

This directory consolidates the Week 03 technical documentation across Windows endpoint monitoring, Linux audit logging and network intrusion detection. It contains topic notes, individual TryHackMe reports, practical records, local Snort rules, a reference sheet and the supporting screenshots.

## Repository map

| Directory | Contents |
|---|---|
| [Notes](Notes/) | Ten technical notes covering endpoint and network monitoring |
| [Writeups](Writeups/) | TryHackMe room reports and LetsDefend access-status record |
| [Evidence](Evidence/) | Original screenshots and evidence index |
| [Cheat-Sheet](Cheat-Sheet/) | Sysmon, Windows events, auditd and Snort reference |
| [Snort-Rules](Snort-Rules/) | Local detection rules and configuration notes |
| [Reports](Reports/) | Consolidated technical lab report |

## Technical coverage

1. EDR and endpoint telemetry.
2. Sysmon architecture, configuration and key Event IDs.
3. Linux auditd and audit record structure.
4. Snort IDS/IPS operation.
5. Snort rule structure and options.
6. Signature-based and anomaly-based detection.
7. MITRE ATT&CK T1046 — Network Service Discovery.
8. Windows Event Log, Sysmon and auditd comparison.
9. Linux log locations and common sources.
10. Log ingestion, correlation and SIEM triage.

## Platform reports and access status

### TryHackMe

The following room reports are included:

- [Linux Logging for SOC](https://tryhackme.com/room/linuxloggingforsoc)
- [Intro to Logs](https://tryhackme.com/room/introtologs)
- [Intro to Log Analysis](https://tryhackme.com/room/introtologanalysis)
- [Snort](https://tryhackme.com/room/snort)

See [Writeups/TryHackMe](Writeups/TryHackMe/) for the individual reports.

### LetsDefend

The six assigned lessons displayed a Premium access requirement and were not completed. This is recorded in [Writeups/LetsDefend](Writeups/LetsDefend/); no course completion or lesson-specific practical result is claimed.

## Practical scope

- **Windows:** Sysmon installation/configuration and review of process, network, file, registry and DNS events.
- **Ubuntu:** audit logging concepts, auditd package/service checks and audit-record interpretation.
- **Ubuntu:** Snort local-rule configuration and alert review.
- **Kali Linux:** Network connectivity verification and authorized Nmap service/version testing.
- **Detection mapping:** Network service discovery behavior mapped to MITRE ATT&CK T1046.

## Detection and evidence considerations

- Sysmon event coverage depends on the active configuration and its filters.
- Linux audit events can span multiple records sharing one event serial number.
- Snort can only inspect traffic visible to the configured sensor.
- A threshold-based SYN alert is an investigative indicator; it does not uniquely identify Nmap or establish malicious intent.
- Installation, configuration and service-status captures do not by themselves prove successful event collection.
- Correlation across endpoint, host-audit and network telemetry provides stronger context than an isolated alert.

The [Evidence index](Evidence/README.md) describes the original screenshots currently published and limits each description to what the capture demonstrates.

## Consolidated report

[Week 03 Technical Lab Report](Reports/Week-03-Final-Report.md)

## Technical references

- [Microsoft Sysmon](https://learn.microsoft.com/sysinternals/downloads/sysmon)
- [Linux Audit documentation](https://github.com/linux-audit/audit-documentation)
- [Snort documentation](https://docs.snort.org/)
- [Nmap Reference Guide](https://nmap.org/book/man.html)
- [MITRE ATT&CK T1046](https://attack.mitre.org/techniques/T1046/)
- [Wazuh documentation](https://documentation.wazuh.com/)
- [Splunk documentation](https://docs.splunk.com/)
