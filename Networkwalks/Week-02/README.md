# NetworkWalks — Week 02 Project Work

**Prepared by:** Hafsa Khan  
**Programme:** NetworkWalks Cybersecurity & Ethical Hacking  
**Assignment deadline:** 23:00, Friday 13 November 2026 (as stated in the assignment PDF)

## Week 02 submission

The Week 02 brief requires at least one elective from PM1–PM4, plus both essential modules: PM5 and PM-FINAL.

| Module | Assignment | Status in this repository |
|---|---|---|
| W2-PM1 | Footprinting with multiple Kali tools | Completed practical work documented in the final report |
| W2-PM2 | GHDB-based Footprinting Attacks | Not included as a completed module |
| W2-PM3 | Maltego-based Footprinting Attacks | Not included as a completed module |
| W2-PM4 | theHarvester-based Footprinting Attacks | Attempted; official Microsoft target and commands documented. Output not validated; see [PM4 notes](PM4-THEHARVESTER.md) |
| W2-PM5 | Zenmap-based Network Scanning | Completed local Wi-Fi Ping Scan documented in the final report |
| W2-PM-FINAL | Detailed report | Final report added |

PM1 provides the selected elective. PM5 and PM-FINAL are the essential modules. PM4 is additionally documented as an attempted elective exercise; its successful output has not yet been verified.

## Main documents

- [Final Penetration Testing Report](FINAL-REPORT.md)
- [Evidence Index](EVIDENCE-INDEX.md)\n- [PM4 theHarvester Notes](PM4-THEHARVESTER.md)
- [Report Template](REPORT-TEMPLATE.md)
- [LOA Draft / Request Template](LOA-DRAFT.md)

## Key verified PM5 results

- Active adapter: Windows Wi-Fi
- IPv4: `192.168.100.33`
- Subnet mask: `255.255.255.0`
- Gateway: `192.168.100.1`
- Scan target: `192.168.100.0/24`
- Scan profile: Zenmap Ping Scan (`nmap -sn`)
- Result: 256 IP addresses scanned; 2 hosts up
- Router MAC shown in Nmap output: `30:D1:7E:4D:EC:10` (Huawei Technologies)
- Windows host MAC: not displayed in the recorded Nmap output
- Topology: saved locally as PDF; upload to the evidence folder is still required

## Authorization and scope

The tester stated that NetworkWalks permission was provided separately. The assignment PDF contains a **sample** Letter of Authorization; it is not the tester's signed authorization. The signed authorization should be retained privately and shared with the programme supervisor when required. Do not publish signatures, personal contact details, or confidential scope information without the issuer's permission.

The PM5 scan documented in the report was performed against the tester's own local Wi-Fi subnet. Do not treat other private IP ranges or third-party domains as authorized solely because they are reachable or appear in lab materials.

The [LOA-DRAFT.md](LOA-DRAFT.md) is an unsigned request/template and does not grant permission.

## Evidence status

The report identifies the PM1, PM4, and PM5 evidence artifacts. Original screenshots and the topology PDF are not yet committed to this repository. Upload redacted originals to the appropriate evidence folders before treating the GitHub evidence pack as complete.

Do not upload credentials, tokens, private keys, VM disk images, or unrelated personal/network data.

## Branch policy

This Week 02 work is maintained on `week-02-project-work`. The `main` branch has not been changed or merged.
