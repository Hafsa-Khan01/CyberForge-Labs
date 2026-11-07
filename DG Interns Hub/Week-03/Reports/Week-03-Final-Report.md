# Technical Lab Report
## Endpoint Telemetry, Linux Auditing and Network Intrusion Detection

**Programme:** DG Interns Hub · Week 03  
**Reporting date:** 7 November 2026

## 1. Executive Summary
This report documents the Week 03 work across three complementary security-visibility layers: Windows endpoint telemetry, Linux audit logging and network intrusion detection. Sysmon provides process, network, file, registry and DNS context. Linux auditd records security-relevant host activity, while Snort evaluates traffic against configured detection rules. Kali Linux and Nmap support controlled network testing within an authorized lab.

The central operational takeaway is that individual events provide only part of an investigative picture. Correlating endpoint, host-audit and network telemetry produces stronger context and supports more defensible triage decisions.

## 2. Objectives
- Examine endpoint detection and response telemetry and its relationship to traditional antivirus.
- Collect and interpret Windows events using Sysmon.
- Work with Linux audit logging and understand audit records and service validation.
- Configure Snort rules and interpret generated alerts.
- Distinguish signature-based detection from anomaly-based detection.
- Map network service discovery behavior to MITRE ATT&CK T1046.
- Relate raw telemetry to SIEM collection, normalization, correlation and alert triage.

## 3. Lab Environment

| Platform | Role | Tooling |
|---|---|---|
| Windows VM | Endpoint telemetry | Sysmon 15.22, Event Viewer, PowerShell |
| Ubuntu VM | Linux auditing and network IDS | auditd, Snort, Linux utilities |
| Kali Linux VM | Authorized network testing | Nmap 7.95 |

All scanning and traffic-generation activity described here is scoped to the authorized lab environment.

## 4. Windows Endpoint Telemetry — Sysmon
Sysmon was deployed with the SwiftOnSecurity configuration. The Sysmon64 service and the `Microsoft-Windows-Sysmon/Operational` event channel were verified.

**Configuration SHA-256:**
`055FEBC600E6D7448CDF3812307275912927A62B1F94D0D933B64B294BC87162`

### 4.1 Event observations

| Event ID | Event type | Observation | Security relevance |
|---|---|---|---|
| 1 | ProcessCreate | Process creation records included Notepad and Windows/Edge processes. | Process lineage, command-line review and user attribution. |
| 3 | NetworkConnect | PowerShell initiated a TCP connection to `142.250.202.142:443`; the source was a private lab address. | Process-to-network correlation and outbound connection review. |
| 11 | FileCreate | PowerShell created a test `.ps1` file in the desktop directory. | File-creation attribution and investigation of unexpected files. |
| 13 | RegistryEvent / SetValue | Microsoft Edge set a user Run-key value for its auto-launch command. | Review of startup configuration and possible persistence mechanisms. |
| 22 | DNS query | PowerShell queried `google.com`; the query status was `0`. | Domain lookup attribution and DNS-based investigation. |

### 4.2 Registry event assessment
The Event ID 13 record showed a SetValue operation under the user's Run registry key. The value data referenced Microsoft Edge with the `--win-session-start` argument. Run-key modifications can be relevant to MITRE ATT&CK T1547.001, Registry Run Keys / Startup Folder. The observed Edge auto-launch value is consistent with application startup behavior and is not, by itself, evidence of malicious persistence.

### 4.3 Configuration consideration
The plain-text test file did not produce the expected Event ID 11 under the active SwiftOnSecurity filters, whereas the PowerShell test file did. This illustrates that Sysmon visibility depends on configuration choices and file-type filters. Event absence must be interpreted in the context of the collection policy.

## 5. Linux Audit Logging — auditd
The Ubuntu work covered audit package/service checks, Linux logging concepts and audit-record interpretation. The primary audit log path is:

`/var/log/audit/audit.log`

| Record type | Purpose |
|---|---|
| SYSCALL | System-call metadata and outcome |
| EXECVE | Command arguments |
| PATH | File-system object associated with an event |
| CWD | Working directory |
| USER_AUTH | Authentication activity |
| USER_LOGIN | Login/session activity |
| CONFIG_CHANGE | Audit configuration changes |

A single audit event can contain multiple records sharing the same audit event serial number. Correlating SYSCALL, EXECVE, PATH and CWD records provides a more complete view of an operation. The `auid` field can help trace the login identity associated with activity performed after privilege changes.

**Evidence note:** The GitHub evidence set currently includes auditd package-installation output and service/systemd status captures. One service-unit capture reports `auditd.service` as not found at the time it was recorded. These published images do not independently demonstrate successful audit-event collection or an `ausearch` result. The practical workflow and concepts are documented here, while the evidence index is intentionally limited to what the uploaded screenshots show.

## 6. Network Intrusion Detection — Snort
Snort was used to inspect selected lab traffic and evaluate local detection rules. The local rule set covers ICMP, TCP traffic to SSH and HTTP ports, and thresholded TCP SYN activity.

