# Q7. MITRE ATT&CK T1046 — Network Service Discovery

## What is T1046?
MITRE ATT&CK technique **T1046 — Network Service Discovery** describes adversary activity that probes systems to identify services running on remote hosts. This can include scanning ports and identifying exposed services to plan later actions. The technique was previously titled “Network Service Scanning”; the current ATT&CK name is “Network Service Discovery.”

Official reference: https://attack.mitre.org/techniques/T1046/

## Why it matters to a SOC
- Unexpected scans can indicate reconnaissance before exploitation or lateral movement.
- Internal scanning may be legitimate administration, vulnerability management, or asset discovery.
- Analysts should consider source host, destination range, ports, rate, timing, user context, and approved change windows.
- A scan alert is an investigative lead, not proof of malicious intent.

## Mapping a Snort rule to ATT&CK
A detection rule can include a human-readable message and metadata/reference identifying the ATT&CK technique. This mapping documents the behaviour the rule is intended to detect; it does not mean Snort independently validates an ATT&CK technique.

Example supplied for this exercise:

```snort
alert tcp $EXTERNAL_NET any -> $HOME_NET any (msg:"MITRE T1046 - Nmap SYN Port Scan Detected"; flags:S; threshold:type threshold, track by_src, count 20, seconds 1; classtype:attempted-recon; metadata:mitre_technique T1046; reference:url,attack.mitre.org/techniques/T1046/; sid:1000004; rev:1;)
```

## How to interpret it
- `tcp` — inspect TCP traffic.
- `$EXTERNAL_NET any -> $HOME_NET any` — source outside the protected network to any protected destination/port.
- `flags:S` — match SYN-flagged TCP packets as specified by the installed Snort version.
- `threshold` — control alert generation for repeated matches from a source.
- `classtype:attempted-recon` — classify as reconnaissance-related activity.
- `metadata` and `reference` — record the intended ATT&CK mapping and supporting reference.
- `sid` and `rev` — identify the rule and its revision.

## Detection limitations
A SYN packet alone is not sufficient to identify an Nmap scan. Normal connection attempts also begin with SYN packets. Thresholds, destination/port diversity, timing, flow context, and controlled validation improve usefulness. The sample rule is a starting point and must be tested; it may need tuning for the local Snort version and network layout.

## Safe validation
Only scan systems you own or are explicitly authorized to test. Record the Nmap command, source and target addresses, time window, Snort version, rule-test output, and alert evidence.
