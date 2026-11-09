# Week 04 — SIEM in Practice: Notes

This folder contains the eight theoretical question-and-answer documents for Week 04. Each assignment question is maintained in a separate file.

## Contents

| # | Topic | File |
|---:|---|---|
| 1 | What is a SIEM? Components, data flow and SIEM vs. log management vs. SOAR vs. EDR | [01-What-is-a-SIEM.md](01-What-is-a-SIEM.md) |
| 2 | Log ingestion methods; Splunk Universal Forwarder vs. Wazuh agent | [02-Log-Ingestion-Methods-and-Agents.md](02-Log-Ingestion-Methods-and-Agents.md) |
| 3 | SPL basics: search, where, stats, table, eval, timechart and rex | [03-SPL-Basics.md](03-SPL-Basics.md) |
| 4 | Wazuh architecture, decoders, rules and rule levels 0–15 | [04-Wazuh-Architecture-Decoders-and-Rules.md](04-Wazuh-Architecture-Decoders-and-Rules.md) |
| 5 | True/false positives and negatives, alert fatigue and tuning | [05-Detection-Accuracy-and-Alert-Tuning.md](05-Detection-Accuracy-and-Alert-Tuning.md) |
| 6 | TTP-to-detection logic for SSH and Windows brute force; MITRE ATT&CK T1110 | [06-TTP-to-Detection-Brute-Force.md](06-TTP-to-Detection-Brute-Force.md) |
| 7 | Correlation rules, thresholds, baselines and allowlists | [07-Correlation-Thresholds-Baselines-Allowlists.md](07-Correlation-Thresholds-Baselines-Allowlists.md) |
| 8 | SOC tiers, alert lifecycle and the five triage questions | [08-SOC-Tiers-and-Alert-Lifecycle.md](08-SOC-Tiers-and-Alert-Lifecycle.md) |

## Documentation standard

- Explanations are written for SOC monitoring and L1 investigation context.
- SPL examples assume an index named `lab`; actual field names and sourcetypes must be verified against ingested events.
- Thresholds in examples are lab starting points, not universal production recommendations.
- Illustrative examples are not evidence that a lab installation or detection has already been completed.
- Practical execution results and screenshots will be documented separately under the Week 04 Findings, Detections and Writeups folders.
