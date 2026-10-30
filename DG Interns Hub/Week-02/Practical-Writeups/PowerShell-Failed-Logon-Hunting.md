# Practical Investigation — PowerShell Failed-Logon Hunting

## 1. Objective

Retrieve Windows Security Event ID 4625 records from an authorized lab host, preserve the results in CSV format and review the records for authentication patterns that merit further investigation.

## 2. Event context

**Event ID 4625** records a failed logon. It is useful for investigating authentication failures, but a single event does not establish malicious activity. Interpret it alongside the account, logon type, source information, time window, host role and related events.

## 3. Collection procedure

Run PowerShell with the permissions required to read the Security log. The following is a reusable query template; replace the time window or output path only as required by the lab.

```powershell
$events = Get-WinEvent -FilterHashtable @{
    LogName = 'Security'
    Id      = 4625
} -ErrorAction SilentlyContinue

$events |
    Select-Object TimeCreated, Id, ProviderName, MachineName, Message |
    Export-Csv -Path .\failed-logons.csv -NoTypeInformation
```

For a bounded investigation, add `StartTime` and `EndTime` to the filter using the actual investigation window. Record the exact query used.

## 4. Validation

1. Confirm the command ran on the intended authorized host.
2. Check whether matching records were returned.
3. Open the CSV and verify its columns and timestamps.
4. Compare selected records with Event Viewer.
5. Inspect the event's Details/XML view when structured fields are required.
6. Preserve the original export before creating filtered or annotated copies.

An empty result is a valid observation: it means the query returned no matching records in the accessible log for that execution. It does not prove that no failed logons occurred outside the retained log, time window or collection permissions.

## 5. Investigation and analysis

For each relevant record, examine the fields that are actually present:

- TimeCreated and the host that recorded the event
- Target account and domain
- Logon type
- Workstation and source network address, where recorded
- Status and sub-status codes
- Authentication package and process details, where present

Look for patterns such as repeated failures against one account, failures across multiple accounts, unusual source systems or activity outside expected operating hours. Validate these patterns against the host's normal role and authorized activity before escalating.

Do not infer password spraying, brute force or account targeting from a raw event count alone. Such a conclusion requires a defined time window, validated account/source fields, supporting context and consideration of benign causes such as mistyped credentials or stale services.

## 6. Data handling and limitations

The rendered `Message` field can vary by Windows version and display language. For repeatable parsing, inspect the event XML and validate the field names before building automation. Event availability depends on audit policy, log retention, permissions and system configuration.

Redact usernames, internal addresses and other sensitive values before publishing evidence externally.

## 7. Evidence register

| Artifact | What it demonstrates |
|---|---|
| PowerShell command screenshot | Query and execution context |
| Event Viewer screenshot | Source event details |
| Original CSV export | Records returned by the query |
| Analysis notes | Interpretation, correlation and limitations |

Reference only artifacts that actually exist in the evidence folder.

## 8. Conclusion

Summarize the query scope, whether matching records were returned, the fields validated and any patterns supported by the records. Clearly separate confirmed observations from hypotheses. Do not fabricate event counts, accounts, source addresses or timestamps.
