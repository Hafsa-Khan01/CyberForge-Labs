# Week 1 — Study Notes

## Cybersecurity and the CIA Triad
Cybersecurity protects systems, networks, applications and information from unauthorized access, disruption, alteration and destruction. The CIA triad is:
- **Confidentiality:** only authorized people or systems can access information.
- **Integrity:** information remains accurate and is changed only through authorized actions.
- **Availability:** systems and information remain accessible when needed.

## Security Roles
- **SOC Analyst:** monitors alerts and telemetry, triages suspicious activity, investigates indicators and escalates incidents.
- **VAPT / Penetration Tester:** performs authorized security testing within an agreed scope and documents validated weaknesses and remediation.
- **Incident Responder:** coordinates containment, investigation, eradication, recovery and lessons learned.

## OSI and TCP/IP
| OSI layer | Examples | Security considerations |
|---|---|---|
| 7 Application | HTTP, DNS, SMTP | injection, malicious requests, phishing |
| 6 Presentation | TLS, encoding | weak cryptography, unsafe parsing |
| 5 Session | session management | hijacking, replay |
| 4 Transport | TCP, UDP | port exposure, scanning, SYN abuse |
| 3 Network | IP, ICMP | spoofing, routing attacks |
| 2 Data Link | Ethernet, ARP | ARP spoofing, MAC abuse |
| 1 Physical | cabling, radio | device tampering, interception |

TCP/IP groups these functions into Application, Transport, Internet and Network Access layers.

## Network Fundamentals
- **IP address:** logical address used to route packets.
- **MAC address:** link-layer interface identifier.
- **DNS:** resolves names to records such as IP addresses.
- **DHCP:** leases network configuration to clients.
- **Ports:** identify application endpoints on a host.

| Port | Common service |
|---:|---|
| 21 | FTP control |
| 22 | SSH |
| 23 | Telnet |
| 25 | SMTP |
| 53 | DNS |
| 80 | HTTP |
| 110 | POP3 |
| 143 | IMAP |
| 443 | HTTPS |
| 445 | SMB |
| 3306 | MySQL |
| 3389 | RDP |

## Linux Filesystem and Permissions
- `/etc`: system and service configuration.
- `/var/log`: system and application logs.
- `/home`: users' home directories.
- `/tmp`: temporary files.
- `chmod` changes permission bits; `chown` changes ownership.
- SUID runs an executable with the file owner's effective UID. Unexpected SUID files deserve investigation.

## Threat, Vulnerability, Risk and Exploit
A **threat** may cause harm; a **vulnerability** is a weakness; **risk** combines likelihood and impact; an **exploit** is a method or code that takes advantage of a weakness.

## Virtual Machine Networking
- **NAT:** guest accesses external networks through host translation.
- **NAT Network:** guests on the same NAT network can communicate, subject to configuration.
- **Host-only:** guest communication is limited to the host-only network.
- **Bridged:** guest joins the physical LAN as another device.
Use isolated NAT Network or Host-only for vulnerable practice systems. Bridging can expose intentionally vulnerable services to the real LAN.

## Legal and Ethical Practice
Obtain explicit authorization, define targets and exclusions, agree on time windows and Rules of Engagement, avoid unnecessary data access, preserve evidence, and report findings responsibly. In Pakistan, check the current text and applicability of the Prevention of Electronic Crimes Act (PECA) and obtain qualified legal advice for legal questions. Never test systems without permission.
