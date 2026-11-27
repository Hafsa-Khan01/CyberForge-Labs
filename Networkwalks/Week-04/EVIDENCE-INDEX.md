# Week 04 — Evidence Index

**Project:** Mediroza General Hospital — Black-box Web Application Penetration Test  
**Prepared by:** Hafsa Khan  
**Programme:** NetworkWalks Academy

## Evidence register

| Evidence ID | Phase | Evidence category | Reported purpose | Handling |
|---|---|---|---|---|
| M1-E01–M1-E04 | M1 — Reconnaissance and Network Enumeration | DNS, WHOIS, TLS, HTTP and network/service reconnaissance captures | Support domain and public-surface observations | Keep raw outputs private; sanitize before publication |
| M2-E01–M2-E02 | M2 — Patient Portal Assessment | Portal interface and PHP/MySQL error-related captures | Document portal observations and error disclosure; access-control concern remains unvalidated | Redact URLs, parameters and sensitive values |
| M3-E01–M3-E09 | M3 — PDF Document Password Security Testing | PDF hash/password-testing and document-open verification captures | Support the assessment of three protected PDF files | Private evidence only; never publish patient documents, contents, recovery hashes or passwords |
| M4-E01–M4-E03 | M4 — Legacy Directory and SQL Backup Exposure | Public directory and database-backup exposure captures | Support the legacy exposure observations | Private evidence only; exclude personal and financial records |

## Evidence status and limitations

This index describes the evidence categories referenced by the assessment report. It does not imply that every original screenshot or raw output is uploaded to this public repository. The detailed evidence set is maintained separately.

Before public upload, inspect each file and remove:
- Patient names, dates of birth, diagnoses, medical record numbers and report contents
- Employee and shareholder names, contact details, identity numbers, salaries and ownership information
- Credentials, recovered passwords, session identifiers, API keys and other secrets
- Raw database contents and any data that could identify an individual

## Evidence integrity

- Preserve original evidence in a restricted location.
- Do not alter original captures; create separately labelled redacted copies for approved publication.
- Keep report statements traceable to the corresponding original evidence ID.
- Distinguish confirmed observations from items that require further validation.
- Do not publish hashes or artefacts that would enable recovery of protected confidential documents.

## Public repository boundary

This repository is a sanitized presentation of the project. It intentionally excludes confidential source documents, patient records, employee/shareholder records, credentials and raw database backups.
