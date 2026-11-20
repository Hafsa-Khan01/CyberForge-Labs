# Lab 01 — SIEM Fundamentals

## Objective
Explain how a Security Information and Event Management (SIEM) platform collects, normalises, correlates, searches and alerts on security telemetry.

## Core concepts
- **Event:** one recorded activity, such as a failed logon or process start.
- **Log source:** system producing events (Windows, Linux, firewall, endpoint agent, application).
- **Collector/forwarder:** component that transports events to the SIEM.
- **Parsing and normalisation:** extracting fields and mapping different source formats into consistent fields.
- **Index/storage:** searchable event repository with retention controls.
- **Detection:** search, rule or correlation logic that identifies suspicious patterns.
- **Alert/case:** an actionable finding routed to an analyst.
- **Enrichment:** adding context such as asset owner, user role, reputation or threat intelligence.
- **Tuning:** reducing false positives while preserving detection coverage.

## Typical pipeline
1. Generate telemetry at an endpoint or network device.
2. Collect events using an agent, syslog, API or file input.
3. Parse timestamps and fields; normalise where possible.
4. Store events in an index or data store.
5. Search or correlate activity over a time window.
6. Generate an alert when a defined condition is met.
7. Triage, scope, contain, eradicate, recover and document.

## Practical exercise
Choose one Windows Security event and one Linux authentication event from the lab. For each, record:
- source host and operating system;
- event timestamp and timezone;
- username and source IP, if present;
- event/action and outcome;
- collector/agent used;
- destination index or Wazuh manager;
- how an analyst would use the event.

Do not copy illustrative values and label them as collected evidence. Use the actual event fields visible in the lab.

## Questions and answers
**1. Why is a SIEM useful?**  
It centralises security telemetry and enables search, correlation, alerting and investigation across multiple systems.

**2. Is a SIEM itself an EDR?**  
No. An EDR focuses on endpoint visibility and response. A SIEM aggregates and correlates telemetry from many sources; it may integrate with EDR tools.

**3. Why does time synchronisation matter?**  
Correlation depends on event ordering. Incorrect clocks or timezone parsing can make related events appear out of sequence.

**4. What is the difference between an event and an alert?**  
An event is raw or processed telemetry. An alert is a detection outcome that meets a defined rule or analytic condition.

**5. Why should analysts validate data before writing detections?**  
A search cannot reliably detect activity if events are missing, delayed, incorrectly parsed or stored under unexpected field names.

## Evidence record
Add a screenshot/export of the actual event search and note the source, time range, index and fields. Do not state that the exercise ran until evidence is captured.
