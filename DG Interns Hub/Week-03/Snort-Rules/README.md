# Snort Local Rules — Week 03

This directory contains the local signatures used for the Week 03 network-detection exercise.

## Rule inventory

| SID | Match objective | Triage note |
|---|---|---|
| 1000001 | ICMP traffic directed to HOME_NET | Establishes ICMP visibility, not hostile intent. |
| 1000002 | TCP traffic destined for SSH port 22 | Does not establish a successful SSH login. |
| 1000003 | TCP traffic destined for HTTP port 80 | Does not establish an HTTP exploit. |
| 1000004 | Thresholded SYN traffic from EXTERNAL_NET to HOME_NET | Scan-like indicator; not unique to Nmap. |

## Deployment checklist

1. Set `HOME_NET` to the actual monitored lab subnet.
2. Define `EXTERNAL_NET` relative to the lab topology (commonly `!$HOME_NET`).
3. Confirm that the active Snort configuration includes `local-week3.rules`.
4. Identify the correct capture interface with `ip -br addr` and `ip route`.
5. Validate the configuration using syntax supported by the installed Snort version.
6. Confirm that the sensor can observe the authorized test traffic.
7. Preserve the validation output and corresponding alert evidence.

## Validation examples

```bash
snort -V
sudo snort -T -i <interface> -c /etc/snort/snort.conf
```

Adjust paths, options and interface names for the installed version and configuration.

## Detection limitations

The first three rules are intentionally broad and can alert on benign traffic. The SYN threshold is a heuristic; ordinary connections and multiple tools can generate SYN packets. Interpret alerts using source identity, destination-port diversity, timing, network context and corroborating telemetry. Sensor placement, traffic direction, rule inclusion and threshold behavior all affect detection.

See the [Ubuntu Snort practical](../Writeups/Ubuntu-Snort-Practical.md) and [evidence index](../Evidence/README.md) for the documented lab context and published screenshots.