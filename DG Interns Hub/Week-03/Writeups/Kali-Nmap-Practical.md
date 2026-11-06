# Network Reconnaissance with Nmap

**Platform:** Kali Linux VM  
**Tool:** Nmap 7.95  
**Scope:** Authorized lab systems only

## Objective
Use Nmap to identify exposed services and versions, and examine TCP SYN scan behavior in a controlled virtual lab.

## Network and tool verification
```bash
ip -br addr
ip route
nmap --version
```

Confirm that the Kali interface has the expected lab address and that a valid route exists before initiating a scan.

## Service and version detection
```bash
nmap -sV -sC <authorized-lab-target> -oN service-detection.txt
```

- `-sV` probes open ports to identify service and version information.
- `-sC` runs Nmap's default script set.
- `-oN` writes the results in normal human-readable format.

## TCP SYN scan
```bash
sudo nmap -sS -p 1-1000 <authorized-lab-target> -oN syn-scan.txt
```

- `-sS` performs a TCP SYN scan and generally requires elevated privileges.
- `-p 1-1000` limits the scan to the selected TCP port range.

## SOC relevance
Unexpected exposed services may increase an environment's attack surface. Scan activity should be assessed using source and destination addresses, timestamps, port distribution, authorization context and corroborating network or endpoint telemetry. A scan result does not, by itself, establish that a host is compromised.

## Evidence
Retain the actual target details, commands and Nmap output from the authorized lab in `Findings/Kali/Nmap/`. Include the network-interface and route verification that corresponds to the successful test session.
