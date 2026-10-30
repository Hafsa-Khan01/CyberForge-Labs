# Practical Write-up — PowerShell Failed-Logon Hunting

## Objective
Query Windows Security event 4625 and export relevant records for review.

## Example
```powershell
$events = Get-WinEvent -FilterHashtable @{
    LogName = 'Security'
    Id = 4625
} -ErrorAction SilentlyContinue

$events |
    Select-Object TimeCreated, Id, ProviderName, MachineName, Message |
    Export-Csv -Path .\failed-logons.csv -NoTypeInformation
```

## Analysis Workflow
1. Confirm the query ran against the intended authorized host.
2. Preserve the original CSV export.
3. Parse account and source fields from event details.
4. Group failures by account and source only after validating parsed fields.
5. Compare repeated failures with normal user activity and related events.

## Limitations
The Message field varies by language and event version. For robust automation, parse event XML and validate field names. Do not invent counts or claim an account was targeted unless the exported records support it.
