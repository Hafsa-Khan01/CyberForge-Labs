# Week 04 — Findings and Practical Evidence

## Evidence groups

| Group | Required evidence |
|---|---|
| Splunk setup | Login page, `lab` index and index configuration |
| Splunk ingestion | UF inputs/outputs, Windows Security/Sysmon events, Ubuntu auth.log events, successful `index=lab` searches |
| Wazuh setup | Dashboard, manager status and both enrolled agents |
| Wazuh FIM | Monitored test folder, file change and resulting alert |
| Attack-to-alert | Authorized Hydra test, raw SSH event, parsed fields and alert/search; Nmap `-sS` command, event and detection |
| SPL detections | Search and results for all five detections |
| Scheduled alerts | Both alert configurations and trigger evidence |
| Dashboard | Four-panel dashboard screenshot |
| Wazuh custom rule | Rule source and `wazuh-logtest` output |

## Triage records
- [Triage 01](Triage-01.md)
- [Triage 02](Triage-02.md)
- [Triage 03](Triage-03.md)

## Evidence handling
Preserve original screenshots. Use descriptive filenames and captions. Record actual timestamps/time zone and host roles. Redact credentials, tokens, private keys and unrelated personal information. Keep raw event and parsed-field views where possible.
