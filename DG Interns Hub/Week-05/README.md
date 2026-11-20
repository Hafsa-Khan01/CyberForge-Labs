# Week 05 — Phishing, Malware Triage, Threat Intelligence & Incident Response

**Track:** DG Interns Hub | **Focus:** Tier 1 / Tier 2 blue-team investigation

## Objectives
- Examine email headers and authentication results without interacting with suspicious links.
- Enrich and document IOCs with source, timestamp, confidence and defanged values.
- Perform safe malware triage using EICAR and public sandbox reports only.
- Map observed behaviours to MITRE ATT&CK and the Cyber Kill Chain.
- Produce evidence-led incident reports and practical detection recommendations.

## Folder map
| Folder | Contents |
|---|---|
| [Notes](Notes/) | Eight separate theory answers |
| [Writeups](Writeups/) | Separate room/resource/challenge writeups; completion status is explicit |
| [Findings](Findings/) | Evidence register, phishing cases, EICAR, sandbox, Navigator and atomic-test records |
| [Incident Report](Incident%20Report/) | Incident report template and worked fictional training scenario |
| [Cheat Sheet](Cheat%20Sheet/) | IOC reference and phishing red-flag checklist |
| Reports | Weekly report, presentation outline, LinkedIn drafts and submission checklist |

## Lab safety and evidence integrity
- Never download or execute live malware. Use EICAR only for local antivirus validation and public sandbox reports for behavioural review.
- Do not click suspicious links. Use defanged indicators and reputation services; public scanners may disclose submitted data to third parties.
- Use isolated, snapshotted VMs for authorised tests. Atomic Red Team tests must be run only on the user's own lab VM and reverted afterwards.
- Keep original evidence read-only; record timezone, collection time, source and SHA-256 where applicable.
- A template or example is not proof of execution. Replace every **[FILL FROM YOUR LAB]** field with actual evidence and do not claim an alert fired unless the SIEM confirms it.

## TryHackMe access note
Room availability can change by account, region and room updates. Current public pages explicitly show **MITRE** and **Pyramid of Pain** as Premium/Max. The Cyber Kill Chain, Phishing Analysis Fundamentals and Intro to Cyber Threat Intel pages are accessible as room information, but sign-in access should be checked in the user's own free account before marking any as completed. No room is marked completed by this repository.

## Weekly deliverables
- Eight theory notes, five core room writeup shells, two optional room shells.
- Evidence templates for three phishing samples, EICAR, two public sandbox reports, ATT&CK Navigator and three Atomic tests.
- Incident report template, IOC reference table, phishing checklist.
- Weekly report, presentation outline, LinkedIn post drafts and final checklist.

## References
- NIST SP 800-61 Rev. 2: https://csrc.nist.gov/pubs/sp/800/61/r2/final
- MITRE ATT&CK: https://attack.mitre.org/
- Cyber Kill Chain: https://www.lockheedmartin.com/en-us/capabilities/cyber/cyber-kill-chain.html
- ATT&CK Navigator: https://mitre-attack.github.io/attack-navigator/
- TryHackMe free rooms: https://tryhackme.com/free-rooms

**Status:** Documentation scaffold prepared. Practical findings and screenshots must be added from the actual lab before submission.
