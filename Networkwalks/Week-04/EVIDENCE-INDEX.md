# Week 04 — Evidence Index

**Project:** Mediroza General Hospital — Black-box Penetration Testing  
**Prepared by:** Hafsa Khan

## Evidence register

| Evidence ID | Activity | Evidence file | What it records | Status |
|---|---|---|---|---|
| M1-E01 | Passive reconnaissance | `M1-Passive-Recon.txt` | DNS, WHOIS, TLS and initial HTTP observations | Captured locally |
| M1-E02 | Reconnaissance checks | `M1-Phases-1-3.txt` | Initial public-surface checks; includes command environment errors | Captured locally; retain as raw record |
| M1-E03 | Corrected public endpoint review | `M1-Phase3-Corrected.txt` | HTTP status checks and publicly exposed page links/forms | Captured locally |
| M1-E04 | Public login-page review | `M1-Phase4-Login-Review.txt` | Staff/patient login page status, form methods and visible fields | Captured locally |
| M1-E05 | Browser screenshots | Not uploaded | Visual confirmation of publicly accessible login pages | Not yet supplied |

## Evidence handling

- The command outputs are currently in the local Week 04 working directory and have not yet been uploaded here.
- Review and redact credentials, personal information, tokens and any sensitive data before committing screenshots or logs.
- Keep original raw outputs separate from edited report summaries.
- Do not include patient records, employee salary details, shareholder data or other confidential information in this public repository.

## Current scope of documented work

The available evidence supports public reconnaissance and non-invasive login-page inspection only. It does not demonstrate authentication bypass, restricted-area access, retrieval of patient PDFs, PDF decryption, or confidential data exposure.
