# Week 04 — SIEM in Practice: Splunk, Wazuh and Log Ingestion

**Analyst:** Hafsa Khan  
**Programme:** DG Interns Hub  
**Topic:** SIEM deployment, telemetry ingestion, detection engineering and SOC triage  
**Reporting date:** 24 November 2026

## Executive summary

Week 04 focused on practical Security Information and Event Management (SIEM) workflows using Splunk and Wazuh. The analyst confirmed completion of the assigned learning and practical activities, including both TryHackMe rooms, SIEM and log-ingestion work, SPL detection exercises, Wazuh monitoring, controlled validation and SOC triage documentation.

This report consolidates the technical objectives, implementation workflow, detection coverage and investigation practices. Eight illustrative/reference screenshots are included in the [Evidence folder](../Evidence/).

## 1. Learning objectives
- Explain SIEM architecture and the event-to-alert lifecycle.
- Understand collection and ingestion from Windows and Linux endpoints.
- Use SPL to filter, extract, aggregate and visualise security events.
- Understand Wazuh manager/agent architecture, decoders, rules and FIM.
- Map suspicious authentication and network discovery behaviour to telemetry.
- Design, validate and tune detections.
- Apply a consistent SOC triage process.

## 2. TryHackMe room completion

The analyst confirmed completion of both assigned rooms:
1. **Introduction to SIEM** — https://tryhackme.com/room/introtosiem
2. **Splunk: Exploring SPL** — https://tryhackme.com/room/splunkexploringspl

## 3. Lab architecture and telemetry

The practical work covered Splunk Enterprise as the central search and analysis platform, Windows Security and Sysmon telemetry, Ubuntu authentication logs, and Wazuh endpoint monitoring. The workflow included checking event arrival, reviewing raw events and timestamps, validating extracted fields and using the collected telemetry for detection and investigation.

## 4. Splunk and SPL detection engineering

The Week 04 detection set includes searches for:
1. Failed logons per user.
2. PowerShell process creation.
3. New user account creation.
4. SSH failures per source IP.
5. Rare parent-child process pairs.

SPL workflows use filtering, field selection, aggregation, extraction and time-series analysis. Detection validation considers the actual index, sourcetype, event fields, time range and normal baseline activity. Scheduled alerts and dashboard panels support monitoring and investigation.

## 5. Wazuh monitoring

The Wazuh work covered manager and agent roles, decoders, rule evaluation and File Integrity Monitoring. Rule testing and event review form part of the validation workflow. A rule match should be interpreted in context and correlated with the relevant endpoint telemetry.

## 6. Controlled security validation

Authorised lab activities included controlled SSH authentication testing and Nmap network discovery validation. These activities support investigation of behaviours associated with MITRE ATT&CK **T1110 — Brute Force** and **T1046 — Network Service Discovery**. A scan or failed login event is an investigation lead and does not, by itself, prove compromise.

## 7. SOC alert triage

Three triage records are included for investigating authentication failures, suspicious PowerShell activity and network discovery/unusual connections. The investigation workflow considers alert context, affected assets and accounts, related events, baseline behaviour, assessment, confidence, verdict and response actions.

## 8. Deliverables
- Eight SIEM theory notes.
- Two TryHackMe room writeups.
- Supplementary SIEM and SPL practical references.
- Five SPL detection searches.
- Wazuh rule and monitoring documentation.
- Scheduled alert and dashboard guidance.
- Three SOC triage records.
- SIEM/SPL cheat sheets.
- Final report and presentation outline.

## 9. Evidence register

> **Evidence provenance:** The screenshots in this folder are illustrative/reference images and were not captured from the analyst's own lab sessions. They are included only to support visual understanding of the documented topics; they must not be interpreted as original execution evidence or as proof that a specific result occurred in the analyst's environment. The analyst confirms that the assigned learning and practical activities were completed. The completion status is based on that confirmation, not on these screenshots.


The [Evidence Register](../Findings/Evidence-Register.md) connects practical claims to artifacts. Eight illustrative/reference screenshots are available in [Evidence](../Evidence/). The descriptions below explain the concepts represented by the images; they are not records of screenshots captured from the analyst's own lab.

## 10. Evidence-based technical review

| Evidence ID | Observation |
|---|---|
| W4-01 | Windows Security EventCode 4625 search returned 40 matching events. |
| W4-02 | Authentication dashboard displayed 476 successful, 4,927 failed and 5,403 total logons. |
| W4-03 | Triggered Alerts displayed one High-severity alert named “Bruteforce Login Attempts”. |
| W4-04 | Linux failed-authentication search `index=main failed` returned five events. |
| W4-05 | Windows 4624/4625 aggregation showed 4,939 events and 102 statistics rows; the interface marked results as partial. |
| W4-06 | Scheduled alert “kareem” was shown in configuration with a firewall-log search and result-count trigger. This proves configuration only, not that this alert fired. |
| W4-07 | Windows Security Monitoring dashboard was in edit mode with a Failed Login Attempts (EventCode 4625) panel. |
| W4-08 | Linux `linux_secure` SSH failed-password search returned three events. |

### Evidence interpretation

The reference images depict examples of Windows and Linux authentication searches, event aggregation, dashboard visualisation and alert configuration/review. They do not establish that these exact outputs were generated in the analyst's own environment. The displayed failed-logon count is higher than the successful count in that dashboard dataset; this is an observation about the displayed data and is not proof of compromise.

### Evidence limitations

The reference screenshots show different dates, hosts, interfaces and time ranges. The 4,939-event result is explicitly partial. The configured alert “kareem” and triggered alert “Bruteforce Login Attempts” are different alerts and must not be presented as one alert lifecycle. The dashboard screenshot is in edit mode. The Add Data screenshot shows source selection rather than completed ingestion. TryHackMe completion pages were not included in the uploaded image set; room completion is based on the analyst's confirmation.

## 11. Conclusion

Week 04 learning and practical activities are complete as confirmed by the analyst. The repository contains the weekly notes, room writeups, detection references, triage documentation, report and eight selected screenshots. The report distinguishes observed screenshot results from broader completion claims and records the limitations visible in the evidence.

## References
- [Splunk Documentation](https://docs.splunk.com/)
- [Splunk Search Reference](https://docs.splunk.com/Documentation/Splunk/latest/SearchReference/WhatsInThisManual)
- [Wazuh Documentation](https://documentation.wazuh.com/)
- [Wazuh Ruleset](https://documentation.wazuh.com/current/user-manual/ruleset/index.html)
- [MITRE ATT&CK T1110 — Brute Force](https://attack.mitre.org/techniques/T1110/)
- [MITRE ATT&CK T1046 — Network Service Discovery](https://attack.mitre.org/techniques/T1046/)
