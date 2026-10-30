# Week 01 | Cybersecurity Foundations & Network Architecture

## 1. Cybersecurity Principles

Cybersecurity is the discipline of protecting information assets, endpoints, applications and networks against unauthorized disclosure, modification, disruption or destruction. Security controls are selected according to the assets being protected, the threats they face and the operational requirements of the environment.

### CIA security objectives

| Objective | Security requirement | Example control |
|---|---|---|
| Confidentiality | Information is accessible only to authorized identities. | Access control, encryption, least privilege |
| Integrity | Data and system state remain accurate and changes are authorized. | Hash verification, change control, file integrity monitoring |
| Availability | Services and information remain accessible when required. | Redundancy, backups, recovery testing, capacity management |

A control may support more than one objective. For example, access control can protect confidentiality and integrity.

## 2. Operational Security Roles

| Role | Primary responsibility | Typical operational output |
|---|---|---|
| SOC Analyst | Monitor security telemetry, validate alerts, triage suspicious activity and escalate incidents. | Alert disposition, investigation notes, escalation record |
| VAPT / Penetration Tester | Assess systems within an approved scope and validate security weaknesses safely. | Technical findings, impact analysis, remediation guidance |
| Incident Responder | Coordinate investigation, containment, eradication, recovery and post-incident review. | Incident timeline, containment actions, recovery record |

These roles may collaborate, but their authority and responsibilities depend on the organization's procedures and Rules of Engagement.

## 3. Network Architecture Models

### OSI reference model

| Layer | Function | Representative protocols / technologies | Security relevance |
|---:|---|---|---|
| 7 — Application | Network services used by applications | HTTP, DNS, SMTP | Application abuse, malicious requests, insecure service configuration |
| 6 — Presentation | Data representation, encoding and cryptographic presentation | TLS-related presentation functions, encoding formats | Cryptographic configuration, unsafe parsing |
| 5 — Session | Establishes and manages communication sessions | Session-control concepts | Session misuse, replay and session-management weaknesses |
| 4 — Transport | End-to-end transport and port addressing | TCP, UDP | Exposed ports, connection abuse, transport-layer filtering |
| 3 — Network | Logical addressing and packet routing | IPv4, IPv6, ICMP | Spoofing, routing and filtering issues |
| 2 — Data Link | Local-segment framing and hardware addressing | Ethernet, ARP | ARP spoofing, unauthorized Layer-2 access |
| 1 — Physical | Transmission of bits over a physical medium | Copper, fibre, radio | Physical tampering and interception |

The TCP/IP model groups networking functions into Application, Transport, Internet and Network Access layers. The models are conceptual references; protocol placement can vary by teaching convention.

## 4. Addressing and Core Network Services

- **IP address:** logical address used to identify an interface for packet delivery across networks.
- **MAC address:** link-layer address used for local-segment frame delivery.
- **DNS:** resolves names and provides other resource records; it is not limited to IPv4 lookups.
- **DHCP:** leases network configuration such as IP address, subnet mask, gateway and DNS resolver.
- **Port:** identifies a transport-layer endpoint associated with an application or service. A port number alone does not prove which software is listening.

### Common service ports

| Port | Common association | Transport / note |
|---:|---|---|
| 21 | FTP control | TCP |
| 22 | SSH | TCP |
| 23 | Telnet | TCP; plaintext protocol |
| 25 | SMTP | TCP |
| 53 | DNS | UDP and TCP |
| 80 | HTTP | TCP |
| 110 | POP3 | TCP |
| 143 | IMAP | TCP |
| 443 | HTTPS | TCP; HTTP/3 commonly uses QUIC over UDP 443 |
| 445 | SMB | TCP |
| 3306 | MySQL | TCP |
| 3389 | RDP | TCP and UDP |

Port assignments are conventional defaults, not guarantees. Services can be configured to use non-standard ports.

## 5. Linux Filesystem and Access Control

| Path | Common purpose |
|---|---|
| `/etc` | System-wide configuration |
| `/var/log` | System and application logs |
| `/home` | Regular users' home directories |
| `/tmp` | Temporary files |
| `/usr` | User-space applications, libraries and shared resources |

Linux permissions define read, write and execute rights for the file owner, group and other users. `chmod` changes permission bits; `chown` changes ownership. Apply least privilege to shared directories and service accounts.

SUID executables run with the effective user ID of the file owner. Unexpected SUID binaries should be inventoried and assessed in context; their presence alone does not establish a vulnerability.

## 6. Security Terminology

| Term | Definition |
|---|---|
| Threat | A circumstance, actor or event capable of causing harm to an asset. |
| Vulnerability | A weakness that could be exploited or otherwise cause an adverse impact. |
| Exploit | A technique or code that takes advantage of a vulnerability. |
| Risk | The potential for loss, commonly assessed using likelihood and impact. |
| Control | A safeguard intended to modify risk or meet a security requirement. |

An exposed service is an observation, not automatically a vulnerability. A defensible finding requires validation, context and impact assessment.

## 7. Virtual Machine Network Modes

| Mode | Connectivity model | Lab consideration |
|---|---|---|
| NAT | Guest initiates outbound connectivity through host translation. | Useful for basic internet access; inbound reachability is restricted unless configured. |
| NAT Network | Guests attached to the same NAT network can communicate, subject to configuration. | Suitable for a contained multi-VM lab. |
| Host-only | Communication is limited to the host-only virtual network. | Useful for isolated host/guest exercises. |
| Bridged | Guest joins the physical LAN as a peer device. | Can expose intentionally vulnerable services to the real network; avoid unless explicitly required and controlled. |

Choose the least-exposed mode that satisfies the exercise. Record the actual adapter configuration and assigned addresses.

## 8. Authorization and Responsible Testing

Before security testing, obtain explicit authorization and establish scope, exclusions, permitted techniques, test windows, points of contact and evidence-handling requirements. Avoid unnecessary access to personal or production data. Preserve relevant evidence and report findings through the approved channel.

For work in Pakistan, consult the current applicable legal text and qualified legal guidance where necessary. This note is an operational reminder, not legal advice. Never scan, access or test systems without permission.
