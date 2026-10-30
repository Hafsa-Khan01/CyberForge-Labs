# Practical Investigation — Wireshark Packet Capture and Analysis

## 1. Objective

Capture permitted traffic in the assigned virtual lab and inspect DNS, ICMP, TCP and HTTP protocol behaviour. The analysis must be based on packets present in the saved capture.

## 2. Scope and preparation

- Use only the assigned Kali and Ubuntu lab VMs.
- Confirm that both systems are connected to the intended lab network.
- Record the capture host, interface, lab endpoints and capture time.
- Avoid capturing unrelated user or third-party traffic.
- If HTTP is not available in the lab, do not claim an HTTP exchange was observed.

## 3. Capture procedure

1. Open Wireshark and select the interface connected to the lab network.
2. Start the capture before generating test traffic.
3. Generate only the permitted test traffic described by the lab, such as a DNS lookup, ICMP reachability check or HTTP request to the assigned host.
4. Stop the capture after the test window.
5. Save the original file in PCAPNG or PCAP format.
6. Preserve the original capture before applying display filters or creating annotated copies.

## 4. Display-filter reference

| Investigation focus | Wireshark display filter |
|---|---|
| DNS | `dns` |
| ICMP | `icmp` |
| TCP | `tcp` |
| HTTP | `http` |
| TLS | `tls` |
| ARP | `arp` |
| Initial TCP SYN | `tcp.flags.syn == 1 && tcp.flags.ack == 0` |
| TCP reset | `tcp.flags.reset == 1` |

These are display filters applied to packets already captured. Capture filters use a different syntax and restrict which packets are recorded in the first place.

## 5. Analysis methodology

### DNS

Identify the query name, query type, response code and corresponding response where present. Note the client and resolver addresses. A query without a visible response may reflect capture timing, packet loss, filtering or resolver behaviour.

### ICMP

Identify echo requests and replies, their source/destination addresses and timing. Distinguish an unanswered request from a confirmed connectivity failure; the capture may not include the full path or relevant response.

### TCP

For an established connection, locate the SYN, SYN/ACK and ACK sequence. Record the endpoints, ports, timestamps and any retransmissions or resets that are actually visible. A SYN without a response does not establish why the connection did not complete.

### HTTP and TLS

For visible HTTP, inspect the request method, host/path and response status where present. TLS generally protects application payloads; do not claim to have inspected encrypted application content from metadata alone.

## 6. Observation worksheet

| Field | Record from the capture |
|---|---|
| Capture filename | Actual PCAP/PCAPNG filename |
| Interface | Actual selected interface |
| Capture window | Actual start and stop times |
| Lab endpoints | Addresses present in the capture |
| Display filters | Exact filters applied |
| Protocol exchanges | DNS / ICMP / TCP / HTTP observations actually present |
| Notable packet details | Packet numbers, flags, ports and timestamps |
| Limitations | Encryption, packet loss, capture point or interface selection |

## 7. Evidence and validation

Retain the original PCAP/PCAPNG file and screenshots that show the relevant packet list and selected packet details. Ensure screenshots correspond to the saved capture. Record packet numbers and filters so another reviewer can locate the observation.

## 8. Conclusion

Explain which protocol exchanges were confirmed, what the packet fields demonstrate and what remains uncertain. Do not infer malicious intent from an isolated packet or claim that a protocol exchange occurred unless it is visible in the original capture.
