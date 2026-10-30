# Wireshark Lab Report — Identify the Attacker's IP

| Field | Details |
|---|---|
| Programme | Networkwalks Internship |
| Prepared by | Hafsa Khan |
| Report date | 2026-10-29 |
| Date performed | Not recorded in the available notes |
| Report status | Draft — evidence review pending |
| Reported score | 89/100 |

> **Basis of this report:** This document records the answers and official-solution details provided after the lab. The original packet capture and screenshots were not available during this repository documentation update, so the packet-level findings have not been independently re-analysed here.

## 1. Summary

The assigned practical, **Identify the Attacker's IP**, focused on recognising port-scanning activity in a Wireshark capture. The learner reported completing the lab with a score of 89/100. According to the official solution shared for review, the SYN display filter showed 73 packets, the suspected scanning source was `192.168.10.66`, and the target was `192.168.10.20`. These values are recorded as lab-reported results, not as independently re-verified packet-capture observations.

## 2. Objective

Identify the suspected scanning source and target in the assigned capture, inspect TCP SYN traffic, and interpret the reported port results and TCP flags.

## 3. Lab environment and scope

| Item | Details |
|---|---|
| Host operating system | Not recorded |
| Capture / target | Assigned lab capture; original file not available for this report review |
| Wireshark version | Not recorded |
| Tool used | Wireshark |
| Display filter reported | `tcp.flags.syn == 1` |
| Authorised scope | The assigned lab exercise only |

The original capture and the exact lab URL were not present in the material available for this documentation update. Environment details have therefore not been guessed.

## 4. Method

The following workflow is recorded from the lab questions and official solution shared for review:

1. Open the assigned capture in Wireshark.
2. Review the packet count displayed in the status bar.
3. Apply the display filter `tcp.flags.syn == 1`.
4. Inspect source and destination addresses and TCP port information.
5. Compare the reported open-port results with replies associated with closed ports.
6. Compare answers with the official lab solution.

This is a summary of the lab workflow, not a claim that the capture was re-opened during this report-writing session.

## 5. Results and observations

| Check | Reported result | Verification status |
|---|---|---|
| Total packets in capture | 309 | From the official solution shared for review |
| Packets displayed by `tcp.flags.syn == 1` | 73 | Official answer; the learner reported initially entering 55 |
| Suspected scanning source | `192.168.10.66` | Official answer |
| Target host | `192.168.10.20` | Official answer |
| Source port reported for the scanner | `52311` | Official answer |
| Ports probed | 40 | Official answer |
| Open ports | 22, 80, 443 | Official answer |
| Closed-port reply flags | `RST, ACK` | Official answer |
| Closed ports reported | 37 | Official answer |
| Activity classification | Port scan | Official answer |
| Overall score | 89/100 | Learner-reported score |

## 6. Technical analysis

A SYN display filter selects TCP packets whose SYN flag is set. Repeated connection attempts to multiple destination ports can be consistent with port-scanning activity. TCP replies carrying RST and ACK flags are commonly associated with rejected or closed TCP connection attempts.

For this exercise, the values in the table are attributed to the official solution shared after completion. Without the original capture, this report cannot independently confirm packet counts, endpoint roles, port states, or whether every listed result is visible in the capture.

## 7. Issues and resolution

The learner reported an incorrect response for Question 2: 55 displayed packets. The official solution provided for comparison gives **73 displayed packets**. The correction is documented here. The original quiz review screen was not available for independent verification during this documentation update.

## 8. Evidence

| Evidence | Status |
|---|---|
| Original capture file | Not included in this repository update |
| Screenshot of the filter and packet count | Not available for review |
| Quiz score screenshot | Not available for review |
| Official solution | Values were pasted into the conversation; no separate source file was added |

Do not treat the Evidence folder's `.gitkeep` file as practical evidence. Add only genuine screenshots that are permitted for sharing, review them for sensitive information, and give them meaningful filenames.

## 9. Conclusion

The learner reported completing the assigned practical with a score of 89/100. The official solution shared for review gives 73 displayed packets for Question 2 and identifies the activity as a port scan. This report remains a draft until the original capture or permitted screenshots can be checked against the recorded findings.

## 10. Learning and next step

The key correction is to distinguish the total capture packet count from the number of packets matching a display filter. If evidence is required for submission, add sanitised screenshots showing the relevant Wireshark result and record the actual lab date and software version. Otherwise, proceed only when Networkwalks provides the next official task.

---

*Review status: Draft. Claims are explicitly attributed to the learner or the official solution where independent verification was not possible.*
