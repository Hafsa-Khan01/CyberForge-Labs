# Week 3 — Practical Evidence Report

## Scope

This report indexes the practical screenshots supplied for the Week 3 work on endpoint telemetry, Linux auditing, and network intrusion detection. It distinguishes visible evidence from tasks that still need a fresh verification screenshot.

## Evidence reviewed

The supplied archive contained 25 image files. The following material is relevant to the Week 3 technical evidence set:

### Windows Sysmon
- Sysmon installation/configuration and PowerShell verification.
- Windows Event Viewer / Sysmon Operational channel views.
- Event examples covering process creation, network activity, file creation, DNS queries, and registry value changes.

**Assessment:** The supplied screenshots support the Sysmon setup and several event-investigation activities. Keep the clearest individual event-detail screenshots in the evidence folder and label each by Event ID.

### Kali Linux and Nmap
- Terminal output showing network and Nmap activity.
- Scan results and related command-line evidence.

**Assessment:** Relevant evidence is present. In the final upload, include the command and target context in the screenshot filename or a short caption. Only scan systems for which authorization exists.

### Snort
- Snort installation/configuration terminal output.
- Snort rule and detection/alert output, including TCP scan-related traffic.

**Assessment:** Relevant setup and detection evidence is present. For a strong audit trail, pair the custom rule screenshot with the corresponding test traffic and alert output. Record the Snort version and lab network used; do not combine screenshots from different environments as if they were one run.

### Ubuntu auditd
- Package installation and service/configuration terminal output.

**Assessment:** The archive does not conclusively establish that `auditd.service` was active and that an audit event was successfully queried. Add fresh screenshots showing service status, audit subsystem status, and an actual event query before marking this practical verified.

## Excluded material

The archive also contained unrelated personal/promotional images and a non-informative image. These are intentionally excluded from the technical evidence set. Do not upload unrelated personal photographs or promotional graphics as lab evidence.

## Evidence integrity

- Screenshots must remain genuine captures from the lab environment.
- Do not edit terminal output, timestamps, event details, or alert contents.
- Redact credentials, tokens, and unrelated personal data before public upload.
- A prepared folder or report is not proof that an activity was completed.
- Any unresolved item must remain labelled as pending verification.

## Final status

| Area | Evidence assessment |
|---|---|
| Windows Sysmon | Evidence present; retain clear event-specific captures |
| Kali / Nmap | Evidence present |
| Snort | Evidence present; improve rule-to-alert pairing |
| Ubuntu auditd | Fresh running-service and event-query proof required |

This report is an evidence index, not a claim that every Week 3 requirement has been completed.
