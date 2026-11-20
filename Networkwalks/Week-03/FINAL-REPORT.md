# NetworkWalks — Week 03
## Password Cracking with John the Ripper and NetworkWalks Tools

**Prepared by:** Hafsa Khan  
**Training programme:** NetworkWalks Academy

---

## 1. Overview

Week 03 covers password recovery for password-protected PDF training files. The essential modules use John the Ripper (John/Johnny) and the NetworkWalks Hash Calculator and Password Cracker.

## 2. Module results

| Module | Activity | Result |
|---|---|---|
| W3-PM1 | John the Ripper with Johnny GUI | In progress. John Jumbo is detected by Johnny and a PDF-format hash has been prepared. Hash loading, attack completion and PDF-open verification remain to be documented. |
| W3-PM2 | NetworkWalks Hash Calculator and Password Cracker | Completed. PDF hashes were extracted, password recovery was performed, and the supplied documents were reported as opening successfully. |
| W3-OPTIONAL1 | AI-JTR with Claude and Hexstrike MCP | Not started |
| W3-OPTIONAL2 | Mediroza hospital patient portal | Not started; requires a clearly authorised, isolated training target |

## 3. PM1 — John the Ripper

Johnny GUI was installed and configured to use the extracted John the Ripper Jumbo Windows x64 engine. Johnny displayed the detected Jumbo engine. A PDF-format hash was prepared for the supplied training file. The attack and document verification have not yet been confirmed, so PM1 remains in progress.

## 4. PM2 — NetworkWalks Tools

The PDF mode of the NetworkWalks Hash Calculator was used to generate a PDF password hash. The hash was submitted to the NetworkWalks Password Cracker. Password recovery and successful opening of the supplied protected documents were reported. Recovered passwords are omitted from this public report.

## 5. Evidence and limitations

Original evidence screenshots are to be added under the relevant module Evidence directories. This report does not claim that screenshots have already been uploaded. No recovered passwords, password hashes or locked source PDFs are included.

## 6. Responsible-use statement

The exercises are limited to the files supplied for the NetworkWalks training tasks. Password recovery must not be applied to files, accounts or systems without permission. The optional Mediroza activity must not be performed against a live hospital service or real patient data; proceed only with explicit authorisation for an isolated training environment.

---

**Current status:** PM2 completed; PM1 in progress; both optional modules not started.
