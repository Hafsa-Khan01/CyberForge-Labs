# IOC Type — Where to Find It — Tool to Check It

| IOC type | Where to find it | Tool to check it |
|---|---|---|
| SHA-256 | Attachment/file metadata, EDR | VirusTotal, local hash utility |
| MD5 | Legacy reports/file metadata | VirusTotal (correlate SHA-256) |
| Domain | Email URLs, DNS/proxy logs | urlscan.io, VirusTotal, OTX |
| URL | Email HTML/body, proxy logs | urlscan.io, VirusTotal |
| IPv4 | Headers, firewall/proxy/DNS logs | AbuseIPDB, VirusTotal, OTX |
| IPv6 | Network telemetry, DNS AAAA | VirusTotal, OTX |
| Sender email | From/Return-Path/mailbox logs | Raw header review, MXToolbox |
| Reply-To | Raw email headers | Header parser, MXToolbox |
| Message-ID | Raw headers/mail trace | Mail gateway/message trace |
| DNS query | Endpoint/resolver/network logs | DNS tools, VirusTotal, OTX |
| TLS certificate fingerprint | TLS inspection/proxy telemetry | Certificate transparency services |
| Registry key/file path | Sysmon, EDR, forensic artefacts | Sysmon/EDR, forensic tools |

Defang domains and URLs. Timestamp reputation checks. Do not submit confidential data to public services.
