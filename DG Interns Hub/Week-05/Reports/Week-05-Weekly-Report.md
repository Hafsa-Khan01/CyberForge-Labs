# Week 05 — Weekly Technical Report

**Analyst:** Hafsa Khan  
**Track:** DG Interns Hub  
**Focus:** Phishing, Malware Triage, Threat Intelligence and Incident Response  
**Reporting date:** 24 November 2026  
**Timezone:** Pakistan Standard Time (UTC+05:00)

## 1. Executive summary

Week 05 activities cover email threat investigation, safe malware triage, threat-intelligence enrichment, ATT&CK mapping and incident response documentation. The analyst confirmed completion of the assigned practical work. Fourteen selected screenshots are published in the [Evidence folder](../Evidence/). This report distinguishes visible screenshot evidence from activities that require additional raw records or exported artifacts.

## 2. Learning outcomes

The week's work addresses the following blue-team competencies:
- Recognising phishing techniques and identifying suspicious sender, message, URL and attachment characteristics.
- Interpreting SPF, DKIM and DMARC results and reviewing email headers to assess message authenticity.
- Distinguishing indicators of compromise (IOCs) from indicators of attack (IOAs), and understanding the Pyramid of Pain.
- Reviewing suspicious files safely with EICAR validation and public sandbox intelligence rather than executing live malware.
- Relating observed adversary behaviour to the Cyber Kill Chain and MITRE ATT&CK.
- Recording investigation timelines, evidence, impact, containment decisions and recommendations in an incident report.

## 3. Practical activity completion register

| Activity | Completion state | Evidence status |
|---|---|---|
| Three phishing sample investigations | Completed, as confirmed by analyst | Two email-related screenshots in uploaded set; three separate case records are not visible |
| EICAR antivirus validation | Completed, as confirmed by analyst | Two screenshots present; historical/sample profile details visible and final remediation not established |
| Two public sandbox report reviews | Completed, as confirmed by analyst | Two analysis screenshots present; public report URLs/IDs are not visible |
| ATT&CK Navigator mapping | Completed, as confirmed by analyst | Matrix screenshots present; exported Navigator layer JSON not included |
| Three Atomic Red Team tests | Completed, as confirmed by analyst | Three test families represented; mixed outcomes and cleanup evidence not fully shown |
| Incident response report | Prepared | Scenario/timeline screenshots present; source provenance and a complete authored incident report need confirmation |

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

The fourteen selected images are stored in [Evidence](../Evidence/). The detailed screenshot-by-screenshot review is below. For each artifact, retain the source, timestamp and relevant case/test identifier. Redact personal information, credentials and unrelated account data.

## 6. Safety and limitations

- No live malware should be downloaded or executed as part of this work.
- EICAR is a harmless antivirus test string and must not be described as real malware.
- Public sandbox reports are third-party analysis records; their findings should be attributed to the report source.
- Atomic Red Team testing is limited to authorised, isolated lab systems and should be followed by cleanup or snapshot restoration.
- MITRE and Pyramid of Pain TryHackMe rooms are listed as Premium/Max restricted in the room-access notes. Topic coverage and platform room completion are reported separately; do not claim a TryHackMe completion badge for a locked room.

## 7. Conclusion

Week 05 learning and practical activities are reported complete by the analyst. The repository contains the weekly notes, room/resource writeups, templates, report and fourteen selected screenshots. Some underlying artifacts—such as separate phishing case records, sandbox report identifiers, Navigator JSON, complete Atomic logs and a fully sourced incident report—are not visible in the uploaded screenshot set. Those items should only be marked as submitted when their original files are present.

## 8. Evidence-based technical review

The supplied 34-image ZIP was reviewed and 14 images (original image order 12–25) were identified as Week 05 material. The remaining images primarily relate to Week 04 Splunk work.

### 8.1 Phishing and email analysis

One Outlook screenshot shows a message labelled “Potential Phish” with an overdue-invoice subject and a header attachment. A separate header view records SPF fail, DKIM fail and DMARC fail. These are suspicious authentication indicators in the displayed sample, not standalone proof of maliciousness. The header contains example-style domains and placeholder-like values. Only two distinct email-related screenshots are present; three separately documented phishing samples are not evidenced in this image set.

