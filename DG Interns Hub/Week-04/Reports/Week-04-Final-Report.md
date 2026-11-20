# Week 04 — SIEM in Practice: Splunk, Wazuh and Log Ingestion

**Programme:** DG Interns Hub  
**Reporting period:** [Actual dates]

## 1. Executive summary
Summarize the work completed, platforms deployed, telemetry ingested, detections tested and key observations. Support every completion claim with repository evidence.

## 2. Objectives
- Understand SIEM architecture and log ingestion.
- Configure Splunk and Wazuh in a lab.
- Ingest Windows, Sysmon and Ubuntu authentication telemetry.
- Investigate controlled SSH and network-scan activity.
- Build and test SPL and Wazuh detections.
- Practice alert triage.

## 3. Lab environment
| System | Role | OS / version | Address / identifier |
|---|---|---|---|
| Splunk | SIEM / indexer / search | | |
| Windows | Endpoint / Universal Forwarder | | |
| Ubuntu | Linux endpoint / Wazuh | | |
| Kali | Authorized test source | | |

Record RAM, tool versions, network mode and time zone.

## 4. Splunk deployment and ingestion
Document installation, `lab` index, receiver configuration, Windows UF inputs, Sysmon/Security sources and Ubuntu auth.log monitoring. Include actual searches and events.

## 5. Wazuh deployment and endpoint monitoring
Document manager/indexer/dashboard setup, agent enrollment, FIM configuration and the observed file-change alert.

## 6. Attack-to-alert validation
### SSH authentication test
Include authorized scope, command (no secrets), raw event, parsed fields, alert or manual search and interpretation.

### Nmap SYN scan
Include authorized scope, command, raw event, parsed fields, alert or manual search and limitations.

## 7. SPL detections
Document all five searches, detection purpose, MITRE mapping, L1 usefulness, tested results and field dependencies. Include the two scheduled alerts and four-panel dashboard.

## 8. Custom Wazuh rule
Include deployed rule, verified parent rule/decoder dependency, logtest input/output and end-to-end alert evidence.

## 9. Alert triage
Summarize three triage records, verdicts and next steps. Link the full notes in Findings.

## 10. Challenges, tuning and conclusion
Record actual troubleshooting, false positives, data-quality issues, tuning decisions and remaining limitations. Conclude only what the evidence demonstrates.

## 11. Evidence register
Link key claims to screenshots and outputs in Findings with filenames and captions.

## 12. References
- https://docs.splunk.com/
- https://documentation.wazuh.com/
- https://tryhackme.com/room/introtosiem
- https://tryhackme.com/room/splunkexploringspl
- https://attack.mitre.org/techniques/T1110/
