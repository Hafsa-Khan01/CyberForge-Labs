# PASSWORD CRACKING REPORT
## JOHN THE RIPPER (JTR) & NETWORKWALKS TOOLS

**W3-PM-FINAL | WEEK 03 | NETWORKWALKS**

| Report detail | Information |
|---|---|
| Prepared by | Hafsa Khan |
| Programme | NetworkWalks Academy — Cybersecurity & Ethical Hacking |
| Reporting period | Week 03 |
| Report date | 20 November 2026 |
| Modules | W3-PM1 — Password Cracking with JTR; W3-PM2 — Password Cracking with NetworkWalks Tools |
| Overall status | Both compulsory modules completed |
| Optional activities | Not attempted; excluded |

---

## 1. Executive Summary

This report documents the completion of both compulsory Week 03 practical modules. The exercises focused on recovering passwords from the password-protected PDF files supplied for the NetworkWalks training tasks and verifying recovery by opening the documents.

**W3-PM1** used John the Ripper Jumbo and its graphical frontend, Johnny, on Windows. Johnny was configured to use the John executable from the extracted Jumbo package. The PDF hash input was prepared and processed through the JTR workflow. Successful access to the protected training document was verified.

**W3-PM2** used the NetworkWalks Hash Calculator in PDF mode and the NetworkWalks Password Cracker. PDF-format hashes were extracted and submitted to the cracker. Three supplied PDFs were processed, and each document was successfully opened using its recovered password.

Both compulsory modules are complete. Optional activities were not performed and are not included in the completion count.

## 2. Objectives

1. Configure John the Ripper Jumbo for use through the Johnny graphical interface.
2. Prepare a PDF-compatible hash input for the JTR exercise.
3. Use the JTR workflow on the supplied authorised training PDF.
4. Extract PDF hashes with the NetworkWalks Hash Calculator.
5. Submit the extracted hashes to the NetworkWalks Password Cracker.
6. Verify successful password recovery by opening the supplied PDF documents.
7. Record the practical workflow and evidence requirements.

## 3. Scope, Environment and Tools

### 3.1 Scope

The work was limited to the password-protected PDF files supplied with the NetworkWalks Week 03 practical tasks. No third-party documents or accounts were targeted.

### 3.2 Environment and tools

| Environment / tool | Purpose |
|---|---|
| Windows 64-bit | PM1 practical environment |
| John the Ripper Jumbo | Command-line password recovery engine |
| Johnny GUI | Graphical interface for configuring and running John |
| NetworkWalks Hash Calculator — PDF mode | Extract PDF-compatible hashes |
| NetworkWalks Password Cracker | Perform the assigned PDF password recovery workflow |
| Web browser | Access the NetworkWalks tools |

## 4. W3-PM1 — Password Cracking with JTR

### 4.1 Objective

Recover the password of the supplied password-protected PDF using John the Ripper (JTR) and the Johnny graphical interface, as specified in the Week 03 Project Module 1 instructions.

### 4.2 Setup and configuration

1. Installed and opened the Johnny graphical interface.
2. Downloaded the Windows x64 John the Ripper Jumbo package.
3. Extracted the package and located the John executable in the package's `run` directory.
4. Configured Johnny to use the extracted `john.exe` executable rather than the Johnny installer.
5. Confirmed that Johnny detected the John Jumbo engine.

### 4.3 Hash preparation and recovery

The supplied PDF's PDF-format hash was prepared as a text input for the JTR workflow. The hash input was loaded through Johnny and the password recovery workflow was run against the authorised training file.

### 4.4 Verification

The recovered password was used to open the protected training PDF. Successful document access was confirmed.

**Result:** W3-PM1 completed. The JTR/Johnny setup and PDF password recovery workflow were carried out, and the protected document was successfully opened.

## 5. W3-PM2 — Password Cracking with NetworkWalks Tools

### 5.1 Objective

Recover the passwords of the three supplied password-protected PDF files using the NetworkWalks Hash Calculator and Password Cracker.

### 5.2 Procedure

1. Opened the NetworkWalks Hash Calculator.
2. Selected PDF mode and supplied each protected PDF.
3. Extracted the corresponding PDF-format hash, identified by the `$pdf$` prefix.
4. Copied the complete hash output for the relevant file.
5. Submitted each hash to the NetworkWalks Password Cracker.
6. Retrieved the password result for each supplied document.
7. Opened each PDF with its recovered password to verify successful access.

### 5.3 Results and verification

| Supplied document | Recovery result | Verification |
|---|---|---|
| PDF 1 | Password recovered | Document opened successfully |
| PDF 2 | Password recovered | Document opened successfully |
| PDF 3 | Password recovered | Document opened successfully |

All three supplied PDFs were successfully processed and opened. The recovered values were recorded in the private lab notes; raw hashes and recovered passwords are intentionally omitted from this public repository report.

**Result:** W3-PM2 completed. All three document recovery results were verified by opening the corresponding PDFs.

## 6. Completion Summary

| Compulsory module | Status |
|---|---|
| W3-PM1 — Password Cracking with JTR | Completed |
| W3-PM2 — Password Cracking with NetworkWalks Tools | Completed |

**Overall result: 2 of 2 compulsory modules completed.**

Optional activities were not attempted and are excluded from this report.

## 7. Key Learning Outcomes

- Understood the role of John the Ripper in authorised password-strength testing.
- Distinguished the John command-line engine from the Johnny graphical interface.
- Configured Johnny to use the John the Ripper Jumbo executable.
- Learned how PDF-compatible password hashes are prepared for a recovery workflow.
- Extracted PDF hashes using the NetworkWalks Hash Calculator.
- Used the NetworkWalks Password Cracker with the extracted PDF hashes.
- Verified password recovery by opening the supplied protected documents.
- Reinforced the importance of strong passwords for document protection.

## 8. Responsible Use and Evidence Handling

All activities described in this report were performed on files supplied for the NetworkWalks training exercise. Password recovery tools must only be used on documents the tester owns or is explicitly authorised to assess.

Screenshots should be retained in the matching evidence folders and reviewed before publication. Raw PDF hashes, recovered passwords, credentials, and unrelated personal information should not be committed to a public repository.

---

**Prepared by: Hafsa Khan**  
**NetworkWalks Academy — Week 03**
