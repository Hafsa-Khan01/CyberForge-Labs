# Network Intrusion Detection with Snort

**Platform:** Ubuntu VM  
**Tool:** Snort IDS  
**Configuration:** Snort main configuration and local rules

## Objective
Configure Snort to inspect controlled lab traffic and generate alerts for selected ICMP, SSH, HTTP and scan-like TCP SYN activity.

## Network configuration
Identify the active interface and its address before starting the sensor:

```bash
ip -br addr
ip route
```

Set `HOME_NET` to the protected lab subnet in the Snort configuration. Define `EXTERNAL_NET` relative to the lab topology, and select the interface that carries the test traffic.

## Local detection rules
The accompanying file `Snort-Rules/local-week3.rules` contains four local rules:

| SID | Detection purpose |
|---|---|
| 1000001 | ICMP traffic directed to HOME_NET |
| 1000002 | TCP traffic to destination port 22 |
| 1000003 | TCP traffic to destination port 80 |
| 1000004 | Thresholded TCP SYN activity as a possible service-discovery indicator |

## Configuration validation and monitoring
```bash
sudo snort -T -i <interface> -c /etc/snort/snort.conf
sudo snort -A console -q -c /etc/snort/snort.conf -i <interface>
```

Use the interface and configuration path present on the installed system. Generate test traffic only between authorized lab hosts.

## Rule interpretation
The SYN rule uses the `flags:S` option to match TCP SYN packets and a source-based threshold to reduce repetitive alerts. This pattern may indicate port-scanning activity, but it is not unique to Nmap. Ordinary connection attempts and other tools can also produce SYN packets.

A reliable assessment should consider destination-port diversity, packet timing, source identity, network context and corroborating endpoint telemetry.

## MITRE ATT&CK context
T1046 — Network Service Discovery describes activity intended to identify services running on remote systems. The SYN threshold rule is a heuristic detection aid for possible T1046 behavior; an alert alone does not establish tool identity, intent or compromise.

## Evidence
Keep the original configuration, successful validation output and console alert captures in `Findings/Ubuntu/Snort/`. Preserve the alert message and timestamp in the evidence.
