# Week 3 Presentation — Linux Logs, Sysmon, auditd and Snort

## Slide 1 — Title
**Linux Logs, Sysmon, auditd and Snort IDS**  
DG Interns Hub | Week 3 | Hafsa Khan

## Slide 2 — Objectives
- Understand endpoint telemetry and EDR.
- Collect Windows telemetry with Sysmon.
- Audit Linux activity with auditd.
- Detect network activity with Snort.
- Map reconnaissance behavior to MITRE ATT&CK T1046.

## Slide 3 — Lab architecture
Windows VM: Sysmon endpoint telemetry  
Ubuntu VM: auditd and Snort sensor  
Kali VM: authorized traffic generation and Nmap  
Add a simple topology diagram and the actual isolated lab network details from the evidence.

## Slide 4 — EDR and endpoint telemetry
Explain process, file, registry, DNS and network telemetry. Contrast endpoint detection/response with signature-focused antivirus.

## Slide 5 — Sysmon practical
Show actual Event Viewer screenshots for Event IDs 1, 3, 11, 13 and 22. Explain one observation per event.

## Slide 6 — Linux auditd
Show actual auditd service status, active rule and correlated ausearch records. Explain SYSCALL, EXECVE, PATH and CWD.

## Slide 7 — Snort IDS
Explain IDS versus IPS and the Snort rule header/options. Show the actual validated local rules and real console alert screenshot.

## Slide 8 — Kali Nmap
Show the actual authorized target, Nmap command, service/version results and SYN scan output. Explain the SOC relevance of exposed services and scan patterns.

## Slide 9 — MITRE ATT&CK T1046
Explain Network Service Discovery. Show the thresholded SYN rule as a heuristic indicator, not proof of Nmap or malicious intent.

## Slide 10 — SIEM correlation
Illustrate: telemetry sources → collection/normalization → correlation/detection → alert triage → investigation/response.

## Slide 11 — Key lessons and limitations
- Configuration determines telemetry coverage.
- Correlate multi-record audit events.
- Threshold tuning affects alert volume.
- A single event is rarely enough to establish maliciousness.
- Preserve evidence and document false-positive considerations.

## Slide 12 — Conclusion
Endpoint, Linux audit and network IDS telemetry provide complementary visibility. Correlation turns individual records into an investigation narrative.
