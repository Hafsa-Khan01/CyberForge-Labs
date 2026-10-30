# NetworkWalks Week 01 — Practical Evidence & Technical Report

**Prepared by:** Hafsa Khan  
**Programme:** NetworkWalks Cybersecurity Internship  
**Scope:** VirtualBox/Kali setup and Wireshark SOC Labs 03–08  
**Source archive:** Evidence.zip supplied 30 October 2026

## Executive summary

The supplied archive was extracted and its image inventory checked. It contains **46 images**: six Wireshark result cards, one Kali-in-VirtualBox desktop screenshot, seven VirtualBox configuration screenshots, and 32 Wireshark packet-analysis screenshots.

The six result cards show scores of 89%, 90%, 100%, 99%, 100%, and 98%, giving a mean of **96%**. The exercises cover TCP SYN scan recognition, TCP stream reconstruction, HTTP request inspection, FTP authentication-failure analysis, and SIP/RTP VoIP traffic.

These images document practical activity and learner-reported results. They do not prove that every packet-level value was independently recalculated from original PCAPs or that every VM setting and connectivity test succeeded.

## 1. Evidence inventory

| Evidence group | Count | Description |
|---|---:|---|
| Wireshark result cards | 6 | Learner results for Labs 03–08 |
| Kali desktop / VirtualBox | 1 | Kali Linux running in the VM |
| VirtualBox setup archive | 7 | VM, network adapter and shared-folder configuration views |
| Wireshark analysis archive | 32 | Packet lists, packet details and protocol/stream views |
| **Total** | **46** | |

## 2. Wireshark results

| Lab | Practical | Score |
|---|---|---:|
| 03 | Identify the Attacker's IP | 89% |
| 04 | Follow TCP Stream | 90% |
| 05 | Follow TCP Stream — Part 2 | 100% |
| 06 | HTTP Plain-Text Credentials | 99% |
| 07 | FTP Brute-Force Detection | 100% |
| 08 | VoIP Call Analysis | 98% |
| **Average** | **6 labs** | **96%** |

## 3. Technical findings and learning outcomes

### Lab 03 — Identify the Attacker's IP
The supplied lab notes/official solution describe a 309-packet capture, 73 packets matching the SYN filter, source 192.168.10.66, target 192.168.10.20, source port 52311, 40 probed ports, and open ports 22, 80 and 443. Closed-port responses were described as RST/ACK. These exact values are attributed to the shared solution and were not independently recomputed from the original PCAP in this report-writing pass.

**Learning:** identify initial SYN traffic, correlate endpoints and interpret TCP responses as scan indicators.

### Lab 04 — Follow TCP Stream
The supplied notes describe a 246-packet capture, TCP port 5000, stream 5 and a 413-byte conversation between the exercise client and server.

**Learning:** reconstruct both directions of a TCP conversation and understand why unencrypted application messages can be exposed.

### Lab 05 — Follow TCP Stream, Part 2
The supplied notes identify a request for /staff.html, stream 7 and an HTTP 200 response. The exercise demonstrated that HTML comments are still delivered to the browser and can be inspected in page source.

**Learning:** never store secrets in client-delivered HTML, comments or JavaScript; enforce access control on the server.

### Lab 06 — HTTP Plain-Text Credentials
The supplied notes describe a 255-packet capture, HTTP POST /login and two login attempts. Actual credential values are intentionally excluded.

**Learning:** HTTP does not encrypt form data. Use correctly configured HTTPS/TLS and secure session handling.

### Lab 07 — FTP Brute-Force Detection
The supplied notes describe a 369-packet capture, 24 FTP failure responses (530) and a later success response (230). Password values are omitted.

**Learning:** repeated authentication failures followed by success warrant investigation and correlation. Prefer SFTP or properly configured FTPS, rate limits and monitoring.

### Lab 08 — VoIP Call Analysis
The supplied notes describe a 1,051-packet capture, SIP signalling, RTP media and PCMU codec. Personal/payment details from the training conversation are excluded.

**Learning:** signalling and media require protection; use TLS-protected SIP signalling and SRTP media where supported.

## 4. VirtualBox and Kali Linux

The archive includes screenshots of Kali running in VirtualBox and views of VM, network adapter and shared-folder configuration.

The assignment brief specifies a NAT Network of 10.0.0.0/24, expected Kali address 10.0.0.2/24, gateway 10.0.0.1 and guest shared-folder path /downloads. These are **expected assignment settings**, not blanket claims that each value was independently verified.

Suggested repeatable checks:

```bash
ip -br address
ip route
ip neigh
ping -c 4 10.0.0.1
getent hosts example.com
findmnt
ls -la /downloads
```

Record actual command output and date when performing these checks. A configuration screenshot alone does not establish successful connectivity or shared-folder read/write access.

## 5. Evidence mapping

- `VirtualBox-Kali-Lab/Evidence/` — setup and VM configuration screenshots.
- `Wireshark-SOC-Labs/Evidence/Lab-03/` through `Lab-08/` — matching result and analysis screenshots.
- `Wireshark-SOC-Labs/Reports/` — individual technical reports.
- `EVIDENCE-INDEX.md` — source inventory, result summary and upload state.

## 6. Privacy and safe handling

Before public release, review screenshots for credentials, session tokens, personal/payment information, host usernames, local paths, MAC addresses and unrelated device identifiers. Do not commit VM disk images, saved-state files, private keys or unreviewed PCAP files. The written reports deliberately omit training secrets.

## 7. Limitations

1. Supplied screenshots are visual evidence, not original PCAP files.
2. Packet-level values are attributed to supplied notes or official lab answers where stated; they were not independently recomputed from PCAPs here.
3. Assignment network values are distinguished from independently verified configuration.
4. The archive contains 46 images; this does not mean the binary images are already committed to GitHub.
5. No connectivity test is marked successful unless actual output supports it.

## Conclusion

Week 01 documents a practical sequence spanning Kali virtual-lab setup and six Wireshark exercises. The learner result cards average 96%. The portfolio records the technical learning, defensive implications, evidence sources, and verification limits without overstating what the screenshots prove.

*Evidence principle: map every screenshot to a task, attribute every result to its source, and separate observation from interpretation.*
