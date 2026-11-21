# Week 05 — Weekly Technical Report

**Analyst:** Hafsa Khan  
**Track:** DG Interns Hub  
**Focus:** Phishing, Malware Triage, Threat Intelligence and Incident Response  
**Reporting date:** 21 November 2026  
**Timezone:** Pakistan Standard Time (UTC+05:00)

## 1. Executive summary

Week 05 activities cover email threat investigation, safe malware triage, threat-intelligence enrichment, ATT&CK mapping and incident response documentation. The analyst has confirmed completion of the assigned practical work. This report is structured for final submission; original screenshots, exported artefacts and report references are to be attached in the evidence folders before submission.

## 2. Learning outcomes

The week's work addresses the following blue-team competencies:

- Recognising phishing techniques and identifying suspicious sender, message, URL and attachment characteristics.
- Interpreting SPF, DKIM and DMARC results and reviewing email headers to assess message authenticity.
- Distinguishing indicators of compromise (IOCs) from indicators of attack (IOAs), and understanding the Pyramid of Pain.
- Reviewing suspicious files safely with EICAR validation and public sandbox intelligence rather than executing live malware.
- Relating observed adversary behaviour to the Cyber Kill Chain and MITRE ATT&CK.
- Recording investigation timelines, evidence, impact, containment decisions and recommendations in an incident report.

## 3. Practical activity completion register

| Activity | Completion state | Evidence to attach |
|---|---|---|
| Three phishing sample investigations | Completed | Case notes, header/authentication review, defanged indicators, verdicts and screenshots |
| EICAR antivirus validation | Completed | EICAR test record, antivirus event and available Sysmon/SIEM evidence |
| Two public sandbox report reviews | Completed | Public report URLs/IDs, process-tree observations, network indicators and screenshots |
| ATT&CK Navigator mapping | Completed | Exported Navigator layer JSON and screenshot |
| Three Atomic Red Team tests | Completed | Test identifiers, execution records, relevant telemetry, alert outcomes and cleanup evidence |
| Incident response report | Prepared | Final case timeline, IOCs and supporting evidence |

## 4. Investigation approach

The investigations follow a repeatable defensive workflow:

1. Preserve the original artefact and record its source and collection time.
2. Review message metadata and authentication results before reaching a phishing verdict.
3. Defang suspicious URLs and record indicators in a safe, non-clickable format.
4. Enrich hashes, domains and IP addresses using appropriate public intelligence sources, considering data-sharing implications.
5. Review sandbox behaviour without downloading or executing the sample locally.
6. Map only evidence-supported behaviours to ATT&CK techniques.
7. Correlate endpoint and SIEM telemetry for the controlled Atomic tests.
8. Document findings, severity, containment, recovery and recommendations.

## 5. Evidence register

Attach the original artefacts to the matching locations:

- `Findings/Phishing-01/`, `Phishing-02/`, `Phishing-03/`
- `Findings/EICAR/`
- `Findings/Public-Sandbox-01/`, `Public-Sandbox-02/`
- `Findings/ATTACK-Navigator/`
- `Findings/Atomic-T1059.001/`, `Atomic-T1136.001/`, `Atomic-T1053.005/`
- `Incident Report/`

For each artefact, retain the source, timestamp and relevant case/test identifier. Redact personal information, credentials and unrelated account data.

## 6. Safety and limitations

- No live malware should be downloaded or executed as part of this work.
- EICAR is a harmless antivirus test string and must not be described as real malware.
- Public sandbox reports are third-party analysis records; their findings should be attributed to the report source.
- Atomic Red Team testing is limited to authorised, isolated lab systems and should be followed by cleanup or snapshot restoration.
- MITRE and Pyramid of Pain TryHackMe rooms are listed as Premium/Max restricted in the room-access notes. Topic coverage and platform room completion are reported separately; do not claim a TryHackMe completion badge for a locked room.

## 7. Conclusion

Week 05 learning and practical activities have been reported complete by the analyst. The final submission step is to attach the original screenshots, exports and report references, then verify that every recorded result is supported by its corresponding evidence. The repository's templates and training examples are supporting documentation, not substitutes for original lab artefacts.
