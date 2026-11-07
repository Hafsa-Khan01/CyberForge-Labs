# Week 03 — SOC Analyst Quick Reference
## Endpoint Telemetry, Linux Auditing and Network Detection

A practical reference for reviewing Windows Sysmon, Windows Security events, Linux auditd, Snort alerts and Nmap validation activity in an authorized lab.

---

## 1. Windows Security Event IDs

| Event ID | Provider | Meaning | Initial analyst checks |
|---|---|---|---|
| 4624 | Security | Successful logon | Account, logon type, source address, workstation, time |
| 4625 | Security | Failed logon | Account, failure reason, source address, repeated attempts |
| 4688 | Security | Process creation (if audit policy enables it) | New process, creator process, command line if configured |
| 4720 | Security | User account created | Target account, subject/actor, host, surrounding events |

**Logon type reminders for Event 4624/4625**

| Logon type | Common meaning |
|---|---|
| 2 | Interactive |
| 3 | Network |
| 4 | Batch |
| 5 | Service |
| 7 | Unlock |
| 10 | RemoteInteractive (commonly RDP) |

Interpret logon type in context; it is not a verdict by itself.

## 2. Sysmon Event IDs

| Event ID | Event | Investigation value |
|---|---|---|
| 1 | Process Create | Image, command line, parent image, user, hashes, process GUID |
| 3 | Network Connection | Process, protocol, source/destination IP and port; depends on configuration |
| 7 | Image Load | DLL/module path and process; can be high-volume and is configuration-dependent |
| 11 | File Create | Target filename, process and timestamp |
| 12 | Registry object create/delete | Registry key activity |
| 13 | Registry value set | Registry path, value name and details |
| 22 | DNS Query | Query name, requesting process and result context |

**Useful Event Viewer path**

Applications and Services Logs → Microsoft → Windows → Sysmon → Operational

**PowerShell — recent Sysmon events**

```powershell
Get-WinEvent -LogName "Microsoft-Windows-Sysmon/Operational" -MaxEvents 30 |
  Select-Object TimeCreated, Id, ProviderName, Message |
  Format-List
```

**Filter selected Event IDs**

```powershell
$ids = 1,3,11,13,22
Get-WinEvent -FilterHashtable @{
  LogName = "Microsoft-Windows-Sysmon/Operational"
  Id = $ids
  StartTime = (Get-Date).AddHours(-24)
} | Select-Object TimeCreated, Id, Message
```

**Check the Sysmon service**

```powershell
Get-Service Sysmon*
```

Analyst note: Event ID 13 is not automatically malicious. Validate the exact registry path/value, writing process, signer, user, timing and related process/network events. A Run-key modification may be legitimate software auto-start behavior.

## 3. Linux auditd

### Common audit record types

| Record | Purpose |
|---|---|
| SYSCALL | System-call metadata, result, process and identity fields |
| EXECVE | Command and argument data |
| PATH | Filesystem objects associated with the event |
| CWD | Working directory |
| USER_AUTH | Authentication-related activity |
| USER_LOGIN | Login/session-related activity |
| CONFIG_CHANGE | Audit configuration or rule changes |

Records belonging to one audit event commonly share a serial identifier, shown in the audit message header as `msg=audit(timestamp:serial)`. Correlate the records by that identifier.

### Service and rule checks

```bash
sudo systemctl status auditd
sudo auditctl -s
sudo auditctl -l
```

### Search recent audit records

```bash
sudo ausearch -ts recent
sudo ausearch -m USER_AUTH,USER_LOGIN
sudo ausearch -m SYSCALL,EXECVE,PATH,CWD -ts today
```

### Read the audit log

```bash
sudo less /var/log/audit/audit.log
```

### Example temporary watch rule

Use only in a disposable/authorized lab; this adds a live rule and is not persistent across reboot unless saved in the system's audit rules configuration.

```bash
sudo auditctl -w /etc/passwd -p wa -k identity_file_watch
sudo ausearch -k identity_file_watch -i
```

Remove the temporary watch when finished:

```bash
sudo auditctl -W /etc/passwd -k identity_file_watch
```

Analyst note: auditd service status, installed packages and loaded rules are different checks. A running service does not by itself prove that the expected event was recorded. Confirm with `ausearch` and inspect the matching records.

## 4. Snort — rule structure and lab SIDs

### Rule anatomy

```
action protocol source_ip source_port -> destination_ip destination_port (options)
```

| Option | Meaning |
|---|---|
| alert | Generate an alert |
| msg | Human-readable alert description |
| sid | Unique local rule identifier |
| rev | Rule revision |
| classtype | Alert classification |
| content | Match a byte/string pattern |
| flags | Match TCP flags |
| threshold | Rate/threshold behavior |

### Local lab SIDs

