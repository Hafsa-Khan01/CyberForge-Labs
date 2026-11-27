# NetworkWalks Week 04 — Penetration Testing Report

**Client / Target:** Mediroza General Hospital — https://medirozahospital.com  
**Assessment type:** Black-box web application penetration test  
**Prepared by:** Hafsa Khan  
**Programme:** NetworkWalks Academy  
**Report edition:** Public sanitized version

> **Confidentiality notice:** This public version summarizes the assessment without reproducing patient documents, personal health information, employee/shareholder records, recovered passwords, credentials or raw database contents. The detailed evidence set and any restricted client report must remain in an appropriately controlled location.

---

## 1. Executive Summary

This report summarizes a four-phase web application security assessment of the Mediroza General Hospital website. The documented work covered public-surface reconnaissance, review of the patient portal, password protection of three PDF documents, and exposure of legacy files and a database backup.

The assessment report records several security concerns: verbose PHP/MySQL error disclosure, weak password protection affecting three PDF documents, a publicly accessible legacy directory, and exposure of a database backup containing sensitive categories of information. The public version intentionally omits the underlying personal records and any material that could enable access to confidential documents.

The patient portal review also raised an access-control concern. A visible portal page or application error does not, by itself, prove that one patient's records can be accessed by another user. Any cross-account authorization claim must be supported by controlled testing with designated test accounts and synthetic records.

## 2. Scope and Assessment Approach

**Target:** https://medirozahospital.com

The report covers:
- Public DNS, domain, TLS and web-technology reconnaissance
- Public staff and patient portal page inspection
- Review of application error disclosure
- Assessment of password protection on three PDF documents
- Review of publicly exposed legacy files and a database-backup exposure
- Risk assessment and remediation recommendations

Testing of a live hospital system must be supported by explicit written authorization and a defined scope. This public report does not reproduce authorization documents or confidential evidence.

## 3. Methodology and Tools

| Phase | Assessment focus | Tools / methods |
|---|---|---|
| M1 — Initial reconnaissance | Domain, DNS, TLS, HTTP responses, technology fingerprinting and public portal inspection | Kali Linux, WHOIS, DNSRecon, Nslookup, Dig, Nmap, cURL, WhatWeb, WAFW00F and browser inspection |
| M2 — PDF document security | Password-protection review and hash-based password testing of three protected PDFs | PDF hash utilities, John the Ripper and document validation |
| M3 — Legacy data exposure | Public legacy directory and database-backup exposure review | Browser, command-line inspection and SQL analysis utilities |
| M4 — Reporting | Evidence review, findings, risk assessment and remediation | Technical report preparation |

## 4. M1 — Reconnaissance and Network Enumeration

### 4.1 Domain and network reconnaissance

The assessment recorded public DNS and domain-registration information, the resolved web host, name-server and mail-exchange records, and TLS certificate information. These details support asset identification and exposure review; they are not vulnerabilities by themselves.

### 4.2 Web technology and HTTP behaviour

The web server was identified as LiteSpeed in the captured responses. WhatWeb and cURL returned different HTTP status codes during separate requests. The difference was recorded as an observation; no definitive cause is assigned without repeatable validation under controlled request conditions.

### 4.3 Public portal inspection

The staff and patient login pages were reviewed for their visible form structure and response behaviour. The report also records PHP/MySQL warning or error disclosure.

Verbose application errors can reveal implementation details and should not be returned to unauthenticated users. The report treats the error disclosure as an information-exposure concern; it does not infer a successful authentication bypass solely from an error message.

### 4.4 Access-control considerations

The patient portal review identified an area requiring authorization testing. A portal dashboard or page response is not sufficient evidence of cross-user data access. Validation should be performed only with approved test accounts and synthetic patient records, confirming that each user can access only their own authorized resources.

## 5. M2 — Patient Portal Assessment

The assessment report documents public patient-portal inspection and PHP/MySQL warning or error disclosure. It also identifies an access-control concern requiring further validation. A dashboard view or error response alone does not demonstrate cross-patient access.

The report records a patient-portal access-control concern that requires further validation. A dashboard view alone does not prove cross-patient access. Validation should use approved test accounts and synthetic records only.

**Security impact:** Verbose application errors may disclose implementation details. An authorization weakness, if confirmed, could permit access to records outside a user's permissions.

