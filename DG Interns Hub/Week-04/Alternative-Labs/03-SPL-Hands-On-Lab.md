# Lab 03 — Splunk SPL Hands-On Exercises

## Objective
Use Search Processing Language (SPL) to filter, transform, aggregate and visualise security events.

> **Important:** The searches below are starting patterns. Confirm the actual index, sourcetype and field names in the lab before relying on them. Windows field names can differ depending on XML rendering and add-ons.

## 1. Confirm available data

```spl
index=lab earliest=-24h
| stats count by host source sourcetype
| sort - count
```

## 2. Failed Windows logons

```spl
index=lab (EventCode=4625 OR EventID=4625)
| stats count as failures values(host) as hosts by user
| sort - failures
```

## 3. Failed logons by source IP

```spl
index=lab (EventCode=4625 OR EventID=4625)
| stats count as failures by src_ip
| sort - failures
```

If the source IP field has another name in the actual event, substitute it after inspecting raw events.

## 4. Successful logons

```spl
index=lab (EventCode=4624 OR EventID=4624)
| stats count by user Logon_Type host
| sort - count
```

## 5. PowerShell process activity (Sysmon)

```spl
index=lab (EventCode=1 OR EventID=1) (Image="*powershell.exe" OR process_name="powershell.exe")
| table _time host User Image CommandLine ParentImage
| sort - _time
```

## 6. New local user creation

```spl
index=lab (EventCode=4720 OR EventID=4720)
| table _time host SubjectUserName TargetUserName
| sort - _time
```

## 7. SSH authentication failures

```spl
index=lab sourcetype=linux_secure ("Failed password" OR "authentication failure")
| stats count as failures by host
| sort - failures
```

## 8. SSH failures by source address

```spl
index=lab sourcetype=linux_secure "Failed password"
| rex "from (?<src_ip>\d{1,3}(?:\.\d{1,3}){3})"
| stats count as failures by src_ip
| sort - failures
```

## 9. Top source addresses

```spl
index=lab sourcetype=linux_secure "Failed password"
| rex "from (?<src_ip>\d{1,3}(?:\.\d{1,3}){3})"
| top limit=10 src_ip
```

## 10. Authentication trend

```spl
index=lab (EventCode=4625 OR EventID=4625)
| timechart span=5m count
```

## 11. Process events by image

```spl
index=lab (EventCode=1 OR EventID=1)
| stats count by Image ParentImage
| sort - count
```

## 12. Rare process-image pairs

```spl
index=lab (EventCode=1 OR EventID=1)
| stats count by ParentImage Image
| where count < 5
| sort count
```

## 13. Network connections (Sysmon Event ID 3)

```spl
index=lab (EventCode=3 OR EventID=3)
| stats count by Image DestinationIp DestinationPort Protocol
| sort - count
```

## 14. Data quality check

```spl
index=lab earliest=-24h
| eval has_host=if(isnull(host),0,1)
| stats count sum(has_host) as events_with_host
```

## SPL command reference
| Command | Purpose |
|---|---|
| `search` | Filter events |
| `where` | Filter using expressions |
| `fields` | Include/exclude fields |
| `table` | Display selected fields |
| `stats` | Aggregate events |
| `eventstats` | Add aggregate values to each event |
| `streamstats` | Calculate running/windowed values |
| `timechart` | Time-series aggregation |
| `chart` | Pivot-style aggregation |
| `top` | Most frequent values |
| `rare` | Least frequent values |
| `sort` | Order results |
| `dedup` | Remove duplicate field values |
| `eval` | Create or transform fields |
| `rex` | Extract fields with regex |
| `lookup` | Enrich events from lookup data |
| `bin` | Bucket numeric/time values |
| `fillnull` | Replace null values |
| `head` | Limit returned events |

## Exercise record
For each search, record the actual time range, result count, fields used, one observation and one limitation. Save screenshots of executed searches. Do not claim a detection fired merely because its SPL syntax is present in this repository.
