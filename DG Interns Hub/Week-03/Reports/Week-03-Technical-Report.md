# Week 03 Technical Report
## Linux Logs, Sysmon, auditd and Snort Setup

**Programme:** DG Interns Hub  
**Focus:** Endpoint telemetry · Linux auditing · Network intrusion detection · MITRE ATT&CK

## 1. Executive summary
This report organizes the week's work across three telemetry layers: Windows endpoint events collected by Sysmon, Linux activity recorded by auditd, and network traffic inspected by Snort. Together, these sources support detection, investigation and SIEM correlation.

## 2. Objectives
- Explain EDR and the value of endpoint telemetry.
- Examine Sysmon process, network, file, DNS and registry events.
- Understand auditd records and their relationship to syslog/journald.
- Configure and validate Snort rules in an authorized lab.
- Map scan-like behavior to MITRE ATT&CK T1046.
- Relate raw logs to SIEM ingestion, normalization, correlation and dashboards.

## 3. Windows endpoint telemetry
Sysmon enriches Windows visibility with process and network context. Event IDs 1, 3, 11, 13 and 22 provide pivots across process execution, connections, file creation, registry changes and DNS activity. Coverage depends on the active configuration; event absence is not proof that activity did not occur.

## 4. Linux auditing
auditd records security-relevant system activity according to configured rules. Multi-record events should be correlated using the audit message serial. EXECVE, SYSCALL, PATH, USER_AUTH and USER_LOGIN records can contribute to a host timeline. General system messages remain useful through syslog or the systemd journal.

## 5. Network intrusion detection
Snort evaluates observed packets against configured rules. The local rules identify ICMP, SSH, HTTP and thresholded SYN-only traffic directed to HOME_NET. The T1046 rule is a scan-like indicator, not definitive attribution to Nmap. Sensor placement, interface selection, network variables and version-specific syntax affect visibility.

## 6. MITRE ATT&CK mapping
T1046 — Network Service Discovery describes adversary discovery of services on a network. Mapping a rule to T1046 provides behavioral context; it does not prove adversary intent. Correlation with endpoint process telemetry and approved scanning schedules improves confidence.

## 7. SIEM workflow
**Source → Collection/agent → Parsing → Normalization → Enrichment → Correlation/detection → Alert triage → Incident record/dashboard.**

Useful sources include Sysmon, Windows Security logs, auditd, syslog/journald, Snort alerts, DNS, firewall and network sensor records. Timestamp normalization, host identity, user context and retention are essential.

## 8. Practical evidence register
Add original screenshots and captions under ../Findings/. Record the capture filename, source VM, event/rule, timestamp and one-sentence interpretation. Evidence must not be fabricated or replaced with stock imagery.

## 9. Training write-ups
Separate TryHackMe and LetsDefend reports are located under ../Writeups/. Record actual completion dates, personal observations and platform evidence in each file after completing the corresponding free lesson.

## 10. Conclusion
Endpoint, operating-system audit and network telemetry provide complementary views. A SOC analyst gains stronger investigative confidence by correlating them into a timeline, validating alerts against context and separating observed facts from hypotheses.

## References
- Microsoft Sysmon: https://learn.microsoft.com/sysinternals/downloads/sysmon
- Linux Audit: https://linux.die.net/man/8/auditd
- Snort: https://www.snort.org/documents
- MITRE ATT&CK T1046: https://attack.mitre.org/techniques/T1046/
- Wazuh: https://documentation.wazuh.com/
- Splunk: https://docs.splunk.com/
