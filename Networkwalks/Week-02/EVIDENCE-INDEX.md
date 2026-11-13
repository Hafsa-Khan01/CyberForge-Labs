# Week 02 — Evidence Index

**Prepared by:** Hafsa Khan  
**Programme:** NetworkWalks Cybersecurity & Ethical Hacking

This index tracks the evidence artifacts for PM1, the attempted PM4 theHarvester exercise, and PM5. The final report documents the observed results. Original screenshots and the topology PDF still need to be uploaded to this repository after a privacy/scope review.

## Repository evidence structure

```text
Networkwalks/Week-02/
├── Evidence/
│   ├── PM1-Footprinting/
│   ├── PM4-theHarvester/
│   └── PM5-Zenmap/
├── README.md
├── FINAL-REPORT.md
└── EVIDENCE-INDEX.md
```

## Evidence register

| Evidence ID | Module | Required artifact | What it demonstrates | Repository location | Status |
|---|---|---|---|---|
| PM1-E01 | PM1 | WHOIS output screenshot | Domain registration/registrar information observed | `Evidence/PM1-Footprinting/` | Upload pending |
| PM1-E02 | PM1 | Nslookup output screenshots | DNS queries and A-record result | `Evidence/PM1-Footprinting/` | Upload pending |
| PM1-E03 | PM1 | cURL output screenshots | HTTP response status and headers | `Evidence/PM1-Footprinting/` | Upload pending |
| PM1-E04 | PM1 | WhatWeb output screenshot | Visible web technology fingerprint | `Evidence/PM1-Footprinting/` | Upload pending |
| PM1-E05 | PM1 | Wafw00f output screenshot | WAF detection result | `Evidence/PM1-Footprinting/` | Upload pending |
| PM1-E06 | PM1 | DNSRecon output screenshot | DNS enumeration output | `Evidence/PM1-Footprinting/` | Upload pending |
| PM4-E01 | PM4 | Microsoft Baidu-source command/output screenshot | Official assignment task; successful output not verified | `Evidence/PM4-theHarvester/` | Pending verification |
| PM4-E02 | PM4 | Microsoft all-sources command/output screenshot | Official assignment task; successful output not verified | `Evidence/PM4-theHarvester/` | Pending verification |
| PM4-E03 | PM4 | Additional NetworkWalks-domain run output, if retained | Additional target reported by user; output not verified | `Evidence/PM4-theHarvester/` | Pending verification |
| PM5-E01 | PM5 | Windows `ipconfig` / `ipconfig /all` screenshot | Active Wi-Fi IPv4, subnet mask, gateway | `Evidence/PM5-Zenmap/` | Upload pending |
| PM5-E02 | PM5 | Zenmap Ping Scan screenshot | Target subnet and actual Nmap output | `Evidence/PM5-Zenmap/` | Upload pending |
| PM5-E03 | PM5 | Zenmap Topology screenshot | Discovered-host topology view | `Evidence/PM5-Zenmap/` | Upload pending |
| PM5-E04 | PM5 | `PM5-Network-Topology.pdf` | Saved topology graphic with legend, if enabled | `Evidence/PM5-Zenmap/` | Saved locally; upload pending |

## Verified PM5 values

| Item | Value |
|---|---|
| Active adapter | Wi-Fi |
| Windows IPv4 | Redacted in public copy |
| Subnet mask | `255.255.255.0` |
| Default gateway | Redacted in public copy |
| Scanned subnet | Redacted local /24 subnet |
| Scan profile | Ping Scan |
| Equivalent command | `nmap -sn <authorized-local-subnet>` |
| Addresses scanned | 256 |
| Live hosts | 2 |
| Router MAC | Redacted in public copy |
| Router vendor | Huawei Technologies |
| Windows host MAC | Not displayed in the recorded scan output |

## Pre-submission checklist

- [ ] Confirm the report matches the original PM1 screenshots and command output.
- [ ] Review PM4 Microsoft Baidu-source and all-sources output files before reporting discovered items.
- [ ] Add the NetworkWalks PM4 run only if its original output is retained and reviewed.
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
