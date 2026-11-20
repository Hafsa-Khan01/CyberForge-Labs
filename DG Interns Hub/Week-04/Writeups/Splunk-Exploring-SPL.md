# TryHackMe — Splunk: Exploring SPL

**Assigned room:** https://tryhackme.com/room/splunkexploringspl  
**Access status:** Premium access required in the learner's account; room not attempted.  
**Completion claim:** Not completed. No room badge or completion screenshot is claimed.

## Learning objective
Understand how SPL filters, transforms, aggregates and presents security events for investigation.

## Alternative learning activity
A self-contained set of SPL exercises is provided in [Alternative Lab 03 — SPL Hands-On Lab](../Alternative-Labs/03-SPL-Hands-On-Lab.md). It includes:
- event inventory and data validation;
- failed and successful Windows logon searches;
- PowerShell and new-account activity;
- SSH authentication failures;
- time-series analysis and process/network pivots;
- SPL command reference and exercise recording guidance.

[Alternative Lab 04 — Detection and Alert Lab](../Alternative-Labs/04-Detection-and-Alert-Lab.md) extends the searches into detection logic, thresholds, alert scheduling and validation.

## SPL pipeline reminder
SPL commands are chained with the pipe character. A search should begin by narrowing the dataset, then extract or transform fields, aggregate where appropriate and present a focused result. Always validate field names against the raw event before using a query in production.

## Reflection
A query returning zero results does not necessarily mean the activity did not occur. The index, time range, sourcetype, field extraction and source coverage must be checked first. Thresholds also require tuning against normal activity.

## Evidence
Add genuine screenshots of executed searches and their actual result counts under the Week 04 evidence folder. The queries in the alternative lab are starting examples, not claimed room answers or proof of execution.
