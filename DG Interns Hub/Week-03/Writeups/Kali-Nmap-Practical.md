# Practical Write-up — Kali Linux and Nmap

**Platform:** Kali Linux VM  
**Tool:** Nmap 7.95  
**Status:** User reports the Kali practical and controlled lab testing were completed.

## Objective
Use Nmap to enumerate services and perform a controlled SYN scan against an authorized lab target.

## Environment checks
```bash
ip -br addr
ip route
nmap --version
```

The initial environment check showed Nmap 7.95 installed. The first network snapshot showed `eth0` UP but without an IPv4 address and no default route; VirtualBox networking was then being corrected. Use the final successful network output and actual target address from the saved evidence in the submission.

## Scan examples
```bash
nmap -sV -sC <authorized-lab-target> -oN service-detection.txt
sudo nmap -sS -p 1-1000 <authorized-lab-target> -oN syn-scan.txt
```

- `-sV`: probe open ports to identify service/version information.
- `-sC`: run Nmap's default script set.
- `-sS`: TCP SYN scan; requires appropriate privileges.
- `-p 1-1000`: limit the scan to the selected TCP port range.
- `-oN`: save human-readable output.

## SOC relevance
Unexpected exposed services can increase attack surface. A scan should be assessed using source and destination addresses, timing, port distribution, authorization context and corroborating network/endpoint logs. A scan result alone does not establish compromise.

## Evidence
Place original Kali screenshots and the saved Nmap text outputs in `Findings/Kali/Nmap/`. Include the exact target, date/time, command and result from the original lab output. Do not substitute an Internet host or a third-party screenshot for lab evidence.
