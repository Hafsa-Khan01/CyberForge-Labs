# Week 04 — Evidence Register

Use this register to connect each practical claim to a real artifact. Keep original screenshots unchanged; use descriptive filenames and redact secrets before publishing.

| ID | Evidence item | Suggested filename | What it should demonstrate |
|---|---|---|---|
| E-01 | Splunk version / home | `E-01-splunk-instance.png` | Running Splunk instance and version |
| E-02 | Lab index | `E-02-lab-index.png` | Dedicated index exists |
| E-03 | Windows UF status | `E-03-windows-forwarder.png` | Forwarder service and connection |
| E-04 | Windows Security events | `E-04-security-events.png` | Actual Security events searchable |
| E-05 | Sysmon events | `E-05-sysmon-events.png` | Actual Sysmon telemetry searchable |
| E-06 | Ubuntu auth log | `E-06-ubuntu-auth.png` | Linux authentication events searchable |
| E-07 | Wazuh manager | `E-07-wazuh-manager.png` | Manager service/dashboard status |
| E-08 | Agent status | `E-08-wazuh-agents.png` | Enrolled endpoint agents |
| E-09 | FIM alert | `E-09-wazuh-fim.png` | Real file integrity event |
| E-10 | SSH test | `E-10-ssh-test.png` | Authorised test and matching event |
| E-11 | Nmap test | `E-11-nmap-test.png` | Authorised scan and matching telemetry |
| E-12 | SPL detections | `E-12-spl-detections.png` | Executed queries and actual results |
| E-13 | Scheduled alerts | `E-13-scheduled-alerts.png` | Two configured alerts and conditions |
| E-14 | Dashboard | `E-14-siem-dashboard.png` | Four populated dashboard panels |
| E-15 | Wazuh custom rule | `E-15-wazuh-rule.png` | Rule configuration and verified ID |
| E-16 | Wazuh logtest | `E-16-wazuh-logtest.png` | Actual test input and decoder/rule match |

## Evidence metadata
For each artifact, record:
- capture date/time and timezone;
- machine/host role;
- tool and version;
- relevant index, source or rule ID;
- what the screenshot proves;
- any redactions or limitations.

## Handling
Do not upload credentials, API keys, private keys, session tokens or unredacted sensitive logs. Avoid exposing public IPs or personal account data unless the assignment specifically requires it and disclosure is safe. Store evidence under this folder and link it from the relevant triage note or report section.
