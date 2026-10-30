# Wireshark Lab Report — Identify the Attacker's IP

| Field | Details |
|---|---|
| Programme | NetworkWalks Cybersecurity Internship |
| Prepared by | Hafsa Khan |
| Practical | Lab 03 — Identify the Attacker's IP |
| Result | 89% |
| Tool | Wireshark |
| Scope | Assigned training capture |

## 1. Overview

This practical focused on identifying port-scanning behaviour in a network capture. The completed exercise involved filtering TCP SYN traffic, reviewing source and destination addresses, and interpreting the responses associated with probed ports.

## 2. Objective

Identify the suspected scanning host, determine the target system, review the SYN packet pattern, and interpret the reported port states and TCP response flags.

## 3. Analysis workflow

1. Open the assigned training capture in Wireshark.
2. Review the capture packet count.
3. Apply the display filter `tcp.flags.syn == 1`.
4. Inspect source and destination addresses and destination-port activity.
5. Review TCP response flags and compare open- and closed-port behaviour.
6. Record the findings and complete the lab assessment.

## 4. Results

| Check | Recorded result |
|---|---|
| Total packets in capture | 309 |
| Packets matching the SYN filter | 73 |
| Suspected scanning source | `192.168.10.66` |
| Target host | `192.168.10.20` |
| Scanner source port | `52311` |
| Ports probed | 40 |
| Open ports | 22, 80, 443 |
| Closed-port response flags | `RST, ACK` |
| Closed ports reported | 37 |
| Activity classification | Port scan |
| Assessment score | 89% |

## 5. Technical interpretation

A SYN-focused display filter helps isolate initial TCP connection attempts. Repeated SYN packets directed towards multiple destination ports can be consistent with port-scanning activity. Responses carrying RST and ACK flags commonly indicate that a TCP connection attempt was rejected, including when a destination port is closed.

The findings demonstrate how packet flags, endpoint addresses, destination-port distribution and response patterns can be considered together when investigating network reconnaissance.

## 6. Security relevance

- Monitor unusual connection rates and broad destination-port coverage.
- Establish baselines for approved vulnerability scanners and administrative tools.
- Correlate network alerts with firewall and endpoint telemetry.
- Investigate unexpected scanning activity within the authorised network scope.

## 7. Evidence

The completed Lab 03 result card is published in `../Evidence/Lab-03/`. Practical screenshots are retained with the Week 01 source evidence archive. The result card records the assessment outcome, while the screenshots provide supporting practical context.

## 8. Conclusion

The exercise provided practical experience in filtering TCP SYN traffic and interpreting port-scan indicators. The recorded result was **89%**. The analysis reinforces the importance of correlating packet flags, source and destination hosts, and port-level responses before drawing conclusions about reconnaissance activity.

---

**Prepared for:** NetworkWalks Cybersecurity Internship — Week 01  
**Author:** Hafsa Khan
