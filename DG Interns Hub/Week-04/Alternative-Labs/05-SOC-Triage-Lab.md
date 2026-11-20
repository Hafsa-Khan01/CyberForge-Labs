# Lab 05 — SOC Alert Triage Exercises

## Objective
Apply a repeatable investigation process to authentication, endpoint and network alerts.

## Triage workflow
1. Validate alert integrity and data source.
2. Identify affected asset, user, source and time range.
3. Establish a baseline and check allowlists/change windows.
4. Pivot across related events and telemetry.
5. Determine scope and likely impact.
6. Assign a verdict with confidence and supporting evidence.
7. Escalate or contain under the organisation's approved process.
8. Record actions, timestamps and follow-up requirements.

## Case A — Repeated authentication failures
**Initial hypothesis:** password guessing or brute-force activity.

**First checks**
- Count failures by source, destination and account.
- Determine whether failures are distributed across accounts or concentrated on one account.
- Check for a subsequent successful logon.
- Compare source with approved VPN, scanner and administrator ranges.
- Review MFA, lockout and authentication policy events.

**Possible verdicts:** expected user error; misconfigured service; authorised test; suspicious password guessing; confirmed compromise only when corroborating evidence supports it.

## Case B — Suspicious PowerShell execution
**Initial hypothesis:** script-based execution requiring review.

**First checks**
- Inspect full command line and parent process.
- Identify user, host and execution time.
- Check script origin, signature and file hash where available.
- Correlate with network connections, file writes and persistence events.
- Compare with software deployment and administrative activity.

**Caution:** PowerShell is a legitimate administration tool. Do not label every PowerShell event malicious.

## Case C — Port scan or unusual network connection
**Initial hypothesis:** discovery activity (MITRE ATT&CK T1046).

**First checks**
- Identify source and destination systems.
- Review connection/flow logs and target port distribution.
- Determine whether the source is an approved vulnerability scanner.
- Correlate with endpoint process telemetry and change tickets.
- Establish whether the activity was limited to the authorised lab.

**Caution:** A SYN scan result or network connection count alone does not prove exploitation.

## Triage note format
Use one copy per actual alert in `../Findings/Triage-01.md`, `Triage-02.md` and `Triage-03.md`:
- Alert ID and source:
- First observed / timezone:
- Affected asset and account:
- Source and destination:
- Evidence reviewed:
- Related events:
- Baseline / allowlist checks:
- Assessment and confidence:
- Verdict:
- Actions taken (only actions actually performed):
- Escalation / next step:
- Analyst notes:

These case studies are investigation guides. They are not records of real alerts unless populated from the user's actual SIEM output.
