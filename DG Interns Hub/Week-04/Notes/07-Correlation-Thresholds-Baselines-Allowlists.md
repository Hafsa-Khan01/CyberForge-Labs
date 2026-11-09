# 7. Correlation Rules, Thresholds, Baselines and Allowlists

These techniques turn individual events into useful detections. They solve different problems and are not interchangeable.

## Comparison

| Technique | What it does | When to use it | Example | Main risk |
|---|---|---|---|---|
| Correlation rule | Combines related events or conditions | Several events together are more meaningful than one | Failed logons followed by success from same source | Incorrect joins or weak time/entity matching |
| Threshold | Alerts when a count or value crosses a limit | Repeated activity is suspicious | Five failures from one IP in five minutes | Too low creates noise; too high misses activity |
| Baseline | Describes normal behavior for a system, user or environment | Deviation from normal is the signal | New SSH source for a server | Normal behavior changes; baseline may learn malicious activity |
| Allowlist | Records known, verified benign entities for a specific detection context | A known source repeatedly triggers a rule | Approved scanner IP for a defined scan detection | Broad or stale exclusions can hide attacks |

## 1. Correlation rules
A correlation rule connects events using shared attributes such as source IP, username, host, process, destination or time window.

Example: five failed logons from an IP followed by a successful logon to the same account may indicate password guessing followed by account access.

Useful correlation keys:
- Source IP address
- Username or account ID
- Hostname or asset ID
- Process ID or process lineage
- Destination IP and port
- Event timestamp

Good correlation requires consistent field extraction and reliable timestamps. Account for NAT, shared accounts, clock drift and duplicate events.

## 2. Thresholds
A threshold is a numeric condition.

Examples:
- Five failed logons from one source in five minutes.
- Ten blocked connections to one host in one minute.
- A process creates an unusually large number of child processes in a short period.

Thresholds are useful for burst behavior. Test against normal and suspicious activity and tune to the environment.

## 3. Baselines
A baseline represents expected activity over a period of observation.

Examples:
- Typical logon hours for a service account.
- Normal outbound destinations for a server.
- Common parent-child process pairs on a workstation.
- Normal daily authentication volume.

A baseline supports anomaly detection, but it is not automatically trustworthy. A baseline created while an attacker is active may learn malicious behavior as normal. Reassess after infrastructure or business-process changes.

## 4. Allowlists
An allowlist is a documented exception for a known and verified entity or behavior.

Examples:
- A fixed scanner address approved for a particular test.
- A known service account performing a documented scheduled task.
- An approved management tool creating a predictable process pattern.

An allowlist should be narrowly scoped, supported by an owner and business reason, reviewed periodically, and given an expiry or review date where practical. Do not allowlist an entire subnet or process family simply to remove noise without justification.

## Choosing the right technique
- Use a **threshold** for repeated activity.
- Use a **correlation rule** when multiple events or stages must be connected.
- Use a **baseline** when deviation from normal behavior is the signal.
- Use an **allowlist** only for a verified, documented exception.

A mature detection may combine techniques. For example, a correlation rule can require a failed-login threshold and raise severity if the same source later succeeds against a privileged account, while excluding a narrowly documented test scanner from a separate network-scan rule.
