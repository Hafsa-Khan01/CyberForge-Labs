# TryHackMe — Introduction to SIEM

**Assigned room:** https://tryhackme.com/room/introtosiem  
**Access status:** Premium access required in the learner's account; room not attempted.  
**Completion claim:** Not completed. No room badge or completion screenshot is claimed.

## Learning objective
Understand how a SIEM collects security telemetry, makes it searchable, correlates events and supports SOC alert triage.

## Alternative learning activity
A self-contained, room-free exercise is provided in [Alternative Lab 01 — SIEM Fundamentals](../Alternative-Labs/01-SIEM-Fundamentals-Lab.md). It covers:
- SIEM purpose and core components;
- event sources, collection and parsing;
- normalisation, indexing and correlation;
- alerts, enrichment and tuning;
- the SOC investigation lifecycle.

The companion [Log Ingestion and Validation lab](../Alternative-Labs/02-Log-Ingestion-and-Validation.md) covers Windows and Linux telemetry paths and data validation.

## Reflection
A SIEM is valuable only when its telemetry is complete, correctly timestamped and searchable. Detection logic must be based on fields that actually exist in the ingested data. An alert is a lead for investigation, not automatic proof of compromise.

## Evidence
Attach screenshots from the actual local Splunk/Wazuh environment to the Week 04 evidence folder. The alternative lab is documented here; local execution should be marked complete only when supported by real evidence.

## Learning outcome mapping
| Room learning objective | Alternative documentation |
|---|---|
| SIEM architecture and purpose | [SIEM fundamentals](../Alternative-Labs/01-SIEM-Fundamentals-Lab.md) |
| Data collection and ingestion | [Log ingestion](../Alternative-Labs/02-Log-Ingestion-and-Validation.md) |
| Alert investigation | [SOC triage](../Alternative-Labs/05-SOC-Triage-Lab.md) |

