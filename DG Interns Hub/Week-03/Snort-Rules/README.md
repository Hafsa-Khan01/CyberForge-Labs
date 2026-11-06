# Snort Local Rules

## Included signatures
- SID 1000001: ICMP traffic to HOME_NET.
- SID 1000002: TCP traffic destined for SSH port 22.
- SID 1000003: TCP traffic destined for HTTP port 80.
- SID 1000004: thresholded SYN-only traffic from EXTERNAL_NET to HOME_NET, mapped to MITRE ATT&CK T1046.

## Deployment and validation
1. Set HOME_NET to the actual monitored lab subnet and EXTERNAL_NET to !$HOME_NET.
2. Confirm the main configuration includes the local rules file.
3. Identify the correct interface with ip -br addr.
4. Validate the configuration with the syntax appropriate to the installed Snort version.
5. Monitor an interface that can actually see the authorized test traffic.
6. Test only between systems you own or are explicitly authorized to assess.

## Limitations
The first three rules are intentionally broad and may alert on benign traffic. The SYN threshold is a heuristic, not definitive Nmap attribution. Sensor placement, traffic direction, rule syntax and threshold behavior depend on the environment and Snort version.
