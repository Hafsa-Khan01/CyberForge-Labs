# Week 04 — SIEM in Practice: Splunk, Wazuh and Log Ingestion

**Programme:** DG Interns Hub  
**Topic:** SIEM deployment, telemetry ingestion, detection engineering and SOC triage

## Executive summary
This report documents the Week 04 SIEM learning track and its technical workflow. The work is organised around Splunk Enterprise, Windows Security and Sysmon telemetry, Ubuntu authentication logs, Wazuh endpoint monitoring, SPL detections and alert triage.

The repository includes the eight topic notes, detection query examples, a Wazuh rule starter, two technical cheat sheets, triage case formats and room-free alternative labs. The assigned TryHackMe rooms required premium access in the learner's account; they are recorded as not attempted, and their learning objectives are mapped to self-contained alternatives. No TryHackMe completion is claimed.

Practical execution claims must be linked to the actual screenshots, command output and SIEM records in the evidence register. Query files and configuration examples are reference material; their presence alone does not prove that a detection was executed or an alert fired.

## 1. Objectives
- Explain SIEM architecture and the event-to-alert lifecycle.
- Understand collection and ingestion from Windows and Linux endpoints.
- Use SPL to filter, extract, aggregate and visualise security events.
- Understand Wazuh manager/agent architecture, decoders, rules and FIM.
- Map suspicious authentication and network discovery behaviour to telemetry.
- Design, validate and tune detections.
- Apply a consistent SOC triage process.

## 2. Lab architecture
The intended lab roles are:
- **Splunk Enterprise:** central search and analysis platform, with a dedicated `lab` index.
- **Windows endpoint:** Security event log and Sysmon telemetry, forwarded by Universal Forwarder.
- **Ubuntu endpoint:** authentication telemetry such as `/var/log/auth.log`, where used by the installed distribution.
- **Wazuh manager and dashboard:** endpoint monitoring, rule evaluation and file integrity alerts.
- **Kali test system:** controlled source for authorised SSH authentication testing and Nmap discovery activity against the lab target only.

Record the actual versions, IP addresses, hostnames, network mode and time zone from the running environment in the evidence captions. Do not infer or invent them.

## 3. SIEM architecture and data flow
A typical SIEM pipeline begins with event generation at an endpoint or network device. An agent, forwarder, syslog receiver or API collects the event and transports it to the platform. Parsing and field extraction make the event searchable; normalisation supports consistent analysis across sources. Searches and correlation logic identify patterns, and alert rules route noteworthy activity for investigation.

The pipeline is only as reliable as its source coverage, timestamps, parsing, retention and access controls. Missing events, incorrect timezones and inconsistent field names can produce false negatives or misleading counts.

## 4. Splunk deployment and log ingestion
The lab workflow uses a dedicated `lab` index and a Splunk Universal Forwarder for endpoint telemetry.

### Windows
Relevant telemetry includes:
- Security events such as failed logons (commonly Event ID 4625), successful logons (4624) and user creation (4720);
- Sysmon process creation (Event ID 1), network connections (Event ID 3) and selected registry/file events.

### Ubuntu
Authentication telemetry is commonly available in `/var/log/auth.log` on Ubuntu/Debian systems. The exact source depends on the distribution and logging configuration.

### Ingestion validation
An analyst should first confirm event arrival by host, source and sourcetype, then inspect raw events, timestamps and extracted fields. The validation searches are documented in [Alternative Lab 02](../Alternative-Labs/02-Log-Ingestion-and-Validation.md).

## 5. Wazuh monitoring and file integrity
Wazuh uses agents to collect endpoint telemetry and a manager to analyse events using decoders and rules. File Integrity Monitoring (FIM) detects configured file or directory changes and produces alerts for investigation.

A valid FIM test should identify the monitored path, the controlled file change, the resulting event and the matching alert. Agent connectivity and manager health should be checked before interpreting missing alerts as a detection failure.

## 6. Controlled attack-to-alert validation
Testing must remain within the authorised lab scope.

### SSH authentication testing
The purpose is to generate a small, controlled series of authentication failures against a lab SSH service and verify whether the endpoint logs and SIEM record the attempts. The investigation should group failures by source, target and account, then check for a subsequent successful login and known benign causes.

