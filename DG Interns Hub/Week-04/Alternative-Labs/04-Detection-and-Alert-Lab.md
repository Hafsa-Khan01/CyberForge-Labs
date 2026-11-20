# Lab 04 — Detection Engineering and Alert Validation

## Objective
Translate attacker behaviour into observable telemetry, a repeatable analytic, an alert condition and an investigation path.

## Detection design record
For every detection, document:
1. Behaviour and threat technique.
2. Required log source and event coverage.
3. SPL/Wazuh logic and field assumptions.
4. Threshold and time window.
5. Expected benign causes.
6. Severity and routing.
7. Validation evidence.
8. Tuning and known blind spots.

## Example detection patterns

### Repeated failed Windows logons
- Telemetry: Windows Security Event ID 4625.
- SPL starting point:

```spl
index=lab (EventCode=4625 OR EventID=4625)
| bin _time span=5m
| stats count as failures by _time host user
| where failures >= 5
```

Tune by user, host, source address and logon type. A burst can result from a mistyped password, stale service credentials or a scheduled task as well as malicious activity.

### SSH password failures
- Telemetry: Linux authentication logs.
- SPL starting point:

```spl
index=lab sourcetype=linux_secure "Failed password"
| rex "from (?<src_ip>\d{1,3}(?:\.\d{1,3}){3})"
| bin _time span=5m
| stats count as failures values(user) as targeted_users by _time host src_ip
| where failures >= 5
```

Check whether the source is an approved scanner, administrator jump host or test machine before escalation.

### PowerShell process execution
- Telemetry: Sysmon Event ID 1 or an equivalent process creation source.
- Review image, parent image, user and command line. Encoded commands, download cradles and unusual parent-child relationships may merit investigation, but command-line flags alone do not prove malicious intent.

## Wazuh custom rule workflow
1. Inspect the actual alert JSON and identify the parent rule ID and fields.
2. Use `wazuh-logtest` to test a representative event.
3. Write a local rule with a unique ID in the permitted local range (the assignment asks for 100000 or higher).
4. Validate XML syntax and test again.
5. Deploy only after confirming the rule matches the intended event and does not over-alert.
6. Restart/reload the relevant Wazuh component according to the installed version's procedure.
7. Confirm the generated alert in the actual manager output.

**Do not use a guessed parent rule ID.** The starter XML in `../Detections/wazuh-local-rules.xml` contains an explicit placeholder that must be replaced with the verified ID.

## Scheduled alerts
For each scheduled alert, define:
- search and index;
- schedule and time range;
- trigger condition;
- suppression/throttling;
- severity and owner;
- notification/action;
- test event and resulting alert evidence.

A saved search is not necessarily a scheduled alert. Capture the schedule and trigger configuration, plus an actual test result.

## Four-panel dashboard suggestion
1. Event volume over time.
2. Failed authentication by source/user.
3. Top hosts and sourcetypes.
4. Process or network activity of interest.

Use panels that have validated data. Label empty or unavailable panels honestly rather than filling them with fabricated values.
