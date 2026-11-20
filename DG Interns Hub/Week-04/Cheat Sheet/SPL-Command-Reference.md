# SPL Command — Meaning — Example

| SPL command | Meaning | Example |
|---|---|---|
| search | Finds matching events | `index=lab EventCode=4625` |
| where | Filters using an expression | `| where count >= 5` |
| stats | Calculates aggregates | `| stats count by user` |
| table | Displays selected fields | `| table _time host user` |
| fields | Keeps/removes fields | `| fields _time host src_ip` |
| eval | Creates/transforms a field | `| eval label="failed login"` |
| timechart | Aggregates into time buckets | `| timechart span=5m count` |
| bin | Buckets numeric/time values | `| bin _time span=5m` |
| rex | Extracts fields with regex | `| rex field=_raw "user=(?<user>[^ ]+)"` |
| sort | Sorts results | `| sort - count` |
| head | Returns first N results | `| head 10` |
| dedup | Removes duplicates by field | `| dedup src_ip` |
| rename | Renames fields | `| rename src_ip as source` |
| eventstats | Adds aggregates to each event | `| eventstats avg(duration) as avg_duration` |
| transaction | Groups related events | `| transaction user maxspan=5m` |
| lookup | Enriches with lookup data | `| lookup asset_inventory host OUTPUT owner` |
| append | Appends another search's results | `| append [ search index=lab ]` |
| fillnull | Replaces null values | `| fillnull value="unknown" user` |
| coalesce | Uses first non-null value | `| eval account=coalesce(user, TargetUserName)` |

Examples are illustrative. Confirm syntax, field names and data volume before production use.
