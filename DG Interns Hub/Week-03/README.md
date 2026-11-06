# Week 03 — Endpoint Telemetry, Linux Auditing & Network Intrusion Detection

**Programme:** DG Interns Hub · Week 03  
**Focus areas:** Sysmon · auditd · Snort IDS · Nmap · MITRE ATT&CK · SIEM

## Overview
This module brings together endpoint monitoring, Linux audit logging and network-based intrusion detection. The lab work examines how operating-system and network telemetry can be collected, interpreted and correlated during a security investigation.

## Lab Environment

| Platform | Function | Tools |
|---|---|---|
| Windows VM | Endpoint telemetry collection | Sysmon 15.22, Event Viewer, PowerShell |
| Ubuntu VM | Linux auditing and network IDS | auditd, Snort |
| Kali Linux VM | Authorized network testing | Nmap 7.95 |

## Repository Structure

| Directory | Contents |
|---|---|
| `Notes/` | Ten technical theory notes covering the weekly syllabus |
| `Writeups/` | Practical documentation for Windows, Ubuntu and Kali |
| `Findings/` | Original screenshots, terminal output and alert evidence |
| `Cheat-Sheet/` | Windows, Sysmon, auditd and Snort quick reference |
| `Snort-Rules/` | Local detection rules used for the lab |
| `Reports/` | Technical report and presentation materials |

## Practical Coverage
- **Windows Sysmon:** Process creation, network connection, file creation, registry modification and DNS query telemetry (Event IDs 1, 3, 11, 13 and 22).
- **Ubuntu auditd:** Audit service configuration, targeted rules and event inspection.
- **Snort IDS:** Local rule configuration, rule validation and alert interpretation for ICMP, SSH, HTTP and scan-like TCP SYN activity.
- **Kali Linux / Nmap:** Service/version identification and controlled port scanning against authorized lab systems.

## Evidence Standards
Screenshots and command output in `Findings/` are retained as original lab evidence. Preserve visible timestamps and command context where possible. Redact passwords, tokens, personal identifiers and unrelated desktop information before publication. Conceptual diagrams are supplementary material and are not substitutes for practical evidence.

## Technical References
- [Microsoft Sysmon documentation](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)
- [Linux Audit documentation](https://github.com/linux-audit/audit-documentation)
- [Snort documentation](https://docs.snort.org/)
- [Nmap Reference Guide](https://nmap.org/book/man.html)
- [MITRE ATT&CK — T1046 Network Service Discovery](https://attack.mitre.org/techniques/T1046/)

## Scope
All Week 03 material is maintained within this directory. Other projects and the NetworkWalks lab directory are outside this module's scope.
