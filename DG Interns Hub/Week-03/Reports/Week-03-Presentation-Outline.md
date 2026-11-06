# Week 03 — Technical Presentation
## Endpoint Telemetry, Linux Auditing & Network Intrusion Detection

### Slide 1 — Endpoint & Network Security Monitoring
**DG Interns Hub · Week 03**  
Hafsa Khan  
Sysmon · auditd · Snort IDS · Nmap · MITRE ATT&CK

### Slide 2 — Lab Architecture & Objectives
**Lab environment**
- Windows VM — Sysmon endpoint telemetry
- Ubuntu VM — auditd and Snort IDS
- Kali Linux VM — authorized network testing with Nmap

**Operational objectives**
- Collect and interpret host and network events.
- Inspect Linux audit records and IDS alerts.
- Correlate evidence across systems.
- Map observed behavior to MITRE ATT&CK.

### Slide 3 — EDR, Windows Logs & Sysmon
- EDR combines endpoint telemetry, detection, investigation and response.
- Traditional antivirus commonly emphasizes malware prevention and detection.
- Sysmon adds detailed process, network, file, registry and DNS visibility.
- Operational channel: `Microsoft-Windows-Sysmon/Operational`.

**Key events:** 1 ProcessCreate · 3 NetworkConnect · 11 FileCreate · 13 RegistryEvent · 22 DNS query

### Slide 4 — Windows Sysmon: Event Analysis
- **Event 1:** Process creation and parent-process context.
- **Event 3:** PowerShell TCP connection to `142.250.202.142:443`.
- **Event 11:** PowerShell created `Week3-Sysmon-Test.ps1`.
- **Event 13:** Microsoft Edge Run-key auto-launch value.
- **Event 22:** PowerShell DNS query for `google.com`.

**Assessment:** Registry startup events require application context. The observed Edge auto-launch entry alone does not establish malicious persistence.

### Slide 5 — Linux Audit Logging with auditd
- Audit daemon records activity selected by audit rules.
- Primary log: `/var/log/audit/audit.log`.
- Important records: SYSCALL, EXECVE, PATH, CWD, USER_AUTH and USER_LOGIN.
- Correlate records sharing the same audit event identifier.
- Review `auid`, `uid`, `euid`, `exe`, `comm`, `pid` and syscall outcome.

### Slide 6 — Snort IDS: Rules & Alert Logic
- IDS monitors traffic and generates alerts; IPS can take preventive action inline.
- Rule structure: action, protocol, source/destination, direction and options.
- Common options: `msg`, `sid`, `rev`, `flags`, `flow`, `threshold`, `classtype`.
- Lab SIDs: 1000001 ICMP · 1000002 SSH · 1000003 HTTP · 1000004 possible SYN scan.

### Slide 7 — Kali Linux: Nmap & Service Discovery
- Nmap 7.95 supports authorized service/version identification and port scanning.
- `-sV`: service/version detection.
- `-sC`: default script set.
- `-sS`: TCP SYN scan.
- `-oN`: save normal output.

**SOC relevance:** Identify exposed services and correlate scan patterns with sensor, firewall and endpoint telemetry.

### Slide 8 — MITRE ATT&CK: T1046
**Network Service Discovery**
- Describes discovery of services running on remote systems.
- Multiple SYN packets across destination ports may indicate scan-like activity.
- A SYN threshold is a heuristic, not a unique Nmap signature.
- Validate source, timing, port spread, authorization and related events.

### Slide 9 — SIEM Correlation & Investigation
**Telemetry sources → Collection → Normalization → Correlation → Alert triage → Investigation / response**

Correlate:
- Host, user and process identity
- Event timestamps and audit identifiers
- DNS requests and network destinations
- IDS alerts and authorized activity

### Slide 10 — Operational Takeaways
- Endpoint, Linux and network telemetry provide complementary visibility.
- Collection configuration determines what can be detected.
- Individual alerts require context and corroboration.
- Thresholds need tuning to manage false positives.
- Evidence-based correlation supports defensible SOC decisions.

**Closing statement:** Connected telemetry turns isolated events into an actionable investigation.
