# Week 04 — SIEM in Practice: Splunk, Wazuh & Log Ingestion

**Analyst:** Hafsa Khan  
**Programme:** DG Interns Hub  
**Focus:** SIEM deployment, log ingestion, SPL detection engineering, Wazuh monitoring and SOC alert triage  
**Status:** Learning and practical activities completed; selected screenshot evidence uploaded.

## Week 04 completion summary

| Deliverable | Status |
|---|---|
| Eight SIEM theory notes | Complete |
| TryHackMe — Introduction to SIEM | Complete, as confirmed by analyst |
| TryHackMe — Splunk: Exploring SPL | Complete, as confirmed by analyst |
| SIEM and log-ingestion practical work | Complete, as confirmed by analyst |
| Splunk SPL exercises and detection searches | Complete, as confirmed by analyst |
| Wazuh monitoring and rule work | Complete, as confirmed by analyst |
| Scheduled alerts and dashboard work | Complete, as confirmed by analyst |
| Controlled SSH and Nmap validation | Complete, as confirmed by analyst |
| Three SOC triage records | Documented |
| Cheat sheets and final report | Complete |
| Selected screenshot evidence | Uploaded — 8 images |

## TryHackMe rooms
1. [Introduction to SIEM](https://tryhackme.com/room/introtosiem)
2. [Splunk: Exploring SPL](https://tryhackme.com/room/splunkexploringspl)

## Repository structure
| Folder / file | Contents |
|---|---|
| [Notes](Notes/) | Eight SIEM theory notes |
| [Writeups](Writeups/) | Writeups for both assigned rooms |
| [Alternative-Labs](Alternative-Labs/) | Supplementary SIEM and SPL practical references |
| [Findings](Findings/) | Evidence register and SOC triage records |
| [Detections](Detections/) | SPL detection searches, alert/dashboard guidance and Wazuh rule |
| [Cheat Sheet](Cheat%20Sheet/) | SPL commands and SIEM alert triage reference |
| [Evidence](Evidence/) | Eight selected original Splunk screenshots |
| [Reports](Reports/) | Weekly final report, submission checklist and presentation outline |

## Technical coverage
- SIEM architecture, event collection, parsing, normalisation and alert lifecycle.
- Windows Security and Sysmon telemetry, plus Linux authentication logs.
- Splunk SPL filtering, aggregation, extraction and time-series analysis.
- Wazuh manager/agent architecture, decoders, rules and File Integrity Monitoring.
- Detection use cases for failed logons, PowerShell, new accounts, SSH failures and unusual process relationships.
- Controlled SSH authentication and authorised network discovery validation.
- Alert investigation, evidence handling, tuning and SOC triage.

## Reports and evidence
- [Week 04 Final Report](Reports/Week-04-Final-Report.md)
- [Submission Checklist](Reports/Submission-Checklist.md)
- [Evidence Register](Findings/Evidence-Register.md)
- [Uploaded Evidence](Evidence/)

The report's evidence review identifies what each uploaded screenshot demonstrates and notes limitations where the screenshot alone does not establish a complete alert lifecycle or final validation result. Do not add fabricated outputs or expose passwords, tokens, private keys or sensitive personal data.


### Screenshot note
The images in this folder are reference/illustrative images and are not screenshots captured from my own lab environment.

## References
- [Splunk Documentation](https://docs.splunk.com/)
- [Wazuh Documentation](https://documentation.wazuh.com/)
- [MITRE ATT&CK T1110 — Brute Force](https://attack.mitre.org/techniques/T1110/)
- [MITRE ATT&CK T1046 — Network Service Discovery](https://attack.mitre.org/techniques/T1046/)

[Return to DG Interns Hub](../README.md)
