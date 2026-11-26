# Week 05 — Weekly Technical Report

**Analyst:** Hafsa Khan  
**Track:** DG Interns Hub  
**Focus:** Phishing, Malware Triage, Threat Intelligence and Incident Response  
**Reporting date:** 24 November 2026  
**Timezone:** Pakistan Standard Time (UTC+05:00)

## 1. Executive summary

Week 05 is complete. The assigned learning and practical work covered phishing investigation, safe malware triage, threat-intelligence enrichment, MITRE ATT&CK mapping, controlled Atomic Red Team exercises and incident response documentation. The weekly notes, writeups, findings, reference material, report and selected evidence have been organised in this repository.

## 2. Learning outcomes

- Recognise phishing techniques and assess suspicious sender, message, URL and attachment characteristics.
- Interpret SPF, DKIM and DMARC results and review email headers.
- Distinguish indicators of compromise (IOCs) from indicators of attack (IOAs).
- Apply safe EICAR validation and review public sandbox intelligence.
- Relate observed adversary behaviour to the Cyber Kill Chain and MITRE ATT&CK.
- Record investigation timelines, evidence, impact, containment decisions and recommendations.

## 3. Practical activity completion register

| Activity | Status |
|---|---|
| Three phishing sample investigations | Complete |
| EICAR antivirus validation | Complete |
| Two public sandbox report reviews | Complete |
| MITRE ATT&CK Navigator mapping | Complete |
| Three Atomic Red Team exercises | Complete |
| Incident response activity and documentation | Complete |
| IOC reference sheet and phishing red-flag checklist | Complete |
| Weekly notes, writeups and reporting | Complete |

## 4. Investigation workflow

1. Preserve investigation artefacts and record relevant source context.
2. Review message metadata and authentication results.
3. Defang suspicious URLs and document indicators safely.
4. Enrich hashes, domains and IP addresses using appropriate intelligence sources.
5. Review sandbox behaviour without executing live malware locally.
6. Map observed behaviours to relevant ATT&CK techniques.
7. Review endpoint and security telemetry for controlled test activity.
8. Document findings, severity, response actions and recommendations.

## 5. Evidence and repository contents

Fourteen selected Week 05 screenshots are stored in the [Evidence folder](../Evidence/). The evidence register below identifies the material represented in the selected images.

| Evidence ID | Activity |
|---|---|
| W5-01 | Windows Security EICAR Protection History |
| W5-02 | Email header authentication review — SPF, DKIM and DMARC |
| W5-03 | Phishing email review |
| W5-04 | File reputation and hash review |
| W5-05 | Sandbox process behaviour analysis |
| W5-06 | EICAR scan and antivirus response options |
| W5-07 | MITRE ATT&CK Navigator technique mapping |
| W5-08 | Atomic Red Team T1087.001 — Account Discovery |
| W5-09 | Incident response scenario review |
| W5-10 | ATT&CK Navigator layer review |
| W5-11 | Atomic Red Team T1218.010 — Regsvr32 |
| W5-12 | Incident event timeline and security telemetry |
| W5-13 | ATT&CK Navigator technique mapping |
| W5-14 | Atomic Red Team T1059.003 — Windows Command Shell |

## 6. Technical review

### 6.1 Phishing and email analysis
Reviewed phishing-message characteristics and email authentication results, including SPF, DKIM and DMARC. The investigation workflow focused on sender and header analysis, suspicious message content, attachment awareness and safe URL handling.

### 6.2 Malware triage and file intelligence
Reviewed file reputation information, SHA-256 metadata and sandbox process behaviour. The observed process chain included document and scripting components such as winword.exe, powershell.exe, cmd.exe and cscript.exe. The work focused on interpreting reported behaviour safely rather than executing live malware.

### 6.3 EICAR and endpoint response
Completed antivirus validation using the harmless EICAR test file and reviewed Windows Security detection and response options. EICAR is an antivirus test artefact, not real malware.

### 6.4 MITRE ATT&CK mapping
Used ATT&CK Navigator to review technique mappings and relate observed behaviours to the ATT&CK knowledge base.

### 6.5 Atomic Red Team exercises
Completed exercises covering:
- **T1087.001 — Account Discovery: Local Account**
- **T1218.010 — Regsvr32**
- **T1059.003 — Windows Command Shell**

The exercises provided practical exposure to controlled adversary-technique simulation, command execution behaviour and endpoint telemetry. Individual test outputs were reviewed as part of the exercises.

### 6.6 Incident response
Worked through incident response scenarios and timeline material covering identification, containment, eradication, recovery and lessons learned. Reviewed supporting endpoint and network telemetry concepts, including Sysmon EventCode 11 and Wireshark SMB filtering.

## 7. Safety practices

- EICAR was used for antivirus validation; live malware was not required.
- Public sandbox analysis was used as a safe way to review reported file behaviour.
- Suspicious links were handled without unsafe interaction.
- Controlled security tests were performed within authorised lab scope.
- Personal information and sensitive values should be protected when sharing evidence.

## 8. Conclusion

**Week 05 is fully completed.** All assigned learning objectives and practical activities have been completed, and the repository contains the weekly notes, writeups, findings, evidence, reference material, technical report and presentation outline. The work strengthened practical understanding of phishing analysis, malware triage, threat intelligence, ATT&CK mapping, adversary-technique simulation and incident response.

