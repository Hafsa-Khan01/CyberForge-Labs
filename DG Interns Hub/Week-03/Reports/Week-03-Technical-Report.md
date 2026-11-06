# Week 03 Technical Report
## Linux Logs, Sysmon, auditd and Snort Setup

**Programme:** DG Interns Hub  
**Focus:** Endpoint telemetry · Linux auditing · Network intrusion detection · MITRE ATT&CK  
**Evidence review:** Supplied practical screenshot archive dated 4–6 November 2026

## 1. Executive summary
This report organizes the week's work across three telemetry layers: Windows endpoint events collected by Sysmon, Linux activity recorded by auditd, and network traffic inspected by Snort. Together, these sources support detection, investigation and SIEM correlation.

The supplied screenshot archive contains terminal captures relating to Linux audit/Snort work and Windows Event Viewer/Sysmon captures. The evidence register below describes the visible material without treating screenshots as proof of any activity that is not actually shown.

## 2. Objectives
- Explain EDR and the value of endpoint telemetry.
- Examine Sysmon process, network, file, DNS and registry events.
- Understand auditd records and their relationship to syslog/journald.
- Configure and validate Snort rules in an authorized lab.
- Map scan-like behavior to MITRE ATT&CK T1046.
- Relate raw logs to SIEM ingestion, normalization, correlation and dashboards.

## 3. Windows endpoint telemetry
Sysmon enriches Windows visibility with process and network context. Event IDs 1, 3, 11, 13 and 22 provide pivots across process execution, connections, file creation, registry changes and DNS activity. Coverage depends on the active configuration; event absence is not proof that activity did not occur.

The supplied Windows Event Viewer screenshots show the Sysmon Operational channel and event records. When selecting evidence for publication, use individual event-detail captures for Event IDs 1, 3, 11, 13 and 22 where available. Preserve the event details pane so the event ID, timestamp, image/process and relevant fields can be read.

## 4. Linux auditing
auditd records security-relevant system activity according to configured rules. Multi-record events should be correlated using the audit message serial. EXECVE, SYSCALL, PATH, USER_AUTH and USER_LOGIN records can contribute to a host timeline. General system messages remain useful through syslog or the systemd journal.

The supplied Ubuntu terminal captures include audit package/service setup and log-oriented command output. For the final evidence set, retain the screenshot that shows the audit service state and the screenshot showing actual audit records or an ausearch result. A package installation screen alone demonstrates installation activity, not successful audit-event generation.

## 5. Network intrusion detection
Snort evaluates observed packets against configured rules. The local rules identify ICMP, SSH, HTTP and thresholded SYN-only traffic directed to HOME_NET. The T1046 rule is a scan-like indicator, not definitive attribution to Nmap. Sensor placement, interface selection, network variables and version-specific syntax affect visibility.

The supplied Ubuntu terminal captures include Snort rule/configuration and packet/alert output. Prefer evidence showing the active rule file, Snort startup/test result, and generated alert output. Keep the tested traffic within the authorized lab.

## 6. MITRE ATT&CK mapping
T1046 — Network Service Discovery describes adversary discovery of services on a network. Mapping a rule to T1046 provides behavioral context; it does not prove adversary intent. A SYN-only threshold rule detects scan-like traffic and cannot uniquely identify Nmap. Correlation with endpoint process telemetry, source context and approved scanning schedules improves confidence.

## 7. SIEM workflow
**Source → Collection/agent → Parsing → Normalization → Enrichment → Correlation/detection → Alert triage → Incident record/dashboard.**

Useful sources include Sysmon, Windows Security logs, auditd, syslog/journald, Snort alerts, DNS, firewall and network sensor records. Timestamp normalization, host identity, user context and retention are essential.

## 8. Practical evidence register
The original screenshots were supplied in the archive `WhatsApp Unknown 2026-11-06 at 10.57.03 PM.zip`. The following groups are relevant to Week 3:

