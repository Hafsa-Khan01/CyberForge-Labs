# NetworkWalks — Week 04

**Project:** Penetration Testing — Mediroza General Hospital  
**Assessment type:** Black-box web application assessment  
**Prepared by:** Hafsa Khan  
**Programme:** NetworkWalks Academy — Cybersecurity & Ethical Hacking

## Work log

This week’s work has focused on the initial, non-invasive assessment of the target's publicly exposed web surface. The activities documented below are limited to passive reconnaissance and inspection of publicly accessible pages and response metadata.

| Activity | Work performed | Status |
|---|---|---|
| Initial reconnaissance | Domain, DNS records, WHOIS information and TLS certificate review | Completed |
| Technology fingerprinting | Web server and publicly returned technology indicators reviewed with WhatWeb | Completed |
| Public endpoint review | Homepage, robots.txt, sitemap.xml and favicon response checks | Completed |
| Login-page inspection | Public staff and patient login pages, form methods and visible input structure reviewed without submitting credentials | Completed |
| Security-header review | Initial response headers captured; further verification remains a separate follow-up | In progress |

## Key observations

- DNS resolution returned `199.188.201.16`.
- The observed web server identified itself as LiteSpeed.
- The captured TLS certificate was issued for `medirozahospital.com`; the observed validity window was 14 August 2026 to 28 February 2027.
- The homepage and the two public login pages returned HTTP 200 in the captured requests.
- The staff and patient login pages exposed POST forms with username and password fields. The patient page also displayed an additional checkbox.
- WhatWeb returned a 403 response during one request, while separate cURL requests returned 200. This difference is recorded as an observation, not as a confirmed vulnerability.
- The public endpoint checks returned 200 for `/`, `/robots.txt` and `/sitemap.xml`; `/favicon.ico` returned 404.

## Tools used

Kali Linux, WHOIS, DNS utilities, WhatWeb, cURL and Python.

## Final report

- [Final assessment report](FINAL-REPORT.md)
- [Evidence index](EVIDENCE-INDEX.md)

## Evidence organization

Command output was saved in the local working directory under:

`Networkwalks/Week-04/M1-Initial-Access/Recon/`

Relevant local records include:

- `M1-Passive-Recon.txt`
- `M1-Phases-1-3.txt`
- `M1-Phase3-Corrected.txt`
- `M1-Phase4-Login-Review.txt`

These local output files and screenshots still need to be reviewed for sensitive information and added to the repository before they can be linked as uploaded evidence.

## Assessment status

The initial public reconnaissance and login-page inspection activities are documented. This does **not** represent completion of the full penetration test. No authentication bypass, restricted-area access, patient-record retrieval, PDF decryption, or employee/shareholder data extraction is claimed.

Any further authentication or access-control validation must use an instructor-approved test environment, test credentials and synthetic records. Do not access or publish real patient or employee information.

## Responsible testing

Testing must remain within the written assessment scope. No denial-of-service activity, social engineering, credential guessing, or access to real confidential records is included in this public work log.
