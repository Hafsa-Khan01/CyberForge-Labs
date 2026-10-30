# Week 02 | Network Traffic Analysis, Nmap & Windows Telemetry

## 1. TCP Connection State and Flags

A typical TCP three-way handshake is:

```text
Client                         Server
  | -------- SYN ------------> |
  | <------ SYN, ACK ---------- |
  | -------- ACK ------------> |
```

Connection termination commonly uses FIN exchanges to close each direction independently. RST aborts or rejects a connection.

| Flag | Operational meaning | Investigation relevance |
|---|---|---|
| SYN | Initiates synchronization of sequence numbers. | Initial connection attempts and scan patterns |
| ACK | Acknowledges received sequence space. | Connection progression and acknowledgement behaviour |
| FIN | Sender has no more data to transmit. | Graceful connection teardown |
| RST | Resets a connection. | Refused, aborted or unexpected connection attempts |
| PSH | Requests prompt delivery of buffered data. | Packet interpretation; not an application-level verdict |
| URG | Marks urgent pointer significance. | Rare in modern traffic; interpret in context |

A SYN packet alone is not evidence of malicious activity. Interpret packet direction, sequence, response and surrounding traffic.

## 2. Protocol Analysis Reference

| Protocol | Function | Useful investigation context |
|---|---|---|
| DNS | Name and service-record resolution | Query patterns, response codes, unusual domains and unexpected resolvers |
| HTTP | Application-layer web communication | Methods, hosts, paths, status codes and plaintext content where visible |
| TLS | Cryptographic protection for application traffic | Handshake metadata, certificate details and negotiated parameters |
| ARP | IPv4 address-to-link-layer resolution on a local segment | Conflicting mappings and unexpected address changes |
| ICMP | Network diagnostics and error reporting | Echo patterns, unreachable messages and unusual volume |
| SMB | File and printer sharing | Authentication patterns, share access and unexpected lateral access |

TLS-encrypted payloads are generally not readable from a passive capture without appropriate decryption material. Do not infer encrypted application content from metadata alone.

## 3. Wireshark: Capture Filters vs Display Filters

Capture filters use the capture-filter syntax and limit what is recorded. Display filters use Wireshark's display-filter syntax and select packets from an existing capture. The syntaxes are not interchangeable.

### Common display filters

| Purpose | Display filter |
|---|---|
| TCP traffic | `tcp` |
| UDP traffic | `udp` |
| DNS traffic | `dns` |
| HTTP traffic | `http` |
| TLS traffic | `tls` |
| ARP traffic | `arp` |
| ICMP traffic | `icmp` |
| Specific IP address | `ip.addr == 192.0.2.10` |
| TCP port 80 | `tcp.port == 80` |
| Initial SYN packets | `tcp.flags.syn == 1 && tcp.flags.ack == 0` |
| TCP resets | `tcp.flags.reset == 1` |

The address `192.0.2.10` is reserved for documentation examples. Replace it with an address observed in the authorized lab capture.

## 4. Nmap: Discovery and Scan Interpretation

| Option | Function | Operational note |
|---|---|---|
| `-sn` | Host discovery without a port scan | Discovery methods depend on privileges and network conditions. |
| `-sS` | TCP SYN scan | Requires suitable privileges; commonly called a half-open scan. |
| `-sT` | TCP connect scan | Uses the operating system's connect call. |
| `-sU` | UDP scan | Can be slow and may produce open/filtered results. |
| `-sV` | Service/version detection | Sends probes to identify services; results are estimates. |
| `-O` | OS detection | Accuracy depends on response quality and scan conditions. |
| `-A` | Enables several advanced detection features | Broad option; use only when explicitly authorized. |

### Evidence preservation

- `-oN <file>`: normal human-readable output.
- `-oX <file>`: XML output suitable for structured processing.

Record the exact command, target scope, timestamp, Nmap version and output filename. An open port indicates a reachable listener at the time of testing; it does not independently establish a vulnerability.

## 5. Windows Security Telemetry

Windows Event Viewer separates records into channels such as Application, Security and System. Event interpretation should include provider, channel, Event ID, timestamp, host, account, source address (when present), logon type and surrounding events.

### Selected Windows Event IDs

| Event ID | Channel / source context | Description |
|---:|---|---|
| 4624 | Security | Successful logon |
| 4625 | Security | Failed logon |
| 4634 | Security | Logoff |
| 4648 | Security | Logon attempted using explicit credentials |
| 4672 | Security | Special privileges assigned to a new logon |
| 4688 | Security | Process creation |
| 4697 | Security | Service installed |
| 4720 | Security | User account created |
| 4722 | Security | User account enabled |
| 4724 | Security | Attempt to reset an account password |
| 4732 | Security | Member added to a security-enabled local group |
| 4768 | Security | Kerberos authentication ticket (TGT) requested |
| 4769 | Security | Kerberos service ticket requested |
| 4776 | Security | NTLM credential validation |
| 1102 | Security | Audit log cleared |

System event **7045** is also associated with service installation. It is not the same event as Security event **4697**. Availability and field details depend on audit policy and Windows configuration.

### Logon type reference

| Type | Description |
|---:|---|
| 2 | Interactive |
| 3 | Network |
| 4 | Batch |
| 5 | Service |
| 7 | Unlock |
| 10 | RemoteInteractive |
| 11 | CachedInteractive |

Validate the event's XML or rendered details before relying on a field. A logon type or single Event ID is not, by itself, proof of compromise.

## 6. SOC Baseline and Triage

A useful baseline describes expected identities, endpoints, services, network flows, authentication patterns and administrative activity. Triage deviations by asking:

1. Is the event expected for this host, account and time window?
2. Is the source system or address known and authorized?
3. Are related events present before or after the alert?
4. Is there corroborating endpoint, network or identity telemetry?
5. What is confirmed, what is inferred and what remains unknown?

Document the evidence and escalate according to the organization's incident-handling procedure. Avoid assigning a malicious verdict solely from an isolated event.
