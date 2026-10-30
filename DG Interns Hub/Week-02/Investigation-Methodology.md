# Week 02 | Investigation Methodology and Analytical Standard

## Purpose

This document defines a repeatable method for turning packet captures, Nmap output and Windows telemetry into defensible technical observations. It is intended to keep practical work reproducible and distinguish evidence from interpretation.

## 1. Investigation lifecycle

### 1.1 Define the question

Write one clear question before collecting data. Examples include:
- Which assigned lab hosts responded to discovery probes?
- Which TCP services were reachable during the scan window?
- Does the capture contain a complete TCP handshake?
- Which failed-logon records are present in the selected Security-log window?

A question should be specific enough to determine the required data source and collection window.

### 1.2 Confirm authorization and scope

Record the assigned systems, permitted actions, network range, time window and any restrictions. Stop if a target is outside scope or cannot be verified as an assigned lab asset.

### 1.3 Preserve collection context

For each artifact, record:
- Host and operating system used for collection
- Tool and version, where relevant
- Date/time and time zone
- Target or data-source scope
- Exact command, filter or query
- Original output filename

Keep original artifacts unchanged. Use separate copies for annotation or redaction.

### 1.4 Validate the artifact

Confirm that the file opens, its contents match the stated collection method and the screenshot corresponds to the original artifact. Check timestamps, endpoints, event IDs and output format. Do not rely on a screenshot alone when the original PCAP, XML or CSV is available.

### 1.5 Analyze and correlate

Use the following sequence:
1. Describe the direct observation.
2. Identify the fields or packets supporting it.
3. Compare with related records from the same time window.
4. Consider expected lab activity and benign explanations.
5. State what the evidence cannot establish.
6. Recommend a proportionate next validation step.

### 1.6 Write a defensible conclusion

Use precise language:
- **Observed:** directly present in the artifact.
- **Indicated:** supported by evidence but not fully confirmed.
- **Hypothesis:** plausible explanation requiring validation.
- **Not established:** conclusion the available evidence does not support.

Do not label an event, packet or open port malicious in isolation.

## 2. Evidence-to-claim matrix

| Data source | Claims it can support | Claims it cannot support alone |
|---|---|---|
| Wireshark PCAP/PCAPNG | Visible packet fields, endpoints, timing, flags and protocol exchanges | Full application content inside encrypted traffic; intent or compromise |
| Nmap output | Host/port states and probe-based service identification at scan time | Exploitability or vulnerability solely from an open port |
| Windows Security/System logs | Events recorded by the host under its configured auditing and retention | Activity that was never logged or has been removed/expired |
| PowerShell CSV export | Records returned by the executed query | Complete historical authentication activity outside the accessible log/window |

## 3. Correlation guidance

- Align timestamps and time zones before comparing sources.
- Confirm that hostnames and IP addresses refer to the same lab systems.
- Compare the Nmap scan time with packet-capture timestamps.
- Compare PowerShell CSV rows with the corresponding Event Viewer records.
- Record discrepancies instead of silently choosing one source.
- Treat missing telemetry as a visibility limitation, not proof that an event did not occur.

## 4. Finding structure

Use this format for any finding that is supported by the evidence:

| Field | Required content |
|---|---|
| Finding title | Neutral description of the observed condition |
| Severity | Only when a defined rubric and sufficient evidence support it |
| Affected asset | Verified lab host or system |
| Observation | What the artifact directly shows |
| Evidence reference | Exact filename and packet/event/line reference |
| Analysis | Why the observation matters |
| Confidence | High / Medium / Low with a brief rationale |
| Limitation | What is not known or not visible |
| Recommended validation | Next authorized check |

If the evidence does not support a security finding, record a technical observation instead of forcing a severity rating.

## 5. Quality-control review

Before submission, verify:
- Every claim maps to an actual artifact.
- Commands and filters are reproduced accurately.
- Capture filters and display filters are not confused.
- Nmap port states are interpreted correctly.
- Windows event channel and Event ID are both identified.
- Event 4697 (Security) and 7045 (System) are distinguished.
- Event 4625 results are validated against the selected time window.
- Sensitive values are redacted from public screenshots.
- Limitations and alternative explanations are documented.
- No fabricated output, counts, addresses, versions or conclusions appear.

## 6. Reporting principle

A strong technical report is not a collection of commands or screenshots. It explains the question, method, evidence, interpretation and limits in a way another reviewer can reproduce. Keep the original artifacts available so that every important conclusion can be independently checked.
