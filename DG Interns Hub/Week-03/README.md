# Week 3 — Linux Logs, Sysmon, auditd & Snort

**Programme:** DG Interns Hub — 15 October 2026 Batch  
**Intern:** Hafsa Khan  
**Deadline:** 6 November 2026, 11:59 PM

## Goal
Understand endpoint telemetry, Windows Sysmon, Linux auditd, Snort IDS, MITRE ATT&CK T1046 and SIEM log ingestion.

## Lab environment
| System | Role | Tooling |
|---|---|---|
| Windows VM | Endpoint telemetry | Sysmon 15.22, Event Viewer / PowerShell |
| Ubuntu VM | Linux auditing and IDS | auditd, Snort |
| Kali VM | Authorized test traffic | Nmap 7.95 |

The intern reports that the Windows, Ubuntu and Kali practicals are complete and screenshots have been saved. Original VM screenshots and raw outputs remain the authoritative evidence.

## Repository contents
- `Notes/` — ten theory question-and-answer files.
- `Writeups/Windows-Sysmon-Practical.md` — Windows practical and observed event IDs 1, 3, 11, 13 and 22.
- `Writeups/Ubuntu-auditd-Practical.md` — Linux auditd practical.
- `Writeups/Ubuntu-Snort-Practical.md` — Snort IDS setup and rule interpretation.
- `Writeups/Kali-Nmap-Practical.md` — authorized Nmap practical.
- `Findings/` — upload original screenshots and raw command/alert outputs.
- `Cheat-Sheet/` — endpoint and network detection quick reference.
- `Snort-Rules/` — local starter rules and possible T1046 SYN-scan indicator.
- `Reports/` — final report and presentation outline.

## Completion checklist
- [x] Ten theory notes prepared.
- [x] Windows Sysmon practical reported complete.
- [x] Ubuntu auditd practical reported complete.
- [x] Ubuntu Snort practical reported complete.
- [x] Kali Nmap practical reported complete.
- [x] Practical screenshots saved locally by the intern.
- [x] Cheat sheet and Snort rules prepared.
- [x] Final report draft and presentation outline prepared.
- [ ] Upload genuine screenshots and raw outputs into `Findings/`.
- [ ] Add TryHackMe/LetsDefend write-ups only for rooms/lessons actually completed.
- [ ] Export final PDF and presentation after inserting verified evidence.
- [ ] Submit using the official DG Interns Hub submission channel.

## Evidence integrity
Do not invent timestamps, IP addresses, command output, alerts, room completion or screenshots. Record limitations accurately. Do not expose credentials, tokens or private data. Conceptual images are illustrations, not practical evidence.

## Scope
This Week 3 work is confined to this directory. Other repository projects and the NetworkWalks directory are out of scope.
