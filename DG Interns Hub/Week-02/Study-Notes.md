# Week 2 — Study Notes

## TCP Connection Lifecycle
A typical TCP connection starts with SYN → SYN/ACK → ACK. Normal teardown commonly uses FIN/ACK exchanges; RST aborts a connection. Important flags:
- SYN: synchronize sequence numbers / initiate connection.
- ACK: acknowledge received data.
- FIN: close one direction of a connection.
- RST: reset a connection.
- PSH: request prompt delivery to the receiving application.
- URG: indicates urgent data pointer significance.

## Common Protocol Behaviour
- **DNS:** name resolution; investigate unusual query volume, unexpected domains and suspicious record responses.
- **HTTP:** web requests and responses, commonly visible in plaintext when not protected by TLS.
- **HTTPS/TLS:** encrypts application traffic; metadata may remain observable.
- **ARP:** maps IPv4 addresses to link-layer addresses on a local segment; unexpected conflicting mappings may indicate spoofing.
- **ICMP:** diagnostics and error reporting; unexpected patterns can be useful indicators.
- **SMB:** file and printer sharing; exposed shares and unusual authentication/access patterns merit review.

## Wireshark Filters
Capture filters are applied before packets are recorded; display filters are applied to packets already captured. Examples:
- `tcp`
- `udp`
- `dns`
- `http`
- `tls`
- `arp`
- `icmp`
- `ip.addr == 192.0.2.10` (documentation-only example address)
- `tcp.port == 80`
- `tcp.flags.syn == 1 && tcp.flags.ack == 0`

Replace example addresses with the actual lab address when investigating.

## Nmap Scan Options
- `-sn`: host discovery without a port scan.
- `-sS`: TCP SYN scan (requires suitable privileges).
- `-sT`: TCP connect scan.
- `-sU`: UDP scan.
- `-sV`: service/version detection.
- `-O`: OS detection.
- `-A`: enables several advanced detection features; use only where authorized.
Save normal and XML output with `-oN` and `-oX`. Record exact command, target, timestamp and output. Scan only authorized lab hosts.

## Windows Administration and Logging
Review processes, services, registry, local users/groups, UAC and Event Viewer (Application, Security and System logs).

### Useful Windows Event IDs
| Event ID | Meaning |
|---:|---|
| 4624 | Successful logon |
| 4625 | Failed logon |
| 4634 | Logoff |
| 4648 | Logon using explicit credentials |
| 4672 | Special privileges assigned to new logon |
| 4688 | Process creation |
| 4697 | Service installed (Security log) |
| 4720 | User account created |
| 4722 | User account enabled |
| 4724 | Attempt to reset an account password |
| 4732 | Member added to a security-enabled local group |
| 4768 | Kerberos authentication ticket (TGT) requested |
| 4769 | Kerberos service ticket requested |
| 4776 | NTLM credential validation |
| 1102 | Audit log cleared |

System event 7045 is also commonly associated with service installation. It is distinct from Security event 4697.

### Logon Types
- 2: interactive
- 3: network
- 4: batch
- 5: service
- 7: unlock
- 10: remote interactive
- 11: cached interactive

Interpret events in context: account, source address, host, time, logon type and surrounding activity. A single event is not proof of compromise.

## SOC Baseline
Establish expected users, hosts, services, network flows, login patterns and administrative activity. Investigate deviations using corroborating evidence and documented escalation procedures.
