# Alternative SIEM Labs (Room-Free Track)

## Why this section exists
The assigned TryHackMe rooms, **Introduction to SIEM** and **Splunk: Exploring SPL**, required premium access in the learner's environment. They are therefore recorded as **not attempted due to access restriction**, not as completed rooms.

To preserve the learning objectives without claiming platform completion, this folder provides self-contained alternatives that can be performed with a local Splunk/Wazuh lab and public product documentation.

## Learning outcomes covered
| Assigned room objective | Alternative activity |
|---|---|
| Understand SIEM purpose and workflow | [SIEM fundamentals lab](01-SIEM-Fundamentals-Lab.md) |
| Understand event fields and ingestion | [Log ingestion and data validation](02-Log-Ingestion-and-Validation.md) |
| Search events with SPL | [SPL hands-on exercises](03-SPL-Hands-On-Lab.md) |
| Build detections and tune alerts | [Detection and alert exercises](04-Detection-and-Alert-Lab.md) |
| Investigate alerts | [SOC triage exercises](05-SOC-Triage-Lab.md) |

## Completion and evidence policy
- These are alternative exercises, not TryHackMe room completions.
- Run commands only in systems you own or are explicitly authorised to test.
- Replace example hostnames, index names and field names with values from the actual lab.
- Capture screenshots or exports from the real environment and place them in `../Findings/Evidence/`.
- Never add passwords, API keys, private keys, tokens or unredacted sensitive logs to GitHub.
- Mark an exercise complete only after running it and retaining evidence.

## Suggested evidence
1. Splunk search showing events in the `lab` index.
2. One successful SPL aggregation and one time-series search.
3. Wazuh agent/manager status and an actual alert.
4. Wazuh custom rule test output from `wazuh-logtest`.
5. Screenshots of scheduled alert configuration and dashboard panels.
6. Three case notes based on actual alert records.

## Status
Alternative learning material is documented here. The premium TryHackMe rooms are not claimed as completed.