| SID | Lab rule purpose | Analyst interpretation |
|---|---|---|
| 1000001 | ICMP echo traffic | Ping/ICMP visibility |
| 1000002 | TCP traffic to port 22 | SSH-destined traffic |
| 1000003 | TCP traffic to port 80 | HTTP-destined traffic |
| 1000004 | Thresholded SYN activity | Scan-like connection pattern |

### Validate configuration and run mode

Commands vary by Snort version and local configuration. Confirm the installed version and configuration path before running:

```bash
snort -V
snort -T -c /etc/snort/snort.conf
```

A typical interface-based console run (adjust interface and configuration path for the lab):

```bash
sudo snort -A console -q -c /etc/snort/snort.conf -i eth0
```

### Rule-writing checks

- Use a unique SID in the local SID range and increment `rev` when changing a rule.
- Confirm the rule file is included by the active configuration.
- Test configuration before interpreting alerts.
- Check HOME_NET, interface, direction, ports and threshold values.
- Validate rule behavior with controlled traffic and inspect the alert output.

Analyst note: a SYN threshold can flag scan-like activity; it cannot uniquely attribute the traffic to Nmap or prove malicious intent. A port-based alert is an indicator, not proof of an exploit.

## 5. Nmap — authorized lab validation

### Identify local interfaces and routes

```bash
ip -br addr
ip route
```

### Host discovery and service identification

```bash
nmap -sn <authorized-subnet>
nmap -sV <authorized-target>
nmap -sV -p 22,80,443 <authorized-target>
```

Use only against systems and ranges for which you have explicit authorization. Keep scan scope narrow and document the target, time, options and purpose.

**Correlation idea:** compare the scan time and target ports with Snort alerts and endpoint/network telemetry. A matching timestamp supports correlation but does not, by itself, establish attribution.

## 6. Fast SOC investigation workflow

1. **Triage:** record alert name, sensor, timestamp, severity and rule/SID.
2. **Scope:** identify affected host, account, source/destination addresses and ports.
3. **Process context:** inspect process image, command line, parent process, user and hash where available.
4. **Correlate:** compare Sysmon, Windows Security, auditd, DNS, firewall and Snort records within a consistent time window.
5. **Validate:** determine whether the activity was expected, authorized and reproducible.
6. **Assess:** document benign explanations, gaps in telemetry and confidence level.
7. **Respond:** follow the approved escalation/containment procedure; preserve original logs and timestamps.
8. **Report:** state observed facts, interpretation, impact, evidence and recommended next action.

## 7. MITRE ATT&CK references

| Technique | Name | Use only when evidence supports it |
|---|---|---|
| T1046 | Network Service Discovery | Service/port discovery behavior is observed |
| T1110 | Brute Force | Repeated authentication attempts support the pattern |
| T1136 | Create Account | Evidence shows account creation behavior |
| T1547.001 | Registry Run Keys / Startup Folder | Relevant startup persistence location and behavior are verified |

A technique mapping describes observed behavior; it does not establish attacker identity or malicious intent.

## 8. Evidence and reporting checklist

- [ ] Record date/time and timezone; preserve original timestamps.
- [ ] Include host, user, source and destination details where visible.
- [ ] Capture the exact command, rule or filter used.
- [ ] Distinguish configuration evidence from successful event/alert evidence.
- [ ] Redact credentials, tokens and unrelated personal data.
- [ ] State limitations and alternative explanations.
- [ ] Link each finding to its original evidence file.

## 9. Common pitfalls

- Missing Sysmon events may reflect configuration gaps, not absence of activity.
- Windows Security events depend on the relevant audit policy.
- auditd events can span multiple records; do not treat each line as a separate action.
- Installed auditd package, active service, loaded rules and recorded audit events are separate proof points.
- Snort rules may be broad and noisy; validate the active ruleset and sensor configuration.
- SYN-based scan detection does not uniquely identify Nmap.
- A registry Run-key write is not automatically malicious.
- Do not claim an alert, event or scan occurred unless the retained evidence demonstrates it.

---

**Reference links**

- Sysmon documentation: https://learn.microsoft.com/sysinternals/downloads/sysmon
- Windows Security auditing: https://learn.microsoft.com/windows/security/threat-protection/auditing/basic-audit-logon-events
- Linux audit userspace: https://github.com/linux-audit/audit-userspace
- Snort documentation: https://docs.snort.org/
- Nmap reference guide: https://nmap.org/book/man.html
- MITRE ATT&CK T1046: https://attack.mitre.org/techniques/T1046/
- MITRE ATT&CK T1110: https://attack.mitre.org/techniques/T1110/
- MITRE ATT&CK T1136: https://attack.mitre.org/techniques/T1136/
- MITRE ATT&CK T1547.001: https://attack.mitre.org/techniques/T1547/001/
