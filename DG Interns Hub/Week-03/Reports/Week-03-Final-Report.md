# Technical Lab Report
## Endpoint Telemetry, Linux Auditing and Network Intrusion Detection

**Programme:** DG Interns Hub · 15 October 2026 Batch  
**Author:** Hafsa Khan  
**Reporting date:** 6 November 2026

## 1. Executive Summary
The Week 03 lab examined three complementary areas of security visibility: endpoint telemetry on Windows, audit logging on Linux, and network intrusion detection. Sysmon was used to inspect process, network, file, registry and DNS events. Ubuntu exercises covered auditd event collection and Snort rule-based alerting, while Kali Linux provided the network testing environment through Nmap.

The central operational lesson is that individual log records provide only partial context. Stronger detection and investigation come from correlating endpoint, identity, audit and network evidence.

## 2. Objectives
- Examine endpoint detection and response (EDR) telemetry and distinguish it from traditional antivirus.
- Collect and interpret Windows events using Sysmon.
- Configure Linux audit collection and inspect audit records with auditd tools.
- Understand Snort IDS operation, rule structure and alert interpretation.
- Compare signature-based and anomaly-based detection.
- Relate network service discovery behavior to MITRE ATT&CK T1046.
- Describe the flow from log collection to SIEM alert triage.

## 3. Lab Environment

| Platform | Role | Tooling |
|---|---|---|
| Windows 64-bit VM | Endpoint telemetry | Sysmon 15.22, Event Viewer, PowerShell |
| Ubuntu VM | Linux audit and network IDS | auditd, Snort |
| Kali Linux VM | Authorized network testing | Nmap 7.95 |

## 4. Windows Endpoint Telemetry — Sysmon

Sysmon was deployed with the SwiftOnSecurity configuration. The Sysmon64 service and the `Microsoft-Windows-Sysmon/Operational` event channel were verified.

**Configuration SHA-256:**  
`055FEBC600E6D7448CDF3812307275912927A62B1F94D0D933B64B294BC87162`

### 4.1 Event observations

| Event ID | Event type | Observation | Security relevance |
|---|---|---|---|
| 1 | ProcessCreate | Process creation records included Notepad and Windows/Edge processes. | Process lineage, command-line review and user attribution. |
| 3 | NetworkConnect | PowerShell initiated a TCP connection to `142.250.202.142:443`; source address recorded as `192.168.100.33`. | Process-to-network correlation and outbound connection review. |
| 11 | FileCreate | PowerShell created `C:\Users\hiras\Desktop\Week3-Sysmon-Test.ps1`. | File creation attribution and investigation of unexpected files. |
| 13 | RegistryEvent / SetValue | Microsoft Edge set a user Run-key value for its auto-launch command. | Review of startup configuration and possible persistence mechanisms. |
| 22 | DNS query | PowerShell queried `google.com`; query status was `0`. | Domain lookup attribution and DNS-based investigation. |

### 4.2 Registry event assessment
The Event ID 13 record showed a SetValue operation under the user's Run registry key. The value data referenced Microsoft Edge with the `--win-session-start` argument. Run-key modifications can be relevant to MITRE ATT&CK T1547.001, Registry Run Keys / Startup Folder. The observed Edge auto-launch entry is consistent with application startup behavior and is not, in isolation, evidence of malicious persistence.

### 4.3 Configuration consideration
The plain-text test file did not produce the expected Event ID 11 under the active SwiftOnSecurity filters, whereas the PowerShell `.ps1` test file did. This demonstrates that Sysmon visibility depends on configuration choices and file-type filters. Event absence must be interpreted in the context of collection policy.

## 5. Linux Audit Logging — auditd

The Ubuntu audit exercise focused on service validation, targeted rule configuration and event inspection using `ausearch`. The primary audit log is:

`/var/log/audit/audit.log`

Relevant audit record types include:

