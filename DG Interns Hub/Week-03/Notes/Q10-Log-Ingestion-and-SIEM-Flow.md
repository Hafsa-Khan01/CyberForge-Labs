# Q10. Log ingestion and SIEM collection

## What is log ingestion?
Log ingestion is the process of collecting records from endpoints, servers, network devices, and applications and making them available to a central monitoring platform. A SIEM receives these records, parses or normalizes fields, enriches them with context, stores them, and evaluates them using searches, rules, and correlation logic.

## Typical flow from source to dashboard

1. **Log source:** Windows Event Log/Sysmon, Linux journald/syslog/auditd, firewall, IDS such as Snort, or an application.
2. **Collection:** An agent, forwarder, syslog receiver, API integration, or network input reads the records.
3. **Transport:** Events are securely sent to the central platform, often with buffering/retry.
4. **Parsing and normalization:** The SIEM extracts timestamps, hostnames, users, process names, IP addresses, event IDs, and other fields into a searchable schema.
5. **Enrichment:** Asset inventory, threat intelligence, identity, geolocation, or vulnerability context may be added.
6. **Detection and correlation:** Rules and analytics identify patterns across one or more sources.
7. **Storage and indexing:** Events are retained and indexed according to retention and access policies.
8. **Dashboard and alert:** Analysts see event counts, timelines, notable alerts, and investigation context.
9. **Investigation and response:** Analysts validate the alert, scope affected assets, document findings, and take authorized response actions.

## Wazuh and Splunk examples
- **Wazuh:** Endpoint agents collect supported operating-system and security events and send them to the Wazuh manager. The platform analyses events and presents alerts through its indexing and dashboard components. Agent configuration and supported log sources determine what is collected.
- **Splunk:** Universal Forwarders or other inputs collect and forward machine data to Splunk indexers. Parsing, indexing, searches, alerts, and dashboards make the data available to analysts. Deployment architecture and configuration determine the exact path.

## Why ingestion quality matters
- Incorrect timestamps can break event timelines.
- Missing or duplicated events can distort counts.
- Poor parsing can hide important fields.
- Unprotected transport can expose sensitive logs.
- Excessive noise can overwhelm analysts.
- Retention and access controls must meet operational and privacy requirements.

## SOC example
A Windows Sysmon process event, a DNS query, and a Snort network alert may arrive from different sources. A SIEM can correlate host, time, process, and destination information to help an analyst investigate whether the activity forms one suspicious sequence. Correlation depends on reliable timestamps, host identity, and field normalization.