| SID | Detection objective |
|---|---|
| 1000001 | ICMP traffic directed to HOME_NET |
| 1000002 | TCP traffic to destination port 22 |
| 1000003 | TCP traffic to destination port 80 |
| 1000004 | Possible SYN-based port-scan activity |

The SYN rule uses the TCP SYN flag and a source-based threshold. It is a heuristic indicator of possible network service discovery, not a unique signature of Nmap. Ordinary connections and other network tools can also generate SYN packets. Reliable interpretation requires port-distribution analysis, timing, source context and corroborating telemetry.

The published screenshots show local-rule configuration and generated TCP scan-like alert output. A rule configuration screenshot alone does not prove successful rule loading; alert output provides the stronger evidence that matching traffic was observed.

## 7. Kali Linux — Nmap
Nmap 7.95 supports authorized service/version identification and TCP SYN scanning in the virtual lab. Example command patterns:

```bash
nmap -sV -sC <authorized-lab-target> -oN service-detection.txt
sudo nmap -sS -p 1-1000 <authorized-lab-target> -oN syn-scan.txt
```

Service identification helps establish which applications are exposed. Port-scan observations can support network discovery investigations when correlated with sensor alerts, firewall records and endpoint activity. Scan output alone does not establish compromise.

## 8. MITRE ATT&CK Mapping

### T1046 — Network Service Discovery
T1046 describes discovery of services running on remote systems. A pattern of TCP SYN packets across multiple destination ports may provide a detection lead. Assessment should consider port diversity, source identity, timing, network topology and whether the activity was authorized.

### T1547.001 — Registry Run Keys / Startup Folder
Registry Run-key changes may be relevant when investigating persistence. The observed Microsoft Edge auto-launch value should be assessed in its application context rather than automatically classified as malicious.

## 9. SIEM Collection and Investigation Workflow
1. **Collection:** Gather endpoint, authentication, audit, DNS and network telemetry.
2. **Normalization:** Standardize timestamps, host identifiers, usernames and network fields.
3. **Correlation:** Link events by host, process, user, time and source/destination.
4. **Detection:** Apply rules and behavioral analytics to identify suspicious patterns.
5. **Triage:** Validate alerts against expected administrative and application activity.
6. **Investigation:** Preserve relevant records, establish scope and document confidence.
7. **Response:** Escalate or contain only when the evidence supports the action.

## 10. Key Findings
- Sysmon adds process-level context that complements standard Windows event logging.
- Event coverage depends on the selected Sysmon configuration.
- Linux audit events can span multiple records and should be correlated by their event identifier.
- Snort thresholds help control alert volume but require tuning against the environment.
- A SYN-based alert is an indicator for investigation, not proof of a specific tool or intent.
- ATT&CK mapping describes observed behavior; it does not replace evidence-based analysis.
- Correlation across endpoint, host-audit and network telemetry provides stronger investigative context than any single event in isolation.

## 11. Evidence Register
Original screenshots currently published in [Evidence](../Evidence/) include:

| Area | Published evidence |
|---|---|
| Windows / Sysmon | Installation/configuration, service verification and selected Event ID 1, 11, 13 and 22 views |
| Kali / Nmap | Network connectivity verification and service/version scan output |
| Ubuntu / Snort | Local rule configuration and TCP scan-like alert output |
| Ubuntu / auditd | Package installation output and service/systemd status captures |
| Linux utilities | strace system-call output |

See the [Evidence README](../Evidence/README.md) for the exact filenames and interpretation notes. Evidence captions should describe the visible command, event, rule or output and avoid implying more than the capture demonstrates. Credentials and unrelated personal information should not be included in public screenshots.

## 12. Training Access Status
The TryHackMe room reports are maintained under [Writeups/TryHackMe](../Writeups/TryHackMe/). The assigned LetsDefend lessons displayed a Premium access requirement and were not completed; this status is recorded under [Writeups/LetsDefend](../Writeups/LetsDefend/). No Premium-only lesson completion is claimed.

## 13. Conclusion
Endpoint telemetry, Linux audit records and network IDS alerts provide complementary visibility. Sysmon helps establish what ran on a Windows endpoint; auditd records security-relevant Linux activity; Snort provides visibility into network patterns; and Nmap supplies controlled test traffic for evaluating detection. Correlation across these sources, followed by validation against operational context, provides a more reliable basis for SOC investigation than any single event in isolation.

## Technical References
- [Microsoft Sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)
- [Linux Audit Documentation](https://github.com/linux-audit/audit-documentation)
- [Snort Documentation](https://docs.snort.org/)
- [Nmap Reference Guide](https://nmap.org/book/man.html)
- [MITRE ATT&CK T1046](https://attack.mitre.org/techniques/T1046/)
- [MITRE ATT&CK T1547.001](https://attack.mitre.org/techniques/T1547/001/)
