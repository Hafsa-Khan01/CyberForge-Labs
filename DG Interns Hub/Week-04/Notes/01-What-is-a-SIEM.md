# 1. What Is a SIEM?

## Definition
A Security Information and Event Management (SIEM) platform collects security-relevant data from multiple systems, normalizes and stores it, makes it searchable, and helps security teams identify suspicious activity. It can correlate events from endpoints, servers, identity systems, firewalls, applications and network devices.

A SIEM alert is an investigative lead, not automatic proof that an attack occurred.

## Core components

| Component | Purpose | Example |
|---|---|---|
| Data sources | Generate events | Windows Security, Sysmon, Linux authentication, firewall logs |
| Collection | Obtain and transport events | Splunk Universal Forwarder, Wazuh agent, syslog |
| Parsing and normalization | Extract consistent fields | Username, source IP, event ID, timestamp |
| Storage and indexing | Retain events for retrieval | Splunk index, Wazuh indexer |
| Search and analytics | Query and correlate events | SPL searches, Wazuh rules |
| Detection and alerting | Identify patterns matching logic | Repeated failed logons |
| Visualization | Present activity and trends | Dashboards and reports |
| Investigation workflow | Support triage and response | Alert queue, case notes, escalation |

## SIEM data flow
1. **Generate:** An endpoint, server, application or network device creates an event.
2. **Collect:** An agent, forwarder, syslog service, API integration or file monitor obtains it.
3. **Transport:** The event is sent to the SIEM collection or processing layer.
4. **Parse and normalize:** The platform extracts useful fields and maps data into a searchable structure.
5. **Index and retain:** Events are stored under the configured retention policy.
6. **Search and correlate:** Analysts and detection rules examine individual events or patterns across sources.
7. **Alert:** A matching detection creates an alert, subject to its configured conditions.
8. **Triage and respond:** An analyst validates the evidence, records a verdict and escalates or closes the case.

## SIEM vs. log management vs. SOAR vs. EDR

| Technology | Main purpose | Typical capabilities | Does not replace |
|---|---|---|---|
| SIEM | Central security monitoring and detection | Collect, normalize, search, correlate and alert | Endpoint protection or all response automation |
| Log management | Store and manage logs | Centralized collection, retention, search and access | Security-focused detection and response workflows |
| SOAR | Orchestrate and automate security operations | Playbooks, enrichment, ticketing, approvals and response actions | Telemetry sources and detection engineering |
| EDR | Monitor and protect endpoints | Endpoint telemetry, behavioral detection, investigation and containment | Organization-wide correlation across every log source |

## Example
A Windows host records repeated failed sign-ins. A firewall separately records connections from the same source. A SIEM can correlate those records and help an analyst assess whether password guessing is occurring. Log management may retain both records; SOAR may automate enrichment or ticket creation; EDR contributes endpoint-level visibility and response.

## Key points
- SIEM provides a searchable and correlatable view of security telemetry.
- Detection quality depends on useful log sources, correct parsing, reliable timestamps and careful tuning.
- An alert is not proof of malicious activity.
- Retention, access control and data quality are part of SIEM operations.
