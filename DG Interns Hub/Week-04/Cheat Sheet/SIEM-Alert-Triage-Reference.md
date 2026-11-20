# SIEM Alert — Likely Cause — First Check

| SIEM alert | Likely cause(s) | First check |
|---|---|---|
| Windows failed logons (4625) | Password guessing, user error, stale credentials | Source IP, target account, logon type and nearby success |
| SSH authentication failures | Password guessing, scanner, typo or service issue | Source IP, username, timestamps and subsequent success |
| New Windows user (4720) | Approved onboarding or unauthorized account creation | Creator, target account, host and change approval |
| PowerShell process created | Admin script, automation or suspicious execution | Command line, parent process, user and script source |
| Unusual parent-child process | Legitimate updater or suspicious process chain | Process tree, signer, path and command line |
| Wazuh FIM alert | File change, package update, admin action or tampering | File path, old/new hash, user and change window |
| SYN scan alert | Approved inventory, vulnerability scan or reconnaissance | Source, destination ports, approval and packet pattern |
| Multiple alerts from one host | Compromise, misconfiguration or noisy agent | Correlate timestamps and inspect raw events |
| Agent disconnected | Host offline, service stopped or network issue | Endpoint service, manager reachability and last keep-alive |
| Log ingestion stopped | Collector failure, wrong input, permissions or network issue | Source channel/file, collector status and last event time |
| Sudden event-volume spike | Attack, scheduled job, log loop or duplicates | Source, sourcetype, host and baseline volume |
| Missing source IP field | Parser/decoder issue or unsupported log format | Raw event and field extraction |

A likely cause is not a verdict. Validate the context and document evidence before classification.
