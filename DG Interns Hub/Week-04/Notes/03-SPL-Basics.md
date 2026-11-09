# 3. Splunk Search Processing Language (SPL) Basics

## What is SPL?
Search Processing Language (SPL) is Splunk's query language. Analysts use it to retrieve events, filter results, calculate statistics, create fields, summarize activity over time and extract values from raw event text.

Examples below assume events are in an index named lab. Field names depend on the actual sourcetype and parsing configuration. Inspect sample events before relying on a field in a detection.

## Core commands

| Command | Purpose | Example |
|---|---|---|
| search | Retrieves matching events | index=lab EventCode=4625 |
| where | Filters results using an expression | ... | where count >= 5 |
| stats | Calculates aggregates | ... | stats count by user |
| table | Displays selected fields | ... | table _time user src_ip |
| eval | Creates or updates a field | ... | eval event_type="Failed Logon" |
| timechart | Aggregates values into time buckets | ... | timechart span=5m count |
| rex | Extracts fields with regular expressions | ... | rex field=_raw "user=(?<user>[^ ]+)" |

## 1. search
Selects events matching terms or field conditions.

    index=lab EventCode=4625

This searches the lab index for Windows Event ID 4625, commonly associated with failed logons. Confirm that the data source uses EventCode; field names vary.

## 2. where
Filters results using an expression, often after aggregation.

    index=lab EventCode=4625
    | stats count by user
    | where count >= 5

This finds users with at least five matching events in the selected time range. It does not by itself enforce a five-minute window.

## 3. stats
Calculates summary values.

    index=lab EventCode=4625
    | stats count by user, src_ip

This counts events for each user and source IP combination.

## 4. table
Displays only selected fields.

    index=lab EventCode=4625
    | table _time host user src_ip EventCode

If a field is missing or named differently, the column may be blank. Validate field extraction.

## 5. eval
Creates or updates a field.

    index=lab EventCode=4625
    | eval event_type="Failed Logon"
    | table _time host user src_ip event_type

This adds a readable label to each returned event.

## 6. timechart
Summarizes events over time.

    index=lab EventCode=4625
    | timechart span=5m count

This counts matching events in five-minute buckets and helps reveal bursts or trends.

## 7. rex
Extracts a field from raw event text using a regular expression.

    index=lab sourcetype=custom_auth
    | rex field=_raw "user=(?<user>[^ ]+)"
    | table _time user _raw

This extracts the value after user= up to the next space. It works only if the raw log format matches the expression.

## Combining commands

    index=lab EventCode=4625
    | stats count as failed_attempts by user, src_ip
    | where failed_attempts >= 5
    | table user src_ip failed_attempts

This is a useful starting point, but it counts across the selected search time range. Add time bucketing or a rolling-window design for a precise five-minute threshold.

## SPL investigation habits
- Set a meaningful time range.
- Start broad enough to inspect the event format, then narrow the search.
- Inspect raw events and field values before writing detection logic.
- Use explicit index and sourcetype constraints where possible.
- Confirm whether a field is source, destination or host information.
- Validate results against known test activity before scheduling an alert.
