# Q1. Endpoint Detection and Response (EDR)

## What is EDR?
Endpoint Detection and Response is a security approach and toolset that continuously collects activity from endpoints—such as workstations and servers—and helps security teams detect, investigate, and respond to suspicious behaviour. An EDR platform commonly gathers process, user, file, registry, network-connection, and security telemetry. It can correlate events over time and may support response actions such as isolating a device or stopping a process, subject to policy and analyst authorization.

## Why endpoint data matters to a SOC
- **Process visibility:** shows which executable ran, its parent process, command line, and user context.
- **Account activity:** helps investigate logons, privilege use, and account changes.
- **File and registry activity:** can reveal dropped files, persistence changes, or unexpected modifications.
- **Network context:** connects a process to remote IP addresses, ports, and DNS lookups.
- **Investigation timeline:** allows analysts to reconstruct what happened before and after an alert.
- **Detection and response:** provides evidence to scope an incident and contain affected endpoints.

## EDR compared with traditional antivirus

| Area | Traditional antivirus | EDR |
|---|---|---|
| Main emphasis | Prevent or quarantine known and suspicious malware | Continuous telemetry, detection, investigation, and response |
| Detection | Historically signature-focused; modern AV also uses heuristics and behaviour | Correlation of endpoint events, behaviour analytics, rules, and threat intelligence |
| Visibility | Often focused on files and malware verdicts | Broader process, identity, file, registry, and network activity |
| Investigation | Basic alerts and quarantine history | Timelines, process trees, searchable telemetry, incident context |
| Response | Block, quarantine, remediate | May additionally isolate hosts, kill processes, or support guided response |

The distinction is not absolute: modern antivirus products may include EDR capabilities, and EDR platforms often include prevention features.

## SOC example
A user reports an unexpected PowerShell window. An analyst can use endpoint telemetry to inspect the command line, parent process, logged-on account, file writes, DNS queries, and outbound connections. No single event proves compromise; the analyst correlates context and validates the activity.

## Key takeaway
EDR adds investigative context to endpoint protection. Endpoint data is valuable because it helps answer **what ran, who ran it, what it changed, and where it communicated**.
