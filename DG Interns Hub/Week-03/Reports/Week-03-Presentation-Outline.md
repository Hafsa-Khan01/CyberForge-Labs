# Week 03 — Presentation Content
## Endpoint Telemetry, Linux Auditing & Network Intrusion Detection

### Slide 1 — Title
**Endpoint Telemetry, Linux Auditing & Network Intrusion Detection**  
DG Interns Hub · Week 03  
Hafsa Khan

### Slide 2 — Lab Architecture & Objectives
**Environment**
- Windows VM — Sysmon endpoint telemetry
- Ubuntu VM — auditd and Snort IDS
- Kali Linux VM — authorized testing with Nmap

**Objectives**
- Collect and interpret host and network events.
- Understand Linux audit records and IDS rules.
- Correlate evidence and map behavior to MITRE ATT&CK.

### Slide 3 — EDR, Windows Logs & Sysmon
- EDR combines endpoint telemetry, detection, investigation and response.
- Antivirus commonly focuses on malware prevention and detection.
- Sysmon adds detailed process, network, file, registry and DNS visibility.
- Operational channel: `Microsoft-Windows-Sysmon/Operational`.

**Key Event IDs:** 1 ProcessCreate · 3 NetworkConnect · 11 FileCreate · 13 RegistryEvent · 22 DNS query

### Slide 4 — Windows Sysmon: Lab Findings
- Event 1: process creation and parent-process context.
- Event 3: PowerShell TCP connection to `142.250.202.142:443`.
- Event 11: PowerShell created `Week3-Sysmon-Test.ps1`.
- Event 13: Microsoft Edge Run-key auto-launch value.
- Event 22: PowerShell DNS query for `google.com`.

**Analysis:** Event ID 13 requires application context; the observed Edge auto-launch entry alone does not establish malicious persistence.

### Slide 5 — Linux Audit Logging with auditd
- Audit daemon records activity selected by audit rules.
- Primary log: `/var/log/audit/audit.log`.
- Important records: SYSCALL, EXECVE, PATH, CWD, USER_AUTH and USER_LOGIN.
- Correlate records sharing the same audit event identifier.
- Review `auid`, `uid`, `euid`, `exe`, `comm`, `pid` and syscall outcome.

### Slide 6 — Snort IDS & Detection Rules
- IDS monitors traffic and generates alerts; IPS can take preventive action inline.
- Rule structure: action, protocol, source/destination, direction and options.
- Common options: `msg`, `sid`, `rev`, `flags`, `flow`, `threshold`, `classtype`.
- Lab SIDs: 1000001 ICMP · 1000002 SSH · 1000003 HTTP · 1000004 possible SYN scan.

### Slide 7 — Kali Linux & Nmap
- Nmap 7.95 used for authorized lab network testing.
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

### Slide 10 — Key Takeaways
- Endpoint, Linux and network telemetry provide complementary visibility.
- Collection configuration determines what can be detected.
- Individual alerts require context and corroboration.
- Thresholds need tuning to manage false positives.
- Evidence-based correlation supports stronger SOC decisions.

**Closing:** Visibility becomes actionable when events are connected into a defensible investigation.