| Record | Purpose |
|---|---|
| SYSCALL | System-call metadata and outcome |
| EXECVE | Command arguments |
| PATH | File-system object associated with an event |
| CWD | Working directory |
| USER_AUTH | Authentication activity |
| USER_LOGIN | Login/session activity |
| CONFIG_CHANGE | Audit configuration changes |

A single audit event can consist of multiple records sharing the same audit event serial number. Correlating SYSCALL, EXECVE, PATH and CWD records provides a more complete view of the operation. The `auid` field is particularly useful for tracing the login identity associated with activity performed after privilege changes.

## 6. Network Intrusion Detection — Snort

Snort was used as a network IDS to inspect selected lab traffic and evaluate local detection rules. The local rule set covers ICMP, TCP traffic to SSH and HTTP ports, and thresholded TCP SYN activity.

| SID | Detection objective |
|---|---|
| 1000001 | ICMP traffic directed to HOME_NET |
| 1000002 | TCP traffic to destination port 22 |
| 1000003 | TCP traffic to destination port 80 |
| 1000004 | Possible SYN-based port-scan activity |

The SYN rule uses the TCP SYN flag and a source-based threshold. It is a heuristic indicator of possible network service discovery, not a unique signature of Nmap. Ordinary connections and other network tools can generate SYN packets. Reliable interpretation requires port-distribution analysis, timing, source context and corroborating telemetry.

## 7. Kali Linux — Nmap

Nmap 7.95 was used for authorized service/version identification and TCP SYN scanning in the virtual lab. The principal command patterns were:

```bash
nmap -sV -sC <authorized-lab-target> -oN service-detection.txt
sudo nmap -sS -p 1-1000 <authorized-lab-target> -oN syn-scan.txt
```

Service identification helps establish which applications are exposed. Port-scan observations can support network discovery investigations when correlated with sensor alerts, firewall records and endpoint activity. Scan output alone does not establish compromise.

## 8. MITRE ATT&CK Mapping

### T1046 — Network Service Discovery
T1046 describes discovery of services running on remote systems. A pattern of TCP SYN packets across multiple destination ports may provide a detection lead. The assessment should consider port diversity, source identity, timing, network topology and whether the activity was authorized.

### T1547.001 — Registry Run Keys / Startup Folder
Registry Run-key changes may be relevant when investigating persistence. The observed Microsoft Edge auto-launch value should be assessed in its application context rather than automatically classified as malicious.

## 9. SIEM Collection and Investigation Workflow

1. **Collection:** Gather endpoint, authentication, audit, DNS and network telemetry.
2. **Normalization:** Standardize timestamps, host identifiers, usernames and network fields.
3. **Correlation:** Link events by host, process, user, time and source/destination.
4. **Detection:** Apply rules and behavioral analytics to identify suspicious patterns.
5. **Triage:** Validate the alert against expected administrative and application activity.
6. **Investigation:** Preserve relevant records, establish scope and document confidence.
7. **Response:** Escalate or contain only when the evidence supports the action.

## 10. Key Findings and Operational Considerations
- Sysmon provides process-level context that complements standard Windows event logging.
- Event coverage depends on the selected Sysmon configuration.
- Linux audit events may span multiple records and should be correlated by their event identifier.
- Snort thresholds help control alert volume but require tuning against the environment.
- A SYN-based alert is an indicator for investigation, not proof of a specific tool or intent.
- ATT&CK mapping should describe observed behavior and should not replace evidence-based analysis.

## 11. Evidence and Reproducibility
The supporting evidence set consists of original VM screenshots, configuration captures, event records, Snort alerts and Nmap output. Evidence should preserve the relevant command, event ID, timestamp and system context. Credentials and unrelated personal information should be excluded from published captures.

## 12. Conclusion
The lab demonstrates how endpoint telemetry, Linux audit records and network IDS alerts complement one another. Sysmon helps establish what ran on a Windows endpoint; auditd records security-relevant Linux activity; Snort provides visibility into network patterns; and Nmap supplies controlled test traffic for evaluating detection. Correlation across these sources provides a more reliable basis for SOC investigation than any single event in isolation.
