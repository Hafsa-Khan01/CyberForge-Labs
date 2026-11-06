# Week 3 Final Report — Linux Logs, Sysmon, auditd and Snort

**Programme:** DG Interns Hub — 15 October 2026 Batch  
**Intern:** Hafsa Khan  
**Reporting date:** 6 November 2026

## 1. Executive summary
This week's work focused on endpoint telemetry, Linux auditing, network intrusion detection and mapping observable behavior to MITRE ATT&CK. The theory set contains ten separate notes. The practical environment used Windows, Ubuntu and Kali virtual machines. The user reports completion of the practical work on all three systems; original screenshots and command outputs should accompany this report.

## 2. Learning objectives
- Explain EDR telemetry and distinguish EDR from traditional antivirus.
- Understand Windows Security logs and Sysmon event telemetry.
- Configure and interpret Linux auditd records.
- Explain Snort IDS/IPS operation and rule structure.
- Distinguish signature-based and anomaly-based detection.
- Map possible network service discovery to MITRE ATT&CK T1046.
- Understand endpoint/network log ingestion into a SIEM.

## 3. Lab environment
| VM | Role | Main tooling |
|---|---|---|
| Windows | Endpoint telemetry source | Sysmon 15.22, Event Viewer / PowerShell |
| Ubuntu | Linux auditing and network IDS | auditd, Snort |
| Kali | Authorized test traffic generation | Nmap 7.95 |

## 4. Windows Sysmon findings
Sysmon was installed with a SwiftOnSecurity configuration and its Operational event channel was verified. Event IDs 1, 3, 11, 13 and 22 were observed.

- Event 1: process creation telemetry, including image, command line, user and parent process context.
- Event 3: a PowerShell TCP connection to `142.250.202.142:443` was recorded; the observed source address was `192.168.100.33`.
- Event 11: PowerShell created `C:\Users\hiras\Desktop\Week3-Sysmon-Test.ps1`.
- Event 13: Microsoft Edge set a user Run-key value for its auto-launch command. This is registry startup telemetry; the observed entry is not by itself evidence of malicious persistence.
- Event 22: PowerShell queried `google.com`; query status was 0.

A configuration-specific observation was that a plain `.txt` test file did not match the selected FileCreate filters, while a `.ps1` file generated Event ID 11.

## 5. Ubuntu auditd
The auditd practical is reported complete. The submitted evidence should show the service state, configured rule, generated test action and matching audit records. Audit records such as SYSCALL, EXECVE, PATH and CWD should be correlated by their shared audit event identifier. A key-based `ausearch` query is valid only when a matching keyed rule exists.

## 6. Snort IDS
The Snort practical is reported complete. The lab rules cover ICMP, SSH, HTTP and thresholded SYN activity. The SYN rule is a heuristic indicator of possible network service discovery; it is not uniquely attributable to Nmap. The final evidence should include the actual configuration, rule validation and console alerts.

## 7. Kali and Nmap
The Kali practical is reported complete. Nmap 7.95 was verified. The final evidence should include the actual authorized lab target, service/version scan output, SYN scan output and relevant observations. The first captured network state showed eth0 UP without an IPv4 address and no default route; use the later successful verification screenshot for the final lab state.

## 8. MITRE ATT&CK mapping
T1046 — Network Service Discovery is relevant when activity identifies services running on remote systems. A burst of TCP SYN packets across multiple destination ports may be a detection indicator. Validate with port diversity, source context, timing, authorization and corroborating logs. Do not infer tool identity or malicious intent from SYN packets alone.

Registry Run-key modifications may be associated with T1547.001, Registry Run Keys / Startup Folder. The observed Edge auto-launch value was legitimate-looking application behavior and should not be labeled malicious without further evidence.

## 9. SIEM investigation workflow
1. Ingest endpoint, authentication, audit and network telemetry.
2. Normalize timestamps, host identity, user and network fields.
3. Correlate events by host, process, user, time and source/destination.
4. Validate the alert against expected administrative or application behavior.
5. Preserve evidence and document scope, confidence and limitations.
6. Map to ATT&CK only where behavior is supported.

## 10. Limitations and evidence integrity
This report intentionally does not invent Ubuntu audit event IDs, Snort alert timestamps, Nmap target addresses or scan results that were not present in the conversation record. Insert the exact values from original VM screenshots and saved output files before final PDF export. Use only genuine lab screenshots; external images may be used as clearly attributed conceptual illustrations, never as practical proof.

## 11. Repository evidence map
- `Notes/`: ten theory answers.
- `Writeups/Windows-Sysmon-Practical.md`: Windows practical.
- `Writeups/Ubuntu-auditd-Practical.md`: Linux audit practical.
- `Writeups/Ubuntu-Snort-Practical.md`: IDS practical.
- `Writeups/Kali-Nmap-Practical.md`: Nmap practical.
- `Snort-Rules/local-week3.rules`: local rules.
- `Cheat-Sheet/Week-03-Endpoint-and-Network-Detection-Cheat-Sheet.md`: quick reference.
- `Findings/`: add original screenshots and scan/alert exports.

## 12. Conclusion
The exercises connect endpoint process and registry telemetry with Linux audit records and network IDS observations. Their combined value comes from correlation: a network alert gains context from the originating host and process, while endpoint events gain significance when correlated with network behavior and authentication records.
