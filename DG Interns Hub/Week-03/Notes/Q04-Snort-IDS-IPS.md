# Q4. How Snort works as an IDS/IPS

## What is Snort?
Snort is an open-source network intrusion detection and prevention system. It inspects network traffic using decoders, preprocessors/inspectors, and detection rules. Rules can match protocol fields, packet content, flow direction, TCP flags, and other conditions. Matching traffic can generate alerts or, in inline prevention deployments, be dropped or rejected according to configuration and mode.

## IDS mode
- Receives traffic from a monitoring interface or traffic mirror/TAP.
- Analyses packets and generates alerts when rules match.
- Normally observes traffic without blocking it.
- Useful for passive monitoring, detection tuning, baselining, and environments where blocking could disrupt services.

## IPS mode
- Operates inline in the traffic path.
- Can take prevention actions such as dropping traffic that matches configured rules.
- Useful when an organization needs active enforcement and has tested rules, reliable inline placement, and a rollback plan.
- A misconfigured rule or inline device can interrupt legitimate traffic.

## When a SOC uses each

| Mode | SOC use | Main consideration |
|---|---|---|
| IDS | Visibility, alerting, threat hunting, detection validation | Does not normally stop the traffic |
| IPS | Blocking known malicious or policy-violating traffic | False positives and availability impact must be managed |

## Basic workflow
1. Traffic reaches the Snort sensor.
2. Snort decodes packets and evaluates applicable detection logic.
3. Rules inspect packet and flow properties.
4. Matching rules produce alerts or configured inline actions.
5. Alerts are reviewed, enriched, correlated, and investigated by analysts.

## Important note
Snort syntax and supported options can vary between Snort 2 and Snort 3. Check the installed version and its documentation before applying a configuration or rule. The supplied internship starter rules are introductory examples, not a complete production detection policy.
