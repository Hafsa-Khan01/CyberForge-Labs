# 4. Wazuh Architecture, Decoders and Rules

## Wazuh overview
Wazuh is an open-source security monitoring platform. Its architecture separates endpoint collection, event analysis, indexing and visualization.

## Main components

| Component | Role |
|---|---|
| Wazuh agent | Runs on monitored endpoints, collects configured logs and telemetry, and reports to the manager |
| Wazuh manager | Receives agent data, analyzes events, applies decoders and rules, and manages agent communications |
| Wazuh indexer | Stores and indexes alerts and related data for search |
| Wazuh dashboard | Web interface for viewing alerts, agent status and security data |

## Event flow
1. An endpoint generates a log or security event.
2. The agent collects configured data and sends it to the manager.
3. The manager receives and processes the event.
4. A decoder identifies the log format and extracts fields.
5. A rule evaluates the decoded event and determines whether it matches a detection condition.
6. Matching alerts are forwarded for indexing.
7. The dashboard presents indexed data for analyst review.

Not every collected event becomes a visible alert. Collection, decoding, rule matching, alert generation and indexing are separate stages.

## Decoders
A decoder interprets a raw log message, identifies its format and extracts useful fields, such as:
- Source IP address
- Username
- Authentication result
- Process name
- Event ID
- Port or service information

A decoder makes raw text understandable to detection rules. If parsing is incorrect, a rule that depends on extracted fields may not behave as expected.

## Rules
A Wazuh rule evaluates an event or sequence/context of events against defined conditions. It can match decoded fields, event IDs, source information, frequency or relationships to other rules. A matching rule can generate an alert with a rule ID, description, level and metadata.

Custom rules are commonly placed in the local rules file and should use IDs in the local custom range (100000 and above), avoiding conflicts with existing rules.

## Wazuh rule levels 0–15

| Level | General interpretation | Analyst meaning |
|---:|---|---|
| 0 | Ignored / no alert | Event is intentionally not raised as an alert |
| 1–3 | Informational / low significance | Contextual or low-priority activity |
| 4–7 | Low | Relevant event that may need basic review |
| 8–10 | Medium | More significant activity that may require investigation |
| 11–12 | High | Serious activity requiring prompt investigation |
| 13–15 | Critical | Very high-severity match requiring urgent attention |

Levels indicate configured severity or importance, not proof of maliciousness. Exact descriptions and behavior depend on rule configuration and Wazuh version.

## Example: repeated SSH failures
1. Ubuntu writes failed SSH authentication messages to its authentication log (commonly /var/log/auth.log on Ubuntu).
2. The Wazuh agent is configured to collect that log.
3. The manager receives the message.
4. A decoder extracts fields such as source IP and username when supported by the message format.
5. A built-in or custom rule matches failed authentication activity.
6. The alert is indexed and shown in the dashboard.

## Testing a custom rule
1. Review the raw log line the rule should detect.
2. Confirm that Wazuh decodes it and identify extracted fields.
3. Add the custom rule while preserving valid XML structure.
4. Run wazuh-logtest with a representative sample event.
5. Confirm decoder name, extracted fields, matched rule ID and level.
6. Review manager logs and the dashboard after testing actual collected events.

A successful wazuh-logtest match proves that the supplied sample matches the tested decoder/rule logic. It does not prove that an agent is collecting the event or that the full alert pipeline works end to end.

## Operational cautions
- Back up local rules before editing.
- Validate XML and avoid reusing rule IDs.
- Test expected matches and benign events that should not match.
- Set severity according to impact and confidence.
- Document the source event, expected fields, rule conditions and limitations.
