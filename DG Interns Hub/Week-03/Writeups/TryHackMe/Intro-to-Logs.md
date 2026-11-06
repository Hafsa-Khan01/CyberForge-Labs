# TryHackMe — Intro to Logs

## Scope
Fundamental log concepts: event sources, timestamps, severity, structured fields and the role of logs in operational troubleshooting and security monitoring.

## Technical focus
- A log record describes an event observed by an application, operating system or security control.
- Useful fields commonly include timestamp, host, source, process, event/message, severity and outcome.
- Time synchronization and consistent time zones are essential when correlating events across systems.
- Log rotation, retention and access controls affect investigation quality.

## Analysis method
1. Identify the source and purpose of the record.
2. Normalize the timestamp and identify the host and account/process context.
3. Separate the raw event from the analyst's interpretation.
4. Search for related events before and after the timestamp.
5. Preserve relevant records and document any gaps or parsing assumptions.

## SOC relevance
Reliable log interpretation is the foundation of alert triage, incident timelines, threat hunting and audit readiness.

## Evidence record
Attach the actual room-completion screenshot and relevant task evidence. Add observed examples only from the completed room; do not invent outputs.
