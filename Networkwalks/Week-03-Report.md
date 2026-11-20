# NetworkWalks — Week 03 Report
## Password Cracking with John the Ripper and NetworkWalks Tools

| Detail | Information |
|---|---|
| Prepared by | Hafsa Khan |
| Programme | NetworkWalks Academy |
| Week | Week 03 |
| Modules | W3-PM1 and W3-PM2 |
| Overall status | Both compulsory modules completed |

---

## 1. Overview

Week 03 focused on password recovery for the password-protected PDF files supplied with the NetworkWalks practical tasks. The work covered two compulsory modules: Password Cracking with John the Ripper (JTR) and Password Cracking with NetworkWalks Tools.

Both compulsory modules were completed. The optional activities were not attempted and are intentionally excluded from this report.

## 2. W3-PM1 — Password Cracking with JTR

**Objective:** Recover the password of the supplied protected PDF using John the Ripper (John) and its graphical interface, Johnny.

**Tools and environment:**
- Windows 64-bit
- John the Ripper Jumbo
- Johnny GUI
- PDF hash in John PDF format

**Work completed:**
1. Installed and opened the Johnny graphical interface.
2. Downloaded and extracted the John the Ripper Jumbo Windows x64 package.
3. Configured Johnny to use the John executable from the extracted `run` directory.
4. Confirmed that Johnny detected the John Jumbo engine.
5. Prepared the PDF hash file for the supplied training document.
6. Used the JTR workflow to recover the PDF password and verified access by opening the protected document.

**Result:** The compulsory JTR practical was completed and the supplied PDF files were successfully opened after password recovery.

## 3. W3-PM2 — Password Cracking with NetworkWalks Tools

**Objective:** Recover the passwords of the supplied protected PDF files using the NetworkWalks Hash Calculator and Password Cracker.

**Tools:**
- NetworkWalks Hash Calculator — PDF mode
- NetworkWalks Password Cracker
- Web browser

**Work completed:**
1. Opened the Hash Calculator and selected PDF mode.
2. Uploaded each supplied password-protected PDF to extract its PDF-format hash.
3. Copied the complete hash beginning with `$pdf$`.
4. Submitted the extracted hash to the NetworkWalks Password Cracker.
5. Retrieved the password result for each supplied PDF.
6. Opened the protected PDFs with the recovered passwords to verify successful access.

**Verification results:**

| Supplied file | Recovered password | Verification |
|---|---|---|
| PDF 1 | Recovered successfully | PDF opened |
| PDF 2 | Recovered successfully | PDF opened |
| PDF 3 | Recovered successfully | PDF opened |

The recovered password values are intentionally not reproduced in this public report.

**Result:** All three supplied PDF files were successfully processed, and successful document opening was confirmed.

## 4. Completion Summary

| Compulsory module | Status |
|---|---|
| W3-PM1 — Password Cracking with JTR | Completed |
| W3-PM2 — Password Cracking with NetworkWalks Tools | Completed |

**Overall result: 2 of 2 compulsory modules completed.**

Optional activities were not attempted and are not included in the completion count.

## 5. Key Learning Outcomes

- Understood the role of John the Ripper in password security testing.
- Configured the Johnny GUI to use the John the Ripper Jumbo engine.
- Learned how a password-protected PDF hash is represented in John-compatible format.
- Practised extracting PDF hashes using the NetworkWalks Hash Calculator.
- Used a password-cracking workflow to recover passwords from the assigned training files.
- Verified recovery by opening the supplied protected PDF documents.
- Reinforced the importance of strong passwords for protecting documents.

## 6. Responsible Use

All activities described in this report were performed on the files supplied for the NetworkWalks training exercise. Password recovery tools must only be used on files and systems that the tester owns or is explicitly authorised to assess. Recovered passwords and raw PDF hashes are not published in this repository.

---

**Prepared by: Hafsa Khan**  
**NetworkWalks Academy — Week 03**