The activity maps to MITRE ATT&CK **T1110 — Brute Force** when the observed behaviour supports that interpretation. A test command or a set of failed logins alone does not establish compromise.

### Nmap SYN scan
An authorised SYN scan can generate network discovery telemetry relevant to MITRE ATT&CK **T1046 — Network Service Discovery**. Validate the source, target, ports and time window, then determine whether the source was an approved scanner. A scan is not evidence of exploitation by itself.

## 7. SPL detection engineering
The repository contains five starter searches:
1. Failed logons per user.
2. PowerShell process creation.
3. New user account creation.
4. SSH failures per source IP.
5. Rare parent-child process pairs.

Each search must be adapted to the actual index, sourcetype and extracted fields. The SPL hands-on lab provides additional examples and explains filtering, aggregation, extraction, time-series analysis and data-quality checks.

Two scheduled alerts should be documented with their schedule, search time range, trigger condition, suppression settings and owner. A four-panel dashboard can display event volume, authentication failures, top hosts/sources and selected endpoint/network activity. The panels should use real data and be labelled honestly if a source is unavailable.

## 8. Custom Wazuh rule
A custom rule should use a unique rule ID in the assignment's requested range (100000 or higher), depend on a verified parent rule/decoder and be tested with representative input using `wazuh-logtest`. The starter file in `../Detections/wazuh-local-rules.xml` intentionally leaves the parent SSH rule ID as a placeholder. Replace it only after checking the actual manager's rule match and test output.

A successful logtest match validates rule evaluation for the supplied input; end-to-end validation additionally requires the expected event to reach the manager and generate the intended alert.

## 9. Alert triage
Three case guides are provided for:
- repeated authentication failures;
- suspicious PowerShell process activity;
- network discovery or unusual connection activity.

For each actual alert, record the alert identifier, time and timezone, affected asset/account, source and destination, evidence reviewed, related events, baseline/allowlist checks, assessment, confidence, verdict and actions taken. Do not write a containment action as completed unless it actually occurred.

## 10. Key operational lessons
- Validate log arrival and field extraction before building detections.
- Use event IDs as pivots, but confirm the actual field mapping in the environment.
- Establish normal behaviour before choosing alert thresholds.
- Treat alerts as investigation leads rather than proof of compromise.
- Record false-positive causes and tune without creating blind spots.
- Preserve evidence and redact secrets before publishing.

## 11. Evidence register
Use [Evidence Register](../Findings/Evidence-Register.md) to link each claim to its screenshot or output. The report should be considered final only after the actual lab artifacts have been added and the corresponding triage notes completed.

## 12. Repository deliverables
- [Eight SIEM topic notes](../Notes/README.md)
- [Room writeups and access status](../Writeups/README.md)
- [Room-free alternative labs](../Alternative-Labs/README.md)
- [Five SPL searches and Wazuh rule starter](../Detections/README.md)
- [SPL command reference](../Cheat%20Sheet/SPL-Command-Reference.md)
- [SIEM alert triage reference](../Cheat%20Sheet/SIEM-Alert-Triage-Reference.md)
- [Three triage notes](../Findings/README.md)
- [Final submission checklist](Submission-Checklist.md)

## References
- [Splunk Documentation](https://docs.splunk.com/)
- [Splunk Search Reference](https://docs.splunk.com/Documentation/Splunk/latest/SearchReference/WhatsInThisManual)
- [Wazuh Documentation](https://documentation.wazuh.com/)
- [Wazuh Ruleset](https://documentation.wazuh.com/current/user-manual/ruleset/index.html)
- [MITRE ATT&CK T1110 — Brute Force](https://attack.mitre.org/techniques/T1110/)
- [MITRE ATT&CK T1046 — Network Service Discovery](https://attack.mitre.org/techniques/T1046/)
- [TryHackMe — Introduction to SIEM](https://tryhackme.com/room/introtosiem) (premium access required; not attempted)
- [TryHackMe — Splunk: Exploring SPL](https://tryhackme.com/room/splunkexploringspl) (premium access required; not attempted)