**Recommended controls:**
- Disable detailed PHP/MySQL error display in production and log diagnostic details privately.
- Return generic error messages to users.
- Validate server-side object-level authorization using approved test accounts and synthetic patient records.
- Ensure each account can access only its own authorized records.

## 6. M3 — PDF Document Password Security Testing

The assessment report documents password-security testing against three protected PDF files, including hash-based password testing and verification that the documents could be opened after password recovery.

The public repository does not include the original PDFs, their contents, patient details, recovery hashes or recovered passwords. Those materials are sensitive and must remain excluded from public version control.

**Security impact:** Weak or guessable document passwords can allow an unauthorized party who obtains a copy to recover the password and read confidential contents.

**Recommended controls:**
- Use strong, unique encryption passwords generated and distributed through a separate secure channel.
- Do not rely on PDF passwords as the only access-control boundary.
- Restrict document storage and downloads through authenticated, server-side authorization.
- Monitor access and download events for unusual activity.

## 7. M4 — Legacy Directory and SQL Backup Exposure

The assessment report documents a publicly accessible legacy directory and an exposed SQL database backup. The backup is reported to contain staff-related and shareholder-related information categories. No personal names, contact details, identity numbers, salary figures, ownership percentages, database rows or raw backup contents are reproduced here.

**Security impact:** Public access to an unprotected database backup can expose sensitive business and personal information and may disclose internal schema details.

**Recommended controls:**
- Remove database backups and legacy archives from public web roots.
- Store backups in private, access-controlled storage.
- Apply least-privilege access and strong encryption at rest and in transit.
- Rotate any credentials or secrets that may have been included in exposed backups.
- Review web-server access logs to determine whether the files were accessed.
- Disable directory indexing and establish a controlled backup lifecycle.

## 8. Findings Summary

| ID | Finding | Severity in assessment | Public-report treatment |
|---|---|---|---|
| F-01 | Publicly accessible database backup containing sensitive data categories | Critical | Exposure summarized; records and backup excluded |
| F-02 | Weak/recoverable password protection affecting three PDF documents | High | Testing outcome summarized; documents, hashes and passwords excluded |
| F-03 | PHP/MySQL error disclosure | Medium | Error-disclosure concern described without exploit instructions |
| F-04 | Patient-portal access-control concern | Requires further validation | Not presented as confirmed cross-patient access |
| F-05 | Public legacy directory listing | High | Exposure summarized; sensitive file contents excluded |
| F-06 | Exposed network/service information | Informational | Reconnaissance observation; no vulnerability inferred solely from disclosure |

Severity labels above reflect the assessment report's recorded ratings. They should be interpreted alongside the underlying restricted evidence and the stated validation limitations.

## 9. Remediation Priorities

1. Immediately remove public access to database backups, legacy archives and confidential document directories.
2. Determine whether exposed files were accessed, preserve relevant logs, and follow the organization's incident-response process.
3. Rotate credentials, keys or secrets that may have been present in exposed backups.
4. Replace weak document passwords and enforce secure document storage and authorization.
5. Configure the application to log detailed errors privately while returning generic error messages to users.
6. Perform server-side authorization checks on every patient and staff resource, using dedicated test accounts for validation.
7. Review security headers, TLS configuration, exposed services and web-server configuration as part of routine hardening.
8. Establish periodic external exposure reviews and secure backup-retention procedures.

## 10. Limitations and Evidence Handling

- This is a sanitized public summary, not the full restricted evidence pack.
- No patient records, employee/shareholder records, credentials, recovered passwords, raw database rows or original PDF files are included.
- Access-control concerns that are not conclusively demonstrated are labelled for further validation.
- Findings and severity ratings should be checked against the original evidence before being used for operational remediation decisions.
- Public repository screenshots and logs must be individually reviewed and redacted before publication.

## 11. Conclusion

The Week 04 assessment report documents reconnaissance, portal review, PDF document-security testing, and legacy directory/database-backup exposure analysis. The most significant reported risks relate to publicly accessible backup material and weak protection of confidential PDF documents. The recommended response is to restrict exposed resources, investigate potential access, rotate affected secrets, strengthen document controls and verify patient-portal authorization using a controlled test environment.

**Prepared by:** Hafsa Khan  
**Programme:** NetworkWalks Academy — Week 04  
**Project:** Mediroza General Hospital — Web Application Penetration Testing
