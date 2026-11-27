# NetworkWalks — Week 04

**Project:** Mediroza General Hospital — Web Application Penetration Test  
**Assessment type:** Black-box assessment  
**Prepared by:** Hafsa Khan  
**Programme:** NetworkWalks Academy  
**Target:** https://medirozahospital.com

## Project overview

Week 04 documents a four-phase web application security assessment covering public-surface reconnaissance, patient-portal security review, PDF document protection, and exposure of legacy files and database backups.

The technical report records the procedures, observations, risk assessment, limitations and remediation guidance. This repository contains a sanitized project summary only. Patient documents, personal information, employee/shareholder records, credentials, recovered passwords and raw database contents must not be committed.

## Assessment phases

| Phase | Focus | Reported outcome |
|---|---|---|
| M1 — Reconnaissance and Network Enumeration | DNS, WHOIS, TLS, HTTP responses, technology fingerprinting and network/service observations | Documented |
| M2 — Patient Portal Assessment | Public portal review, PHP/MySQL error disclosure and access-control considerations | Documented; cross-patient access remains unvalidated |
| M3 — PDF Document Password Security Testing | Password-protection review, hash-based testing and document-open verification for three PDFs | Documented in the assessment report; sensitive document contents excluded |
| M4 — Legacy Directory and SQL Backup Exposure | Review of public legacy directory listing and exposed database-backup material | Exposure documented; personal and financial records excluded |

## Principal observations documented

- Public DNS, TLS and web-server information was collected during reconnaissance.
- The target returned different HTTP status codes to separate WhatWeb and cURL requests; the difference was recorded without assuming a cause.
- Public staff and patient login pages and their visible form structures were reviewed.
- The assessment report documents weak password protection affecting three PDF files. No patient names, diagnoses, report contents or recovered passwords are published here.
- The report documents a publicly accessible legacy directory and an exposed database backup. No employee or shareholder personal, contact, identity or financial records are reproduced in this repository.
- PHP/MySQL error disclosure and access-control concerns are discussed with appropriate evidence limitations. A login page or error message alone is not treated as proof of an authentication bypass or unauthorized patient-record access.

## Risk summary

The private assessment report records the risk ratings and supporting evidence for the observations. Public repository material intentionally avoids reproducing sensitive records or operational details that could expose individuals. Findings that require additional validation are identified as such rather than presented as confirmed exploit paths.

## Tools and environment

Kali Linux, Nmap, DNSRecon, Nslookup, Dig, WHOIS, cURL, WhatWeb, WAFW00F, John the Ripper, PDF hash utilities, browser inspection and SQL analysis utilities.

## Repository contents

- [Final report — sanitized project version](FINAL-REPORT.md)
- [Evidence index](EVIDENCE-INDEX.md)

## Evidence handling

The detailed report and original evidence are maintained separately from this public summary. Before uploading any supporting screenshot or log, redact patient information, employee/shareholder details, credentials, session tokens, recovered passwords, and database contents. Evidence entries marked as local or private are not represented as files available in this repository.

## Responsible disclosure and scope

This is a training assessment record. Testing of live systems must remain within the owner's written authorization and the agreed scope. No confidential patient, employee or shareholder information should be published. The public report is deliberately sanitized and is not a substitute for the restricted full technical report.
