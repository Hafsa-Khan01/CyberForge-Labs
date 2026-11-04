# Q6. Signature-based vs anomaly-based detection

## Signature-based detection
Signature detection looks for known patterns or indicators associated with specific threats. A rule may match a known byte sequence, protocol pattern, domain, hash, or traffic behaviour.

**SOC examples**
- An IDS rule matches a known exploit request pattern.
- Endpoint protection identifies a file hash associated with known malware.
- A Snort rule alerts on a defined suspicious TCP flag or content pattern.

**Strengths:** precise for known patterns, explainable, and often easier to validate.

**Limitations:** may miss new variants, modified payloads, or activity that does not match the rule.

## Anomaly-based detection
Anomaly detection identifies activity that deviates from an established baseline or expected behaviour. It may use statistical thresholds, behavioural models, or machine-learning methods.

**SOC examples**
- A workstation suddenly makes hundreds of outbound connections when its normal pattern is a few.
- A service account logs in at an unusual time or from a new location.
- DNS query volume from one host rises sharply compared with its baseline.

**Strengths:** can highlight previously unseen or unusual behaviour.

**Limitations:** can produce false positives when legitimate workloads change; requires reliable baselines and context.

## Comparison

| Aspect | Signature-based | Anomaly-based |
|---|---|---|
| Detection basis | Known rule, pattern, or indicator | Deviation from expected behaviour |
| Best at | Recognized threats and repeatable patterns | Novel or unusual activity |
| Main weakness | Unknown or changed threats may evade signatures | False positives and baseline drift |
| Tuning | Rule quality and coverage | Baseline quality, thresholds, and context |

## SOC practice
The approaches complement each other. Analysts correlate a signature alert with behavioural context and endpoint/network telemetry before deciding whether an event is malicious.
