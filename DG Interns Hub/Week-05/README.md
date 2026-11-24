# Week 05 — Phishing, Malware Triage, Threat Intelligence & Incident Response

**Analyst:** Hafsa Khan  
**Programme:** DG Interns Hub  
**Focus:** Tier 1 / Tier 2 blue-team investigation  
**Submission deadline:** 22 November 2026, 11:59 PM (PKT)

## Completion overview

The analyst has confirmed completion of the assigned learning and practical work. Fourteen selected screenshots from the supplied evidence set are uploaded under [Evidence](Evidence/). The weekly report records what each screenshot demonstrates and explicitly notes where additional source records or exports are not present.

| Deliverable | Status |
|---|---|
| Eight theory notes | Complete |
| Core room learning/writeups | Prepared; see room-access note |
| Optional learning resources | Reference notes prepared |
| Phishing analysis | Practical work reported complete; two email-related screenshots in current evidence set |
| EICAR validation | Practical work reported complete; supplied screenshots have historical/sample profile details |
| Public sandbox reviews | Practical work reported complete; screenshots present, but source URLs/sample IDs are not visible |
| ATT&CK Navigator mapping | Matrix screenshots uploaded; exported layer JSON not included |
| Atomic Red Team tests | Three test families represented; outcomes include mixed results |
| Incident response | Scenario/case-study screenshots uploaded; source provenance is not established |
| IOC cheat sheet and phishing checklist | Complete |
| Weekly report and presentation outline | Prepared |

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
| [Writeups](Writeups/) | Room/resource/challenge writeups and access notes |
| [Findings](Findings/) | Phishing cases, EICAR, sandbox, Navigator and atomic-test documentation |
| [Incident Report](Incident%20Report/) | Incident report template and worked training scenario |
| [Cheat Sheet](Cheat%20Sheet/) | IOC reference and phishing red-flag checklist |
| [Evidence](Evidence/) | Fourteen selected original screenshots |
| [Reports](Reports/) | Weekly report, submission checklist and presentation outline |

## TryHackMe access and completion note

The Week 05 assignment includes rooms that may be restricted by the account's subscription. The MITRE and Pyramid of Pain room pages indicated Premium/Max access in the earlier review. The corresponding learning objectives are covered in the Week 05 study material; however, a locked room must not be represented as a completed TryHackMe room unless its own completion state is visible in the account. Use room-specific writeups to distinguish platform completion from equivalent topic coverage.

- [Cyber Kill Chain](https://tryhackme.com/room/cyberkillchainzmt)
- [MITRE](https://tryhackme.com/room/mitre) — Premium/Max access indicated
- [Pyramid of Pain](https://tryhackme.com/room/pyramidofpainax) — Premium/Max access indicated
- [Phishing Analysis Fundamentals](https://tryhackme.com/room/phishingemails1tryoe)
- [Intro to Cyber Threat Intel](https://tryhackme.com/room/cyberthreatintel)
- Optional: [Threat Intelligence Tools](https://tryhackme.com/room/threatinteltools) and [Yara](https://tryhackme.com/room/yara)

## Reports and evidence
- [Week 05 Weekly Report](Reports/Week-05-Weekly-Report.md)
- [Submission Checklist](Reports/Submission-Checklist.md)
- [Uploaded Evidence](Evidence/)

## Lab safety and evidence integrity
- Never download or execute live malware. Use EICAR only for local antivirus validation and public sandbox reports for behavioural review.
- Do not click suspicious links. Use defanged indicators and reputation services; public scanners may disclose submitted data to third parties.
- Use isolated, snapshotted VMs for authorised tests. Atomic Red Team tests must be run only on the analyst's own lab VM and reverted afterwards.
- Keep original evidence read-only; record timezone, collection time, source and SHA-256 where applicable.
- A template or example is not proof of execution. Screenshots and exports should support the exact activity being reported.

## References
- [NIST SP 800-61 Rev. 2](https://csrc.nist.gov/pubs/sp/800/61/r2/final)
- [MITRE ATT&CK](https://attack.mitre.org/)
- [Cyber Kill Chain](https://www.lockheedmartin.com/en-us/capabilities/cyber/cyber-kill-chain.html)
- [ATT&CK Navigator](https://mitre-attack.github.io/attack-navigator/)

[Return to DG Interns Hub](../README.md)
