# Week 2 — Wireshark Filter Cheat Sheet

These are **display filters** unless marked as capture filters. Replace documentation/example addresses with the actual authorized lab endpoints.

| Filter | What it shows / when to use |
|---|---|
| `tcp` | All TCP packets |
| `udp` | All UDP packets |
| `dns` | DNS traffic |
| `http` | HTTP traffic |
| `tls` | TLS records |
| `arp` | ARP packets |
| `icmp` | ICMP packets |
| `ip.addr == 192.0.2.10` | Packets to or from example host |
| `ip.src == 192.0.2.10` | Packets from example source |
| `ip.dst == 192.0.2.10` | Packets to example destination |
| `tcp.port == 80` | TCP port 80 |
| `tcp.port == 443` | TCP port 443 |
| `udp.port == 53` | UDP DNS |
| `dns.qry.name contains "example"` | DNS queries containing text |
| `tcp.flags.syn == 1` | TCP SYN flag set |
| `tcp.flags.ack == 1` | TCP ACK flag set |
| `tcp.flags.syn == 1 && tcp.flags.ack == 0` | Initial SYN packets |
| `tcp.flags.reset == 1` | TCP reset packets |
| `tcp.analysis.retransmission` | Packets marked as retransmissions |
| `http.request` | HTTP requests |

## Capture Filter Examples
Capture filters use BPF syntax, not display-filter syntax:
- `tcp port 80`
- `udp port 53`
- `host 192.0.2.10`
- `icmp`
- `tcp and port 443`

## Workflow
Choose the correct interface, start capture, generate known lab traffic, stop capture, save PCAPNG, then apply display filters to analyse it. A filter showing no packets does not prove the traffic never occurred; verify interface, capture scope and time window.