| Evidence group | Supplied files | Use in report |
|---|---|---|
| Windows PowerShell / host setup | `WhatsApp Image 2026-11-04 at 1.39.26 PM.jpeg` and its `(1)`, `(2)` variants; `WhatsApp Image 2026-11-04 at 1.39.27 PM.jpeg` and its `(1)`, `(2)` variants | Supporting command-line setup and validation context; caption each screenshot according to the exact visible command/output. |
| Ubuntu auditd / Linux terminal | `2fde05cc-681f-4c2e-b8b5-e2c28393658e.jfif`, `3831668d-61b4-4ad6-91b7-891babc30976.png` | Audit package/service setup evidence. |
| Snort configuration and traffic/alert output | `765fc040-28d9-458e-9f3d-99b48edd039b.png`, `7925b70f-1bf3-40b7-bb62-a3afd2f74423.jfif`, `80883d4b-bdfc-4eb7-822c-2d11b57de397.png`, `ac347325-ceff-41d4-aa0b-e9c05cbf51d8.png`, `e756710e-f320-4b5e-8941-b6e33be061fe.jfif`, `ea354ee3-914e-4c3a-bf1a-76f80070541b.png`, `c67ea45e-38a7-4cba-a289-ed349b6db49f.png` | Rule editor/configuration and terminal traffic or alert output; use only the captures where the relevant rule or output is legible. |
| Additional terminal capture | `WhatsApp Image 2026-11-04 at 1.56.59 PM.jpeg` | Include only if its visible output directly supports a Week 3 practical. |
| Windows Event Viewer / Sysmon | `WhatsApp Image 2026-11-06 at 5.15.27 PM (1).jpeg`, `WhatsApp Image 2026-11-06 at 5.15.27 PM.jpeg`, `WhatsApp Image 2026-11-06 at 8.51.12 PM (1).jpeg`, `WhatsApp Image 2026-11-06 at 8.51.12 PM (2).jpeg`, `WhatsApp Image 2026-11-06 at 8.51.12 PM.jpeg` | Sysmon Operational channel/event evidence; select the clearest event-detail views and caption the exact Event ID visible. |

**Evidence handling:** The ZIP also contains unrelated images (including a portrait and promotional graphics); these are intentionally excluded from the technical report. The screenshots have been reviewed from the supplied archive but have **not** been uploaded as individual image files to this GitHub repository in this update. To make them viewable directly in GitHub, copy only the relevant original screenshots into `Findings/` and preserve their original content. Redact personal usernames, public IPs or other sensitive values before public release.

For every retained screenshot, add a short caption with: source VM/host, tool, event or rule, what is visibly demonstrated, and a cautious interpretation. Do not infer successful detection from a configuration screenshot alone.

## 9. LinkedIn weekly reflection
**From Endpoint Telemetry to Network Intrusion Detection | Week 3**

Security monitoring is only as effective as the visibility behind it.

This week focused on practical endpoint and network monitoring: Windows Sysmon process, network, file, DNS and registry telemetry; Linux auditd logs and service monitoring; Snort rule configuration and traffic inspection; and the relationship between scan-like network activity and MITRE ATT&CK T1046.

A key takeaway is that individual events provide useful evidence, while correlating endpoint, operating-system and network telemetry gives analysts a stronger investigative picture. Detection alerts still require context and validation before they become incident conclusions.

**Suggested media:** Attach 3–4 original screenshots directly to the LinkedIn post: one clear Sysmon Event Viewer detail, one auditd record/service capture, and one Snort rule or alert output. Avoid uploading the report PDF as the post media for this update. Tag the official DG Interns Hub page by selecting it from LinkedIn's @ mention dropdown; also use `#DGInternsHub`.

## 10. Training write-ups and access status
Separate TryHackMe and LetsDefend reports are located under `../Writeups/`. Add completion dates, personal observations and platform evidence only after completing the corresponding lesson. LetsDefend lessons that display a Premium access prompt on this account must remain marked as not completed under the free-tier scope; do not imply completion or fabricate screenshots.

## 11. Conclusion
Endpoint, operating-system audit and network telemetry provide complementary views. A SOC analyst gains stronger investigative confidence by correlating them into a timeline, validating alerts against context and separating observed facts from hypotheses.

## References
- Microsoft Sysmon: https://learn.microsoft.com/sysinternals/downloads/sysmon
- Linux Audit: https://linux.die.net/man/8/auditd
- Snort: https://www.snort.org/documents
- MITRE ATT&CK T1046: https://attack.mitre.org/techniques/T1046/
- Wazuh: https://documentation.wazuh.com/
- Splunk: https://docs.splunk.com/
