# WEEK 05 — Phishing, Malware Triage, Threat Intelligence & Incident Response

**Technical Activity & Evidence Review | DG Interns Hub**  
**Analyst:** Hafsa Khan  
**Focus:** Phishing, Malware Triage, Threat Intelligence and Incident Response  
**Evidence reviewed:** 34-image ZIP; 14 Week 05-related screenshots identified.

## 1. Executive Summary
This report reviews the Week 05 image evidence supplied for the DG Interns Hub track covering phishing analysis, malware triage, threat intelligence and incident response. Fourteen screenshots were identified as Week 05-related material. They show email-header authentication checks, an Outlook message marked Potential Phish, a VirusTotal file-details page, an interactive sandbox process graph, Windows Security EICAR views, MITRE ATT&CK Navigator matrices, three Atomic Red Team test executions, and incident-response timeline interfaces. The screenshots contain mixed provenance indicators, including dates and Windows profile names that do not match a current analyst session. Accordingly, this document is an evidence review and technical activity summary—not independent verification that every pictured task was performed by the named analyst.

## 2. Objectives
Examine suspicious email characteristics and authentication headers; extract and review file indicators; inspect suspicious process behaviour in a sandbox; understand EICAR antivirus detection; map observed behaviours to MITRE ATT&CK; execute selected Atomic Red Team tests in a controlled lab; and document an incident timeline with containment and recovery activities.

## 3. Scope and Evidence Basis
The source is the 34-image ZIP supplied in the conversation. Images 12–25 in the ZIP contain the Week 05-related material; the remaining images primarily show Splunk/SIEM material associated with Week 04. This report uses the visible content of those 14 images only. No additional logs, sandbox URLs, raw email files, exported ATT&CK layers, Atomic test logs or TryHackMe completion pages were supplied for this review.

## 4. Tools and Artefacts Visible
The screenshots visibly include Microsoft Outlook, Windows Security / Microsoft Defender Protection History, VirusTotal-style file analysis details, an interactive malware-analysis sandbox process graph, MITRE ATT&CK Navigator, Windows PowerShell with Atomic Red Team commands, and incident-management/timeline interfaces. The screenshots do not consistently show product versions, sample IDs, source URLs or a single common lab environment.

## 5. Technical Review by Workstream

### 5.1 Phishing and Email Analysis
One Outlook screenshot shows a message labelled “Potential Phish” with an overdue-invoice subject and a header attachment. A separate header view records SPF fail, DKIM fail and DMARC fail. These are suspicious authentication indicators in the displayed sample. The header uses example-style domains and placeholder-like values, so it should be treated as a training artefact. Only two distinct email-related screenshots are present; three separately documented phishing samples are not evidenced in this image set.

### 5.2 Malware Triage and File Intelligence
A VirusTotal-style screenshot shows one detection among 67 engines and displays file metadata including a SHA-256 value. A separate sandbox process graph shows a document-to-script execution chain involving winword.exe, powershell.exe, cmd.exe and cscript.exe; the graph marks raserver.exe as malicious with a 100/100 score. The screenshots do not expose a report URL, sample identifier or enough context to independently validate the files and analysis results.

### 5.3 EICAR and Endpoint Response
One Windows Security Protection History view shows Virus:DOS/EICAR_Test_File with status Removed. Another Windows Security scan-options view shows the same test detection as Active with Remove, Quarantine and Allow options. The visible dates and Windows profile path (including the “mitch” profile) do not establish that these captures came from the analyst’s current VM. The active-detection screenshot does not show which remediation option was finally selected.

### 5.4 MITRE ATT&CK Mapping
The supplied Navigator screenshots show populated ATT&CK matrices with highlighted technique cells and operation/layer tabs. They demonstrate matrix interaction and technique highlighting. No exported JSON layer, layer name/metadata or saved-layer proof is visible, so a completed export cannot be confirmed from these screenshots alone.

### 5.5 Atomic Red Team Execution
Three test families are represented:
- **T1087.001 — Account Discovery: Local Account:** the screenshot shows Invoke-AtomicTest details and a test execution that enumerates logged-on users through CMD; this is the clearest successful execution evidence in the set.
- **T1218.010 — Regsvr32:** multiple test cases are shown with mixed exit codes, including Access denied (exit code 5) and other outcomes. The evidence does not support describing every case as successful.
- **T1059.003 — Windows Command Shell:** the first batch test shows a file-not-found error; later commands display output including a command-shell message and a harmless print-bomb simulation. Treat the execution as mixed rather than uniformly successful.

### 5.6 Incident Response
Two screenshots show ransomware-related incident/timeline interfaces, including severity, affected assets, antivirus alert context, event timestamps, Sysmon EventCode 11 and a Wireshark SMB filter reference. They include timeline stages for identification, containment, eradication, recovery and lessons learned. The visible interface content appears to be scenario/case-study material; source and ownership are not established by the screenshots.

## 6. Evidence Register
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

## 7. Key Findings
The image set contains practical artefacts across phishing indicators, file reputation, sandbox process behaviour, EICAR detection, ATT&CK technique mapping, Atomic Red Team tests and incident timeline review. The clearest technical execution result is the T1087.001 local-account enumeration. The other two Atomic test families show mixed results and should be reported with their visible errors. The email authentication failures are suspicious indicators in the sample, not proof of a malicious sender on their own.

## 8. Evidence Quality, Safety and Validation
- Preserve original screenshots and redact personal paths, usernames, email addresses, tokens and other sensitive data before public upload.
- Add the raw email/sample source or sanitized headers for each phishing sample; this image set does not document three separate samples.
- Include VirusTotal and sandbox report URLs, sample hashes and analysis timestamps so the results can be reproduced.
- Include the EICAR test source and a fresh capture from the analyst’s own isolated VM showing detection and final quarantine/removal state.
- Export the ATT&CK Navigator layer (JSON) and retain its name and metadata.
- Save Atomic Red Team command output, test IDs, timestamps and cleanup results; explain failed test cases rather than omitting them.
- Identify the incident scenario source and attach the complete incident report with IOCs, impact, containment, eradication, recovery and lessons learned.
- The supplied image set does not contain TryHackMe completion pages or all underlying raw artefacts.

## 9. Conclusion
The supplied Week 05 screenshots provide a useful cross-section of phishing analysis, malware triage, threat intelligence and incident-response work. They support the specific observations and limitations recorded in this report. They do not, by themselves, independently verify every required deliverable or prove that every screenshot originated from one current lab environment. Final submission quality will improve by attaching the original report URLs, exported layer, execution logs and analyst-owned lab evidence.

## 10. Recommended Final Submission Attachments
Attach the 14 reviewed screenshots, three separate phishing sample records, two public sandbox report URLs with hashes, EICAR detection and remediation evidence from the analyst’s VM, exported ATT&CK Navigator JSON, Atomic Red Team logs and cleanup records, and the complete incident report. Include TryHackMe completion evidence if required by the programme.
