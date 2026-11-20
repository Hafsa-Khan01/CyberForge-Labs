# Week 04 — Detection Engineering

## SPL searches
1. [Failed logons per user — EventCode 4625](01-Failed-Logons-Per-User.spl)
2. [PowerShell process creation — Sysmon Event ID 1](02-PowerShell-Process-Creation.spl)
3. [New user account creation — EventCode 4720](03-New-User-Account-Creation.spl)
4. [SSH failures per source IP](04-SSH-Failures-Per-Source-IP.spl)
5. [Rare parent-child process pairs](05-Rare-Parent-Child-Process-Pairs.spl)

- [Custom Wazuh rule starter](wazuh-local-rules.xml)
- [Scheduled alerts and dashboard record](Scheduled-Alerts-and-Dashboard.md)

Verify field names against actual events. Confirm the SSH decoder and parent rule ID on the installed Wazuh manager before enabling the frequency rule. Test with `wazuh-logtest` and verify the end-to-end alert separately.
