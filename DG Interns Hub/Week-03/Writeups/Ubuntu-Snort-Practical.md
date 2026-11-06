# Practical Write-up — Snort IDS on Ubuntu

**Platform:** Ubuntu VM  
**Tool:** Snort IDS  
**Status:** User reports the installation, rule setup and testing were completed. Keep original terminal output and screenshots as the authoritative evidence.

## Objective
Configure a network IDS to observe controlled lab traffic and generate alerts for selected ICMP, SSH, HTTP and possible SYN-scan activity.

## Configuration concepts
- `HOME_NET` must represent the actual protected lab subnet.
- `EXTERNAL_NET` should be defined relative to `HOME_NET` according to the lab topology.
- The monitored interface must be the actual Ubuntu interface name, discovered using `ip -br addr`.
- Local rule SIDs should be unique within the local ruleset.

## Local rule set
The companion file `../../Snort-Rules/local-week3.rules` contains local rules:
- SID 1000001 — ICMP traffic to HOME_NET.
- SID 1000002 — TCP traffic to destination port 22.
- SID 1000003 — TCP traffic to destination port 80.
- SID 1000004 — thresholded TCP SYN activity as a possible network service discovery indicator.

## Validation and monitoring commands
```bash
ip -br addr
sudo snort -T -i <interface> -c /etc/snort/snort.conf
sudo snort -A console -q -c /etc/snort/snort.conf -i <interface>
```

Use the interface name and configuration path actually present on the VM. Generate test traffic only between authorized lab systems.

## Rule interpretation
The SYN rule uses `flags:S` to match SYN packets and a source-based threshold to reduce alert volume. It can indicate scan-like behavior, but ordinary connection attempts and other tools can also generate SYN packets. Correlate with destination-port spread, timing, source identity and other telemetry before classifying as reconnaissance or attributing the activity to Nmap.

## MITRE ATT&CK
T1046 — Network Service Discovery describes activity aimed at identifying services running on remote systems. The local SYN threshold rule is a detection hypothesis for possible T1046 behavior, not proof of a particular tool or intent.

## Evidence
Place original screenshots in `Findings/Ubuntu/Snort/`: configuration/HOME_NET, successful syntax test, console alert output and the controlled test context. Include the actual alert text and timestamps in the final report only if visible in the captured evidence.
