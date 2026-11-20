# Lab 02 — Log Ingestion and Validation

## Objective
Trace Windows and Linux security logs from their source to the SIEM and verify that ingestion is working.

## Windows telemetry
Common sources include:
- Windows Security event log (authentication, account and audit events);
- Sysmon Operational log (process, network, file and registry telemetry);
- System and Application event logs.

A Splunk Universal Forwarder can monitor Windows event logs. Example input configuration (adapt to the installed version and approved lab configuration):

```ini
[WinEventLog://Security]
disabled = 0
index = lab
renderXml = true

[WinEventLog://Microsoft-Windows-Sysmon/Operational]
disabled = 0
index = lab
renderXml = true
```

Place configuration in the forwarder's local app configuration directory, validate the configuration, and restart the forwarder using the supported service procedure for the installed OS. Confirm that the receiver, forwarding port and index are configured consistently.

## Linux authentication telemetry
On Ubuntu/Debian systems, authentication events are commonly written to `/var/log/auth.log`. On some distributions, authentication records may instead be in the systemd journal or `/var/log/secure`.

Example Splunk monitor input:

```ini
[monitor:///var/log/auth.log]
disabled = 0
index = lab
sourcetype = linux_secure
```

Ensure the forwarder service account has appropriate read access. Avoid broad permissions such as making the entire log directory world-readable.

## Validation searches
Start by checking whether any events arrived:

```spl
index=lab earliest=-24h
| stats count by host source sourcetype
| sort - count
```

Inspect a small sample:

```spl
index=lab earliest=-24h
| head 20
| table _time host source sourcetype _raw
```

Check timestamp distribution:

```spl
index=lab earliest=-24h
| timechart span=1h count
```

## Validation checklist
- [ ] Source host is the expected endpoint.
- [ ] Events arrive within the expected delay.
- [ ] Correct index and sourcetype are populated.
- [ ] Timestamp and timezone are sensible.
- [ ] Relevant fields are extracted.
- [ ] Duplicate events are not inflating counts.
- [ ] No credentials or secrets are exposed in the event payload.
- [ ] Retention and access controls are appropriate.

## Troubleshooting
| Symptom | First checks |
|---|---|
| No events | Forwarder/agent service, network path, receiver, input enabled |
| Events in wrong index | Input stanza, deployment app, index existence and permissions |
| Wrong timestamps | Timezone, timestamp extraction, endpoint clock |
| Missing fields | Raw event format, sourcetype, parsing configuration |
| Duplicate events | Multiple monitor inputs, overlapping collection paths |
| Permission errors | Service account access to the specific log source |

## Evidence
Record the actual host, source, sourcetype, index, time range and result count. Add the real Splunk screenshot and (where useful) a redacted forwarder configuration. The searches above are examples, not proof of execution.
