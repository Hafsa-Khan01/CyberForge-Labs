# Week 3 — Linux Logs, Sysmon, auditd & Snort

**Programme:** DG Interns Hub — 15 October 2026 Batch  
**Intern:** Hafsa Khan  
**Intern ID:** DG/15/OCT/CYBER/035  
**Deadline:** 6 November 2026, 11:59 PM

## Goal
Build an understanding of endpoint telemetry and network intrusion detection by studying EDR, Sysmon, Linux auditd, Snort, MITRE ATT&CK T1046, and SIEM log ingestion.

## Environment status
| System | Availability | Planned use |
|---|---|---|
| Windows VM | Available | Sysmon installation and event generation |
| Ubuntu VM | Available | auditd and Snort installation, configuration, and testing |
| Kali VM | Available | Authorized traffic generation and Nmap testing |

All three required virtual machines are available. Practical tasks will be performed on their assigned systems; Kali will be used as the traffic-generation/test machine where appropriate.

## Repository structure
- `Notes/` — ten separate theory question-and-answer files.
- `Writeups/TryHackMe/` — separate writeups for each assigned room actually completed.
- `Writeups/LetsDefend/` — separate writeups for each assigned lesson actually completed.
- `Findings/` — genuine screenshots and notes from Sysmon, auditd, and Snort practicals.
- `Cheat-Sheet/` — event IDs, audit event types, and Snort rule examples.
- `Snort-Rules/` — local starter and T1046 detection rules, tested status recorded.
- `Reports/` — final PDF and presentation when evidence is ready.

## Theory progress
All ten question files are prepared in `Notes/`. Review them in your own words and add personal examples where appropriate.

## Practical evidence checklist
- [ ] Install Sysmon on Windows and verify the Operational channel.
- [ ] Generate and inspect Sysmon Event IDs 1, 3, and 11.
- [ ] Install/configure auditd on Ubuntu and capture verified audit records.
- [ ] Install Snort on Ubuntu, configure HOME_NET/EXTERNAL_NET, and validate rules.
- [ ] Use Kali for authorized test traffic; verify starter alerts and the SYN-scan detection rule.
- [ ] Complete assigned TryHackMe rooms and LetsDefend lessons; write up only completed work.
- [ ] Build the 15+ entry cheat sheet.
- [ ] Prepare PDF, presentation, LinkedIn posts, and final shared folder.

## Evidence integrity
Do not invent event timestamps, IP addresses, command output, alerts, room completion, or screenshots. Record failures and environment limitations accurately. Do not expose credentials, tokens, or private data in screenshots.

## Scope
This Week 3 work is confined to this directory. Other repository projects and the NetworkWalks directory are out of scope.
