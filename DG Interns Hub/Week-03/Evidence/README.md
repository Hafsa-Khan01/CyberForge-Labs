# Week 3 — Practical Evidence

This folder contains the original screenshots retained for Week 3 practical work. Filenames identify visible activity; they do not imply that every required task was successfully completed.

## Evidence index

| File | Evidence |
|---|---|
| `01-Windows-Sysmon-Installation-and-Configuration.jpeg` | Windows Sysmon Installation and Configuration |
| `02-Sysmon-Event-ID-1-Process-Creation-and-DNS-Events.jpeg` | Sysmon Event ID 1 Process Creation and DNS Events |
| `03-Sysmon-Event-ID-1-and-22-Event-Details.jpeg` | Sysmon Event ID 1 and 22 Event Details |
| `04-Sysmon-Event-ID-11-File-Creation.jpeg` | Sysmon Event ID 11 File Creation |
| `05-Sysmon-Event-ID-13-Registry-Value-Set.jpeg` | Sysmon Event ID 13 Registry Value Set |
| `06-Sysmon-Service-and-Configuration-Verification.jpeg` | Sysmon Service and Configuration Verification |
| `07-Kali-Network-Connectivity-Verification.jpeg` | Kali Network Connectivity Verification |
| `08-Kali-Nmap-Service-Version-Scan.jfif` | Kali Nmap Service Version Scan |
| `09-Linux-strace-System-Call-Output.png` | Linux strace system-call output (not Snort evidence) |
| `10-Snort-Local-Rules-Configuration.png` | Snort Local Rules Configuration |
| `11-Snort-TCP-Port-Scan-Detection-Alerts.png` | Snort TCP Port Scan Detection Alerts |
| `12-Ubuntu-auditd-Service-Unit-Status.png` | Ubuntu auditd service-unit status (not Snort evidence) |
| `13-Ubuntu-auditd-Package-Installation-Output.jpeg` | Ubuntu auditd Package Installation Output |

## Review notes

- Windows Sysmon screenshots show service/configuration activity and selected event records, including Event IDs 1, 11, 13 and 22.
- Kali screenshots show network connectivity checks and an Nmap service/version scan.
- Snort evidence includes local-rule configuration and TCP port-scan alert output. The former `09` screenshot is Linux strace output, and the former `12` screenshot is an auditd service-unit listing; neither proves Snort initialization or a Snort rule test.
- Ubuntu evidence includes an auditd package-installation output and a service-unit listing that reports `auditd.service` as not found. These do not prove a running auditd service, configured audit rules, or successful `ausearch` verification. Capture fresh service, rule, and event output before marking that practical complete.
- Duplicate copies, blank/irrelevant images, unrelated boot-error output, and screenshots from unrelated/older Event Viewer environments were excluded.

Only the files listed above are retained here. Original screenshot bytes were preserved; filenames were made descriptive.