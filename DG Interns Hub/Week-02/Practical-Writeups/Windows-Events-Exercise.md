# Practical Write-up — Windows Event Investigation

## Objective
Review selected Windows Security and System events in an authorized disposable VM and understand their investigative context.

## Events
4624 successful logon; 4625 failed logon; 4720 account created; 4732 local security group membership changed; 4697 service installed in the Security log; 7045 service installed in the System log; 1102 Security audit log cleared.

## Procedure
1. Open Event Viewer and inspect Security and System logs.
2. Filter for assigned event IDs and time window.
3. Record timestamp, host, account, source/workstation and related events.
4. Correlate with expected lab actions.
5. Export or capture evidence with sensitive values redacted.

## Interpretation
An event ID is a starting point, not a verdict. Check actor, target, host, source, timing and surrounding activity. Event 1102 is an audit-integrity signal that requires contextual investigation.

## Safety
Any demonstration that intentionally clears logs must occur only in an explicitly authorized disposable VM. Never clear logs on production or third-party systems.
