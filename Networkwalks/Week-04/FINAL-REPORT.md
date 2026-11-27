# NetworkWalks Week 04 — Final Assessment Report

**Client / Target:** Mediroza General Hospital — `https://medirozahospital.com`  
**Assessment type:** Black-box web application assessment  
**Prepared by:** Hafsa Khan  
**Programme:** NetworkWalks Academy — Cybersecurity & Ethical Hacking  
**Assessment record:** Week 04  
**Report status:** Final report for the evidence collected; restricted-access and confidential-data objectives were not executed.

---

## 1. Executive Summary

This report documents the Week 04 assessment activities performed against the publicly accessible web surface of Mediroza General Hospital. The work completed covered passive reconnaissance, DNS and domain information review, TLS certificate inspection, technology fingerprinting, public endpoint checks, and non-invasive inspection of publicly accessible staff and patient login pages.

The collected evidence confirms that the homepage and both login pages responded with HTTP 200 during the recorded requests. The login pages exposed POST forms containing username and password fields. A WhatWeb request returned HTTP 403, while separate cURL requests returned HTTP 200. This difference is recorded as an observation and not treated as a confirmed security weakness.

No authentication bypass, restricted-area access, patient PDF retrieval, PDF decryption, employee salary discovery, or shareholder-data extraction is claimed. Those objectives require an instructor-approved test environment with synthetic records and dedicated test credentials. Accessing real patient or employee confidential information is not an appropriate validation method for a public-facing portfolio report.

**Overall conclusion:** Initial public reconnaissance and login-page inspection were completed and documented. No exploitable vulnerability was confirmed by the evidence collected. M2 and M3 data-handling objectives remain unvalidated; this report does not misrepresent them as completed.

## 2. Scope and Rules of Engagement

### In-scope target

- Domain: `medirozahospital.com`
- Public homepage: `https://medirozahospital.com/`
- Public staff login page: `https://medirozahospital.com/staff/login.php`
- Public patient login page: `https://medirozahospital.com/patient/login.php`
- Public endpoint checks: `/robots.txt`, `/sitemap.xml`, and `/favicon.ico`

### Assessment boundaries

The documented work was limited to low-impact public reconnaissance and unauthenticated page inspection. No denial-of-service activity, social engineering, credential guessing, authentication bypass attempts, or access to real confidential records was performed.

Any further access-control testing must use a designated staging environment, written scope confirmation, instructor-issued test credentials, and synthetic patient/employee records.

## 3. Methodology and Tools

| Stage | Method | Tools | Result |
|---|---|---|---|
| M1 — Initial reconnaissance | Domain, DNS, WHOIS and TLS review | Kali Linux, WHOIS, DNS utilities, cURL | Completed for public information |
| M1 — Technology review | HTTP response and technology fingerprinting | WhatWeb, cURL | Completed; response variation recorded |
| M1 — Public endpoints | Status checks and public page/link inspection | cURL, Python | Completed |
| M1 — Login-page review | Inspect public form structure without submitting credentials | cURL, Python HTML parser, browser review | Form structure captured |
| M2 — PDF analysis | Requires approved synthetic sample PDFs | Not performed | Awaiting approved lab samples |
| M3 — Sensitive-data analysis | Requires synthetic employee/shareholder data | Not performed | Awaiting approved lab dataset |
| M4 — Reporting | Consolidate observations, limitations and remediation guidance | Markdown documentation | Completed |

## 4. M1 — Initial Access Surface and Reconnaissance

### 4.1 Domain and DNS observations

- Resolved IPv4 address: `199.188.201.16`
- Registrar observed: NameCheap, Inc.
- Name servers observed: `dns1.namecheaphosting.com`, `dns2.namecheaphosting.com`
- Mail exchangers observed:
  - `mx1-hosting.jellyfish.systems`
  - `mx2-hosting.jellyfish.systems`
  - `mx3-hosting.jellyfish.systems`
- DNSSEC: unsigned in the captured WHOIS/DNS record.

These are reconnaissance observations, not vulnerabilities by themselves.

### 4.2 TLS and web technology

- Certificate subject: `CN=medirozahospital.com`
- Issuer observed: SSL.com TLS Issuing RSA CA R1
- Captured validity window: 14 August 2026 to 28 February 2027
- Web server identification: LiteSpeed
- WhatWeb identified HTML5 and LiteSpeed-related indicators.

### 4.3 HTTP response variation

A WhatWeb request returned HTTP 403, while separate cURL requests to the homepage returned HTTP 200. The available evidence does not establish why the responses differed. This may depend on request characteristics or server-side handling, but no cause is asserted without further validation.

