# Week 02 | Practical Procedures & Evidence Collection

## Exercise 1 — Wireshark Traffic Inspection

**Objective:** Identify selected protocol exchanges in a controlled lab capture.

**Scope:** Assigned Kali and Ubuntu lab VMs only.

**Procedure**
1. Confirm the capture interface and the lab network address range.
2. Start a capture on the relevant interface.
3. Generate permitted test traffic: ICMP reachability checks, a DNS lookup and an HTTP request to the assigned lab host where an HTTP service is available.
4. Apply display filters to isolate the relevant protocols.
5. Inspect packet direction, source/destination addresses, ports, flags and protocol fields.
6. Save the original capture in PCAPNG or PCAP format.

**Analysis requirements**
- Identify the DNS query and corresponding response, if present.
- Identify ICMP request/reply pairs, if present.
- Identify the TCP handshake where a TCP session was established.
- Identify HTTP request/response fields only if the capture contains visible HTTP.
- Explain capture limitations, including encryption, packet loss or an incorrect capture interface.

Do not claim an exchange was captured unless it is present in the saved file.

## Exercise 2 — Nmap Host and Service Assessment

**Objective:** Document authorized host-discovery and port-scanning behaviour.

**Scope:** Assigned Ubuntu and Windows lab targets only.

**Procedure**
1. Confirm the target address against the lab topology.
2. Record the Nmap version and the exact command used.
3. Perform only the discovery and scan types permitted by the exercise.
4. Save normal and XML output where required.
5. Compare the output with the corresponding packet capture, if available.

For SYN-packet review, a useful Wireshark display filter is:

```text
tcp.flags.syn == 1 && tcp.flags.ack == 0
```

**Required record:** target, timestamp, command, discovered ports, reported service/version, output filenames and any scan limitations. Do not infer a vulnerability from an open port alone.

## Exercise 3 — Windows Event Review

**Objective:** Locate and interpret selected Windows Security events in an authorized VM.

**Procedure**
1. Open Event Viewer and inspect the Security channel.
2. Filter for the assigned Event IDs.
3. Review the event's General and Details/XML views.
4. Record the timestamp, account, host, source address and relevant fields when present.
5. Correlate related events before drawing a conclusion.

Event 1102 records that the Security audit log was cleared. Any demonstration involving log clearing must be performed only in an explicitly authorized disposable VM. Never clear logs on production or third-party systems.

## Exercise 4 — PowerShell Failed-Logon Export

The following is a query template for an authorized Windows lab. It retrieves Security event 4625 and exports selected fields for review.

```powershell
$events = Get-WinEvent -FilterHashtable @{
    LogName = 'Security'
    Id      = 4625
} -ErrorAction SilentlyContinue

$events |
    Select-Object TimeCreated, Id, ProviderName, MachineName, Message |
    Export-Csv -Path .\failed-logons.csv -NoTypeInformation
```

**Validation**
- Confirm that the Security log contains matching records.
- Review the exported CSV and compare selected rows with Event Viewer.
- Treat the rendered Message as a summary; inspect event XML when structured fields are required.
- Document access-denied errors, retention limits or an empty result set.
- Do not invent counts, usernames, source addresses or timestamps.

## Evidence Register

| Evidence class | Artifact to retain | Minimum metadata |
|---|---|---|
| Packet analysis | Original PCAP/PCAPNG | Capture interface, time window, filter and observation |
| Nmap | Normal and XML output | Target scope, command, tool version and timestamp |
| Windows logging | Event Viewer screenshots or exported records | Channel, Event ID, host and time |
| PowerShell | CSV export and query used | Host, query, execution time and validation note |

Redact credentials, tokens and personal data before publication. Preserve original files separately from annotated copies.

## Reporting format

For every exercise, use the following sequence:

- **Objective and scope**
- **Environment and prerequisites**
- **Procedure and exact commands**
- **Observed evidence**
- **Technical interpretation**
- **Limitations and unresolved questions**
- **Artifact references**

Distinguish direct observations from hypotheses. Report only results supported by the captured evidence.
