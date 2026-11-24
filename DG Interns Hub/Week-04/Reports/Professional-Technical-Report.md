# WEEK 04 — SIEM Monitoring & Splunk Investigation

**Technical Activity Report | DG Interns Hub**  
**Analyst:** Hafsa Khan  
**Focus:** SIEM Monitoring and Splunk Investigation  
**Evidence reviewed:** 34-image ZIP supplied; 8 Splunk screenshots selected.

## 1. Executive Summary
This report documents the Week 04 SIEM and Splunk work represented by the supplied evidence. The reviewed screenshots show Windows authentication-event searches, Linux failed-login searches, event aggregation, authentication dashboards, and alert configuration/triggering in Splunk. The Authentication Monitoring dashboard displays 5,403 total logons, comprising 476 successful and 4,927 failed logons. A separate Triggered Alerts view displays one high-severity alert named “Bruteforce Login Attempts”. These values are transcribed from the screenshots and are not independently re-created or re-validated in this report.

## 2. Objectives
Understand how a SIEM collects and presents security events, search authentication logs, identify failed login activity, summarize events by user and host, visualize authentication trends, and configure or review alerts for suspicious login behaviour.

## 3. Scope and Learning Activities
The Week 04 learning track included the TryHackMe rooms “Introduction to SIEM” and “Splunk: Exploring SPL”. The analyst has confirmed completing both rooms. The supplied ZIP does not include TryHackMe completion/badge screenshots, so platform completion evidence should be attached separately if required. The practical evidence reviewed here is limited to the Splunk screenshots listed below.

## 4. Tools and Data Sources
The screenshots show Splunk Enterprise Search & Reporting and dashboard interfaces, Windows Security event data (including EventCode 4625 and EventCodes 4624/4625), and Linux authentication/security log sources including `linux_secure` and Kali system log events. One screenshot shows a firewall-log search in an alert configuration. The screenshots display more than one Splunk interface/version context; this report does not assume that all captures came from one identical instance or time window.

## 5. Practical Methodology
The visible workflow consisted of: (a) searching for Windows failed-logon events using EventCode 4625; (b) reviewing Linux failed-authentication and SSH “Failed password” events; (c) aggregating Windows authentication events by user, computer name and event code; (d) reviewing authentication dashboards for successful/failed/total logons and source-account trends; and (e) reviewing alert configuration and the Triggered Alerts page. The report describes only the actions and outputs visible in the supplied screenshots.

## 6. Evidence and Observations
- **W4-01 — Windows EventCode 4625 search:** Splunk shows 40 matching events. Event details include Windows Security log fields such as EventCode and ComputerName.
- **W4-02 — Authentication Monitoring dashboard:** 476 successful logons, 4,927 failed logons and 5,403 total logons. Panels include top failed accounts, top source IPs and an authentication timeline.
- **W4-03 — Triggered Alerts:** One triggered alert, “Bruteforce Login Attempts”, with High severity and Real-time / Per Result mode.
- **W4-04 — Linux failed-authentication search:** `index=main failed` shows five events, including failed authentication-related messages from Kali logs.
- **W4-05 — Windows event aggregation:** SPL filters EventCode 4624 and 4625, excludes service accounts, then uses transaction/table/sort operations to summarize events by time, user, computer and event code. The interface reports 4,939 events and 102 statistics rows and explicitly indicates partial results.
- **W4-06 — Scheduled alert configuration:** An alert named “kareem” is shown in the Edit Alert screen. The visible search references a Windows firewall log and a source IP/destination port filter. The trigger is based on a result-count condition. This demonstrates configuration, not that this particular alert fired.
- **W4-07 — Windows Security Monitoring dashboard:** The dashboard is in edit mode and contains a Failed Login Attempts (EventCode 4625) chart panel.
- **W4-08 — Linux SSH failed-password search:** The `linux_secure` search returns three events containing “Failed password” from Kali SSH logs.

## 7. Key Findings
The evidence demonstrates practical use of Splunk to search Windows and Linux authentication data, inspect failed-login events, aggregate Windows logon activity, and present authentication metrics in dashboards. The screenshots also show both alert configuration and a separate triggered high-severity brute-force alert. The displayed dashboard totals indicate that failed logons form the majority of the logons represented in that dashboard; this is an observation about the displayed dataset only and is not proof of a confirmed compromise.

## 8. Evidence Limitations and Validation Notes
The screenshots contain different visible dates, hosts, interfaces and time ranges. The 4,939-event aggregation screenshot is explicitly marked as partial results. The alert configuration screenshot and triggered-alert screenshot show different alert names, so they must not be described as the same alert lifecycle. The SSH dashboard screenshot supplied separately is an editor view with a panel value of 3; it is not a final dashboard screenshot. The Add Data screenshot shows the source-selection stage only and does not prove ingestion completed. TryHackMe completion screenshots are not present in the supplied ZIP. Verify that each image is the analyst’s own lab evidence and redact information that should not be shared.

## 9. Conclusion
The supplied Week 04 evidence provides a coherent demonstration of core SIEM investigation tasks: searching authentication events, identifying failed logons across Windows and Linux sources, summarizing event activity, visualizing authentication behaviour, and reviewing alert workflows. The evidence supports the specific observations recorded in this report. Any claim beyond these visible results should be supported with additional original screenshots or exported results.

## 10. Recommended Final Submission Attachments
Attach the eight selected Splunk screenshots in the accompanying evidence ZIP. Add separate TryHackMe completion screenshots for “Introduction to SIEM” and “Splunk: Exploring SPL” if platform proof is required. If available, include the final (non-edit-mode) SSH dashboard and exported alert/search results.

## Appendix A — Screenshot Evidence Register
| Evidence ID | Screenshot description |
|---|---|
| W4-01 | Windows Security Event ID 4625 search — 40 matching events |
| W4-02 | Authentication monitoring dashboard — 476 successful, 4,927 failed, 5,403 total logons |
| W4-03 | Triggered high-severity “Bruteforce Login Attempts” alert |
| W4-04 | Linux failed-authentication search — five events |
| W4-05 | Windows authentication aggregation — 4,939 events, 102 statistics rows, partial results |
| W4-06 | Scheduled firewall-log alert configuration — configuration only |
| W4-07 | Windows Security Monitoring dashboard panel in edit view |
| W4-08 | Linux SSH failed-password investigation — three events |
