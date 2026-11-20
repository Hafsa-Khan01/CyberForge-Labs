# Week 04 — SIEM in Practice
## 10-Slide Presentation Plan

### Slide 1 — Title
**SIEM in Practice: Splunk, Wazuh and Log Ingestion**  
DG Interns Hub · Week 04  
Use a clean SIEM dashboard visual and the actual lab environment name.

### Slide 2 — Objectives and scope
- Centralise Windows and Linux security telemetry.
- Explore Splunk searches and Wazuh monitoring.
- Build and validate detection logic.
- Practice alert triage.
- State the authorised lab scope and tool versions.

### Slide 3 — SIEM architecture
Show the flow: endpoint/network sources → agent/forwarder/syslog → parsing and normalisation → index/search → correlation and alert → SOC triage. Explain why time synchronisation and field quality matter.

### Slide 4 — Splunk and the lab index
Show the actual Splunk instance and `lab` index. Include version and index screenshot. Explain the difference between a saved search and an alert.

### Slide 5 — Log ingestion
Show Windows Security, Sysmon and Ubuntu authentication telemetry. Include one genuine event screenshot for each source and identify host, source, sourcetype and timestamp.

### Slide 6 — Wazuh monitoring
Explain manager, agents, decoders and rules. Show actual manager/agent status and the monitored FIM path.

### Slide 7 — FIM validation
Show the controlled file change and corresponding Wazuh alert. Explain what changed and why the alert is meaningful. Use the actual event, not a mock output.

### Slide 8 — Attack-to-alert validation
Summarise the authorised SSH authentication test (T1110) and Nmap SYN discovery test (T1046). Show source/target scope, relevant event fields and detection evidence. Redact credentials and sensitive identifiers.

### Slide 9 — Detection engineering
Present the five SPL use cases, two scheduled alerts, four-panel dashboard and custom Wazuh rule. Include the verified parent rule ID and actual `wazuh-logtest` output. Note field dependencies and tuning.

### Slide 10 — SOC triage and lessons
Summarise three real triage cases, verdicts and next steps. Close with lessons about telemetry quality, baselines, false positives and evidence-led investigation.

## Presenter notes
- Keep screenshots large enough to read.
- Add a short caption explaining what each screenshot proves.
- Use the same timezone throughout.
- Never show passwords, tokens, private keys or personal data.
- Do not claim the premium TryHackMe rooms were completed; mention the room-free alternatives if relevant.
- If an item was not executed or cannot be evidenced, label it as documented/design work rather than completed practical work.

## Export checks
Export to PDF or PPTX, reopen the exported file, verify slide count, readability, links and image quality. The outline itself is not an exported presentation.
