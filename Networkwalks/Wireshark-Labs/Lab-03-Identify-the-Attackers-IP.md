# Lab 3 — Identify the Attacker's IP

**Internship:** Networkwalks  
**Tool:** Wireshark  
**Status:** Completed by the learner  
**Reported score:** 89/100

## Objective
Identify the source and target IP addresses involved in the supplied port-scan traffic and interpret the relevant TCP flags and port results.

## Findings
| Check | Result |
|---|---|
| Total packets shown in the capture | 309 |
| Packets displayed with `tcp.flags.syn == 1` | 73 |
| Suspected scanning source | `192.168.10.66` |
| Target host | `192.168.10.20` |
| Attacker source port | `52311` |
| Number of ports probed | 40 |
| Ports reported open | 22, 80, 443 |
| Flags associated with closed-port replies | `RST, ACK` |
| Closed ports reported | 37 |
| Identified activity | Port scan |

## Method
1. Open the supplied capture in Wireshark.
2. Review the packet count in the status bar.
3. Apply the display filter `tcp.flags.syn == 1`.
4. Review source and destination addresses and TCP port details.
5. Compare replies for open and closed ports, including TCP flags.
6. Check answers against the lab's official solution.

## Filter used
```wireshark
tcp.flags.syn == 1
```

## Interpretation
The SYN-filtered traffic and repeated connection attempts across multiple destination ports are consistent with port-scanning activity. The lab's official solution identifies `192.168.10.66` as the scanner and `192.168.10.20` as the target. Replies marked `RST, ACK` were associated with closed ports in this exercise.

## Result correction
The displayed-packet answer for Question 2 is **73**, matching the official solution. The learner initially entered 55 and received 89/100 overall.

## Evidence
The learner reported completing the lab. Add reviewed screenshots to the `Evidence/` folder if they are available and permitted by the internship rules. No screenshot or raw capture is claimed as committed in this report.

## Limitations
This report records the results supplied from the lab and its official solution; it does not independently re-analyse a packet capture. Keep the original capture private unless the internship explicitly permits sharing it.

## Conclusion
Lab 3 is reported complete with a score of 89/100. The confirmed correction is Question 2: **73 displayed packets**.
