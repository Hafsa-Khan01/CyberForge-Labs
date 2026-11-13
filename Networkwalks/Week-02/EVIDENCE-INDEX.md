# Week 02 — Evidence Index

**Prepared by:** Hafsa Khan  
**Programme:** NetworkWalks Cybersecurity & Ethical Hacking

This index tracks the evidence artifacts for PM1, the attempted PM4 theHarvester exercise, and PM5. The final report documents the observed results. Original screenshots and the topology PDF still need to be uploaded to this repository after a privacy/scope review.

## Suggested folder structure

```text
Networkwalks/Week-02/
├── PM1-Kali-Footprinting/
│   ├── PM1-E01-WHOIS.png
│   ├── PM1-E02-NSLOOKUP.png
│   ├── PM1-E03-CURL.png
│   ├── PM1-E04-WhatWeb.png
│   ├── PM1-E05-WAFW00F.png
│   └── PM1-E06-DNSRecon.png
├── PM5-Zenmap/
│   ├── PM5-E01-Windows-IP-Configuration.png
│   ├── PM5-E02-Zenmap-Ping-Scan.png
│   ├── PM5-E03-Zenmap-Topology.png
│   └── PM5-Network-Topology.pdf
├── FINAL-REPORT.md
├── README.md
└── EVIDENCE-INDEX.md
```

## Evidence register

| Evidence ID | Module | Required artifact | What it demonstrates | Repository status |
|---|---|---|---|---|
| PM1-E01 | PM1 | WHOIS output screenshot | Domain registration/registrar information observed | Upload pending |
| PM1-E02 | PM1 | Nslookup output screenshots | DNS queries and A-record result | Upload pending |
| PM1-E03 | PM1 | cURL output screenshots | HTTP response status and headers | Upload pending |
| PM1-E04 | PM1 | WhatWeb output screenshot | Visible web technology fingerprint | Upload pending |
| PM1-E05 | PM1 | Wafw00f output screenshot | WAF detection result | Upload pending |
| PM1-E06 | PM1 | DNSRecon output screenshot | DNS enumeration output | Upload pending |
| PM4-E01 | PM4 | Microsoft Baidu-source command/output screenshot | Official assignment task; successful output not verified | Evidence pending |\n| PM4-E02 | PM4 | Microsoft all-sources command/output screenshot | Official assignment task; successful output not verified | Evidence pending |\n| PM4-E03 | PM4 | Additional NetworkWalks-domain run output, if retained | Additional target reported by user; output not verified | Evidence pending |\n| PM5-E01 | PM5 | Windows `ipconfig` / `ipconfig /all` screenshot | Active Wi-Fi IPv4, subnet mask, gateway | Upload pending |
| PM5-E02 | PM5 | Zenmap Ping Scan screenshot | Target subnet and actual Nmap output | Upload pending |
| PM5-E03 | PM5 | Zenmap Topology screenshot | Discovered-host topology view | Upload pending |
| PM5-E04 | PM5 | `PM5-Network-Topology.pdf` | Saved topology graphic with legend, if enabled | Saved locally; upload pending |

## Verified PM5 values

| Item | Value |
|---|---|
| Active adapter | Wi-Fi |
| Windows IPv4 | `192.168.100.33` |
| Subnet mask | `255.255.255.0` |
| Default gateway | `192.168.100.1` |
| Scanned subnet | `192.168.100.0/24` |
| Scan profile | Ping Scan |
| Equivalent command | `nmap -sn 192.168.100.0/24` |
| Addresses scanned | 256 |
| Live hosts | 2 |
| Router MAC | `30:D1:7E:4D:EC:10` |
| Router vendor | Huawei Technologies |
| Windows host MAC | Not displayed in the recorded scan output |

## Pre-submission checklist

- [ ] Confirm the report matches the original PM1 screenshots and command output.\n- [ ] Review PM4 Microsoft Baidu-source and all-sources output files before reporting discovered items.\n- [ ] Add the NetworkWalks PM4 run only if its original output is retained and reviewed.
- [ ] Upload redacted PM1 screenshots.
- [ ] Upload Windows network configuration evidence.
- [ ] Upload Zenmap Ping Scan configuration/output screenshot.
- [ ] Upload Zenmap Topology screenshot.
- [ ] Upload the saved topology PDF.
- [ ] Confirm the topology PDF and screenshots do not expose unrelated or sensitive network details.
- [ ] Keep signed authorization private unless publication is explicitly permitted.
- [ ] Do not describe PM4 as a successful enumeration until its original output has been reviewed. PM2 and PM3 are not included as completed modules.

## Evidence handling

Retain original captures privately. Publish only redacted copies appropriate for the intended audience. Never commit passwords, tokens, private keys, VM images, or raw packet captures containing third-party personal information.
