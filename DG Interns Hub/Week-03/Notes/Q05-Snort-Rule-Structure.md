# Q5. Structure of a Snort rule

A basic Snort rule has a **rule header** followed by a parenthesized **rule-options** section.

Example:

```snort
alert tcp any any -> $HOME_NET 22 (msg:"SSH Connection Attempt"; sid:1000002; rev:1;)
```

## Rule header
- `alert` — rule action; generate an alert on a match.
- `tcp` — protocol to inspect.
- First `any any` — source IP and source port.
- `->` — traffic direction.
- `$HOME_NET 22` — destination network and destination port.

The header identifies the traffic scope. Variables such as `$HOME_NET` are defined in the Snort configuration.

## Common rule options

| Option | Purpose | Example |
|---|---|---|
| `msg` | Human-readable alert message | `msg:"SSH Connection Attempt";` |
| `sid` | Rule identifier; local rules commonly use IDs 1,000,000 and above | `sid:1000002;` |
| `rev` | Revision number for tracking rule changes | `rev:1;` |
| `flags` | Match TCP flag conditions | `flags:S;` |
| `flow` | Match flow direction/state properties supported by the version | `flow:to_server,established;` |
| `threshold` | Control alert frequency based on a tracking/count/time condition | `threshold:type threshold, track by_src, count 20, seconds 1;` |
| `classtype` | Assign a predefined classification and priority | `classtype:attempted-recon;` |

## Example interpretation
`alert tcp any any -> $HOME_NET 22` matches TCP packets directed to port 22 on the protected network. The options give the alert a readable message, a unique SID, and a revision number.

## Threshold note
A `threshold` option controls how often alerts are generated for matching traffic; it does not by itself prove that a scan or attack occurred. In the supplied example, the threshold condition is evaluated per source according to the selected tracking mode and time window. Test behaviour using the installed Snort version.

## Rule-writing checklist
- Scope source and destination networks correctly.
- Choose the correct protocol and ports.
- Use unique SIDs and increment revisions when changing a rule.
- Add a clear message and appropriate classification.
- Test syntax before monitoring traffic.
- Validate with controlled traffic and record false positives/limitations.
