# Week 04 — SIEM in Practice: Splunk, Wazuh & Log Ingestion

**Programme:** DG Interns Hub  
**Focus:** SIEM deployment · Log ingestion · Detection engineering · Alert triage

## Repository structure

| Folder / file | Contents |
|---|---|
| [Notes](Notes/) | Eight separate theoretical Q&A documents |
| [Writeups](Writeups/) | Assigned TryHackMe room status and learning writeups |
| [Alternative-Labs](Alternative-Labs/) | Five self-contained room-free SIEM/SPL practical learning guides |
| [Findings](Findings/) | Evidence register and three SOC triage records |
| [Detections](Detections/) | Five SPL searches, scheduled-alert/dashboard guide and Wazuh rule starter |
| [Cheat Sheet](Cheat%20Sheet/) | SPL command reference and SIEM alert troubleshooting table |
| [Reports](Reports/) | Final report, 10-slide presentation plan, LinkedIn drafts and submission checklist |

## Theoretical coverage
1. SIEM architecture and SIEM vs. log management, SOAR and EDR.
2. Agent, syslog, API and file-based ingestion; Splunk UF vs. Wazuh agent.
3. SPL: search, where, stats, table, eval, timechart and rex.
4. Wazuh architecture, decoders, rules and rule levels.
5. Detection outcomes, alert fatigue and tuning.
6. Brute-force detection mapped to MITRE ATT&CK T1110.
7. Correlation, thresholds, baselines and allowlists.
8. SOC tiers, alert lifecycle and triage documentation.

## Practical scope
- Splunk Enterprise and dedicated `lab` index.
- Windows Security/Sysmon and Ubuntu authentication telemetry.
- Wazuh manager, endpoint agents and file integrity monitoring.
- Controlled SSH authentication testing and Nmap SYN scan on authorised lab systems.
- Five SPL detection use cases, two scheduled alerts and a four-panel dashboard.
- Custom Wazuh rule tested with `wazuh-logtest`.
- Three alert triage records.

Use the [Evidence Register](Findings/Evidence-Register.md) to connect practical claims to actual screenshots and outputs.

## TryHackMe access note
The assigned [Introduction to SIEM](https://tryhackme.com/room/introtosiem) and [Splunk: Exploring SPL](https://tryhackme.com/room/splunkexploringspl) rooms required premium access in the learner's account. They are marked **not attempted**; no completion is claimed. Equivalent learning objectives are documented in [Alternative-Labs](Alternative-Labs/README.md).

## Evidence standard
Practical claims must be backed by actual configuration, commands, SIEM events or screenshots. Preserve original screenshots, record tool versions and timezone, and redact secrets. A saved query or isolated `wazuh-logtest` match alone does not prove end-to-end ingestion or alerting. Do not publish invented outputs or completion claims.

## Submission checklist
See [Reports/Submission-Checklist.md](Reports/Submission-Checklist.md) for the complete content, evidence, export and quality-control checklist.

## References
- [Splunk documentation](https://docs.splunk.com/)
- [Wazuh documentation](https://documentation.wazuh.com/)
- [MITRE ATT&CK T1110 — Brute Force](https://attack.mitre.org/techniques/T1110/)
- [MITRE ATT&CK T1046 — Network Service Discovery](https://attack.mitre.org/techniques/T1046/)

[Return to DG Interns Hub](../README.md)
