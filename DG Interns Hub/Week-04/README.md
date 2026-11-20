# Week 04 — SIEM in Practice: Splunk, Wazuh & Log Ingestion

**Programme:** DG Interns Hub  
**Focus:** SIEM deployment · Log ingestion · Detection engineering · Alert triage

## Repository structure

| Folder / file | Contents |
|---|---|
| [Notes](Notes/) | Eight separate theoretical Q&A documents |
| [Writeups](Writeups/) | Individual TryHackMe room writeups |
| [Findings](Findings/) | Practical evidence index, screenshots and three triage records |
| [Detections](Detections/) | Five SPL searches, scheduled-alert record and custom Wazuh rule |
| [Cheat Sheet](Cheat%20Sheet/) | SPL command reference and SIEM alert troubleshooting table |
| [Reports](Reports/) | Weekly report source and presentation outline |

## Theoretical coverage
1. SIEM architecture and SIEM vs. log management, SOAR and EDR.
2. Agent, syslog, API and file-based ingestion; Splunk UF vs. Wazuh agent.
3. SPL: search, where, stats, table, eval, timechart and rex.
4. Wazuh architecture, decoders, rules and rule levels.
5. Detection outcomes, alert fatigue and tuning.
6. Brute-force detection mapped to MITRE ATT&CK T1110.
7. Correlation, thresholds, baselines and allowlists.
8. SOC tiers, alert lifecycle and triage documentation.

## Practical work to document
- Splunk Enterprise and dedicated `lab` index.
- Windows Security/Sysmon and Ubuntu auth.log ingestion.
- Wazuh deployment, Windows/Ubuntu agents and file integrity monitoring.
- Controlled SSH authentication testing and Nmap SYN scan on owned lab systems.
- Five SPL detections, two scheduled alerts and a four-panel dashboard.
- Custom Wazuh rule tested with `wazuh-logtest`.
- Three alert triage records.

## Evidence standard
Practical claims must be backed by actual configuration, commands, SIEM events or screenshots. Preserve original screenshots, record tool versions and time zone, and redact secrets. A saved query or isolated `wazuh-logtest` match alone does not prove end-to-end ingestion or alerting. Do not publish invented outputs or completion claims.

## Submission checklist
- [ ] Notes reviewed.
- [ ] Both TryHackMe room writeups completed with actual results.
- [ ] Splunk/Wazuh setup and ingestion evidence added.
- [ ] SSH and Nmap attack-to-alert evidence added.
- [ ] Five SPL searches tested; two alerts and four-panel dashboard evidenced.
- [ ] Custom Wazuh rule and logtest output included.
- [ ] Three triage notes completed.
- [ ] Cheat sheets completed.
- [ ] Final PDF and presentation exported and reviewed.
- [ ] Submission folder sharing permissions checked.

## References
- [Splunk documentation](https://docs.splunk.com/)
- [Wazuh documentation](https://documentation.wazuh.com/)
- [TryHackMe — Introduction to SIEM](https://tryhackme.com/room/introtosiem)
- [TryHackMe — Splunk: Exploring SPL](https://tryhackme.com/room/splunkexploringspl)
- [MITRE ATT&CK — T1110](https://attack.mitre.org/techniques/T1110/)

[Return to DG Interns Hub](../README.md)
