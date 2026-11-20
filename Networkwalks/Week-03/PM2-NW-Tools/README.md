# W3-PM2 — Password Cracking with NetworkWalks Tools

**Tools:** NetworkWalks Hash Calculator and NetworkWalks Password Cracker  
**Status:** Completed — practical result and document opening reported

## Objective

Extract the PDF password hash using the NetworkWalks Hash Calculator, submit the PDF hash to the NetworkWalks Password Cracker, and verify the recovered password by opening the supplied password-protected PDF.

## Work record

- Selected the PDF mode in the NetworkWalks Hash Calculator.
- Generated a PDF hash in `$pdf$` format for the supplied lab document.
- Submitted the complete PDF hash to the NetworkWalks Password Cracker.
- Recovered passwords for the tested lab documents.
- Confirmed that the protected documents opened successfully with the recovered passwords.

The recovered passwords are intentionally not reproduced in this public write-up.

## Evidence

See [PM2 evidence folder](Evidence/README.md).

## Notes

- The MD5/SHA text hashes shown when the calculator is in Text mode are not PDF password hashes and were not used as the PDF hash input.
- Store only redacted screenshots in the public repository.
- Do not commit PDF hashes, recovered passwords, source PDFs, or private files.