### 8.2 Malware triage and file intelligence

A VirusTotal-style screenshot shows one detection among 67 engines and displays file metadata including a SHA-256 value. A separate sandbox process graph shows a document-to-script chain involving winword.exe, powershell.exe, cmd.exe and cscript.exe; raserver.exe is marked malicious with a 100/100 score. The screenshots do not show report URLs or sample IDs, so the results cannot be independently reproduced from this evidence alone.

### 8.3 EICAR and endpoint response

One Windows Security Protection History view shows Virus:DOS/EICAR_Test_File with status Removed. Another scan-options view shows the same test detection as Active with Remove, Quarantine and Allow options. The visible dates and Windows profile path (including “mitch”) do not establish that these captures came from the analyst's current VM. The active-detection screenshot does not show the final remediation action.

### 8.4 MITRE ATT&CK mapping

Navigator screenshots show populated ATT&CK matrices with highlighted technique cells and operation/layer tabs. They demonstrate matrix interaction and technique highlighting, but no exported JSON layer, layer metadata or saved-export proof is visible.

### 8.5 Atomic Red Team execution

Three test families are represented:
- **T1087.001 — Account Discovery: Local Account:** the screenshot shows an execution that enumerates logged-on users through CMD; this is the clearest successful test evidence.
- **T1218.010 — Regsvr32:** multiple test cases show mixed exit codes, including Access denied (exit code 5). Not every case can be described as successful.
- **T1059.003 — Windows Command Shell:** the first batch test shows a file-not-found error; later commands display output including a command-shell message and a harmless print-bomb simulation. Results are mixed.

### 8.6 Incident response

Two screenshots show ransomware-related incident/timeline interfaces, including severity, affected assets, antivirus alert context, timestamps, Sysmon EventCode 11 and a Wireshark SMB filter reference. The interface includes identification, containment, eradication, recovery and lessons-learned stages. Source and ownership are not established, so treat these as scenario/case-study material until provenance is confirmed.

### 8.7 Screenshot evidence register

| Evidence ID | Visible material | Review note |
|---|---|---|
| W5-01 | Windows Security EICAR Protection History — Removed | Historical/sample profile details visible |
| W5-02 | Email header — SPF, DKIM and DMARC fail | Training/example-style values |
| W5-03 | Outlook message labelled Potential Phish | One phishing email view |
| W5-04 | VirusTotal-style file details — 1/67 detections | SHA-256 visible; report URL/sample ID absent |
| W5-05 | Sandbox process graph | Word-to-script chain; raserver.exe flagged 100/100 |
| W5-06 | Windows Security EICAR scan options — Active | Final remediation action not shown |
| W5-07 | MITRE ATT&CK Navigator matrix | Highlighted techniques; export not shown |
| W5-08 | Atomic Red Team T1087.001 | Local account discovery; successful enumeration visible |
| W5-09 | Ransomware incident interface | Treat as case-study/mock data until provenance is confirmed |
| W5-10 | MITRE ATT&CK Navigator layer view | Layer tabs visible; saved export not established |
| W5-11 | Atomic Red Team T1218.010 | Mixed exit codes and access-denied outcome |
| W5-12 | Incident event timeline | Sysmon EventCode 11 and SMB filter reference visible |
| W5-13 | MITRE ATT&CK Navigator matrix | Highlighted techniques; export not shown |
| W5-14 | Atomic Red Team T1059.003 | Initial file-not-found error; later command output shown |

### 8.8 Evidence quality and remaining artifacts

The screenshot set is uploaded. For a stronger, independently reproducible submission, add the raw/sanitised email records for all three phishing cases, VirusTotal and sandbox report URLs with hashes, fresh EICAR evidence from the analyst's own isolated VM showing final remediation, exported ATT&CK Navigator JSON, Atomic Red Team logs with test IDs and cleanup results, and the complete incident report with IOCs, impact, timeline, containment, eradication and recovery. Redact personal paths, usernames, email addresses and credentials. Do not execute live malware. Public sandbox results should be attributed to their source.

The supplied screenshots do not include TryHackMe completion pages or all underlying raw artifacts. A template or example is not proof of execution. Keep platform completion distinct from equivalent topic coverage for any room that is subscription-restricted.
