# 2. Log Ingestion Methods: Splunk Universal Forwarder and Wazuh Agent

## What is log ingestion?
Log ingestion is the collection and delivery of event data from its source to a platform where it can be parsed, stored, searched and analyzed.

## Common ingestion methods

| Method | How it works | Suitable sources | Advantages | Considerations |
|---|---|---|---|---|
| Agent / forwarder | Software on a host reads selected logs and sends them centrally | Windows Event Logs, Sysmon, Linux files | Host-level visibility and configurable collection | Requires deployment, permissions and maintenance |
| Syslog | A device sends messages to a syslog receiver, commonly over UDP or TCP; TLS is available in supported designs | Linux syslog, firewalls, routers | Broad device support | UDP may lose messages; secure transport and parsing matter |
| API | SIEM polls or receives events through an application's API | Cloud, identity and SaaS platforms | Useful when agents are unavailable | API limits, authentication, pagination and polling delay |
| File monitoring | Collector watches a file and reads appended records | /var/log/auth.log, application logs | Simple for text logs | Rotation, permissions, multiline records and duplicates |

## Splunk Universal Forwarder
The Splunk Universal Forwarder (UF) is a lightweight collector that sends selected data to Splunk receiving infrastructure.

Typical workflow:
1. Install UF on the endpoint.
2. Configure inputs for the intended sources, such as Windows Security Event Logs or a Linux log file.
3. Configure the receiving Splunk instance as the destination.
4. Confirm receiving ports and network connectivity.
5. Search the expected index and sourcetype to verify ingestion.

Example Windows input configuration concept:

    [WinEventLog://Security]
    disabled = 0
    index = lab
    renderXml = 1

The actual configuration depends on the installed UF version and environment. Sysmon events are collected from the Sysmon Windows Event Log channel using a compatible input/add-on configuration.

## Wazuh agent
The Wazuh agent runs on a monitored endpoint and communicates with the Wazuh manager. It collects configured events and supports endpoint monitoring features such as log collection, file integrity monitoring (FIM) and security configuration assessment.

Typical workflow:
1. Install and register the agent with the Wazuh manager.
2. Confirm that it is connected and reporting.
3. Configure relevant log sources and monitoring settings.
4. Verify events reach the manager and are processed.
5. Review alerts and indexed events in the dashboard.

## Splunk UF vs. Wazuh agent

| Area | Splunk Universal Forwarder | Wazuh agent |
|---|---|---|
| Primary role | Forward selected data to Splunk | Send endpoint telemetry to Wazuh manager |
| Destination | Splunk receiving/indexing infrastructure | Wazuh manager |
| Configuration | Inputs, outputs and add-ons/apps | Agent enrollment, log collection and modules |
| Windows visibility | Windows Event Logs, including Security and Sysmon | Configured Windows event channels and endpoint capabilities |
| Linux visibility | Monitors configured files and supported inputs | Collects configured logs and endpoint telemetry |
| Detection processing | SPL searches and Splunk alert rules | Wazuh decoders and rules on manager |
| Additional endpoint functions | Primarily data forwarding | Includes FIM and security configuration assessment |

## Example ingestion paths
**Splunk:** Windows Security / Sysmon → Universal Forwarder → Splunk receiver/indexer → lab index → SPL search.

**Wazuh:** Windows / Ubuntu → Wazuh agent → Wazuh manager (decoders and rules) → Wazuh indexer → dashboard.

These are different architectures. A Wazuh agent does not send events to a Splunk indexer by default.

## Operational checks
- Verify timestamps and time zones across endpoints and the SIEM.
- Collect only the required channels and files.
- Check agent/forwarder connectivity, ports and firewall rules.
- Confirm the destination index or Wazuh agent status before troubleshooting detections.
- Watch for duplicate events, log rotation issues and missing permissions.
- Never publish passwords, API tokens, enrollment keys or other secrets.
