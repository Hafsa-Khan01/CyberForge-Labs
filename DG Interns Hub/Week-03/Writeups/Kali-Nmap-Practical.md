# Network Reconnaissance and Service Identification with Nmap

**Platform:** Kali Linux VM  
**Tool:** Nmap 7.95  
**Scope:** Authorized lab systems only

## Objective
Verify the Kali network path and use Nmap to identify exposed services and versions on an explicitly authorized lab target.

## Network and tool verification
```bash
ip -br addr
ip route
nmap --version
```

Confirm the active interface, assigned address and route before initiating a scan. Record the target and test window so that scan activity can be correlated with network sensor output.

## Service and version detection
```bash
nmap -sV -sC <authorized-lab-target> -oN service-detection.txt
```

- `-sV` probes discovered open ports to identify service/version information.
- `-sC` runs Nmap's default script set; review script behavior and scope before use.
- `-oN` saves results in normal human-readable format.

## TCP SYN scan
```bash
sudo nmap -sS -p 1-1000 <authorized-lab-target> -oN syn-scan.txt
```

- `-sS` performs a TCP SYN scan and generally requires elevated privileges.
- `-p 1-1000` restricts the scan to the selected TCP port range.

## SOC investigation relevance
Unexpected exposed services may increase attack surface, but service discovery is not evidence of compromise. Assess scan activity using source and destination addresses, timestamps, port distribution, authorization context and corroborating network or endpoint telemetry. Compare the scan window with Snort alerts where sensor visibility permits.

## Evidence
Original screenshots are stored in [Evidence](../Evidence/):

- [07 — Kali network connectivity verification](../Evidence/07-Kali-Network-Connectivity-Verification.jpeg)
- [08 — Nmap service/version scan output](../Evidence/08-Kali-Nmap-Service-Version-Scan.jfif)

Use the captured output as the source for any target-specific result. The command examples above are reproducible reference commands and should not be treated as additional scan results.