### 4.4 Public endpoint checks

| Endpoint | Captured status |
|---|---:|
| `/` | 200 |
| `/robots.txt` | 200 |
| `/sitemap.xml` | 200 |
| `/favicon.ico` | 404 |

### 4.5 Public login-page inspection

| Observation | Staff login | Patient login |
|---|---|---|
| URL | `/staff/login.php` | `/patient/login.php` |
| HTTP status | 200 | 200 |
| Form method | POST | POST |
| Form action | `login.php` | `login.php` |
| Username input | Present | Present |
| Password input | Present | Present |
| Autocomplete | off | off |
| Additional checkbox | Not observed | Present |
| Cache-Control in captured headers | Not observed | `no-store, no-cache, must-revalidate` |

The inspection did not submit either form and did not test authentication behaviour. The presence of a login page is expected functionality and is not a vulnerability by itself.

## 5. M2 — PDF Encryption and Content Recovery

**Status: Not performed / awaiting approved lab material.**

The assignment describes analysis and recovery of three confidential patient PDF reports. No real patient reports were accessed, downloaded, decrypted, or reproduced for this assessment record.

To complete this stage safely, the training provider should supply three synthetic PDF files with no real patient information and confirm that password-recovery analysis is authorized for those files. The report can then record file metadata, encryption properties, test procedure, and recovery results without exposing personal health information.

## 6. M3 — Employee and Shareholder Data Analysis

**Status: Not performed / awaiting synthetic dataset.**

No employee salary information, shareholder details, or other confidential records were accessed or extracted. These data categories are sensitive and must not be collected from a live hospital system for a training portfolio.

A safe validation requires instructor-provided synthetic records or a purpose-built lab dataset. Any final summary should use fictional identities and values and should avoid publishing personal or financial data.

## 7. Findings and Risk Assessment

No exploitable vulnerability was confirmed from the evidence collected. The following are observations and hardening recommendations, not verified vulnerabilities.

| ID | Observation | Rating | Evidence / limitation |
|---|---|---|---|
| OBS-01 | LiteSpeed server technology is disclosed in response headers | Informational | Server header captured; version-specific exposure not established |
| OBS-02 | WhatWeb and cURL received different HTTP statuses | Informational | 403 and 200 responses captured; cause not established |
| OBS-03 | Several security headers were not visible in the captured header excerpts | Needs verification | Full, repeatable response-header capture is required before confirming absence |
| OBS-04 | DNSSEC was reported as unsigned | Informational / hardening | Record observation only; assess DNS provider support and operational requirements |

No Critical, High, Medium, or Low severity vulnerability is assigned because no exploitable weakness or impact was demonstrated.

## 8. Recommendations

1. Review and maintain a current inventory of externally exposed web services and DNS records.
2. Confirm whether DNSSEC can be enabled through the domain's DNS provider, following change-control procedures.
3. Review web response headers and apply appropriate controls where compatible with the application, including HSTS, Content-Security-Policy, X-Content-Type-Options, Referrer-Policy and frame-embedding protections.
4. Ensure authentication endpoints use secure password storage, rate limiting, monitoring, secure session management, and multi-factor authentication where appropriate. These controls were not tested in this assessment.
5. Keep patient and staff portals isolated by role and enforce server-side authorization checks on every protected resource.
6. Use synthetic records and a dedicated staging environment for security testing, including PDF encryption and data-exposure exercises.
7. Review server and application logs for unusual authentication patterns and access to sensitive records.
8. Redact personal, health, financial, credential and token data from screenshots and public reports.

## 9. Limitations

- The assessment evidence available for this report covers public, unauthenticated observations only.
- No test credentials or instructor-provided synthetic patient PDFs or employee/shareholder datasets were available in the evidence reviewed.
- No authenticated testing, exploit validation, or restricted-resource access was performed.
- Header observations are based on captured response excerpts and require a complete repeatable verification before being treated as confirmed omissions.
- The report makes no claim that the target is secure; it records only what was observed within the performed assessment.

## 10. Conclusion

The M1 public reconnaissance and login-page inspection activities were completed and documented. M4 reporting is complete for the evidence collected. M2 and M3 remain pending approved synthetic training material and a designated test environment. No real patient, employee, or shareholder information was accessed or included.

**Prepared by:** Hafsa Khan  
**Programme:** NetworkWalks Academy — Week 04  
**Project:** Mediroza General Hospital — Black-box Penetration Testing
