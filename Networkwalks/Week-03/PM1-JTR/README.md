# W3-PM1 — Password Cracking with JTR

**Tooling:** John the Ripper Jumbo (CLI engine) and Johnny (GUI)  
**Platform used:** Windows 64-bit  
**Status:** In progress

## Objective

Use John the Ripper and its Johnny graphical interface to recover the password of the NetworkWalks-provided, password-protected PDF, then verify that the supplied PDF opens with the recovered password.

## Work record

- Johnny GUI installed and launched.
- John the Ripper Jumbo Windows x64 package extracted.
- Johnny configured to point to the John engine in the extracted `run/john.exe` location.
- Johnny displayed the detected Jumbo engine.
- A PDF hash in John PDF format (`$pdf$`) was prepared for the lab file.
- Hash-file loading, attack completion and PDF-open verification are still pending confirmation.

## Remaining verification

1. Save the complete lab hash as a one-line `hash1.txt` file.
2. Load `hash1.txt` through Johnny's **Open password file** option.
3. Start a new attack using the lab's supplied file and an appropriate wordlist/attack configuration.
4. Record the result shown by John/Johnny.
5. Open the same supplied PDF with the recovered password and capture a verification screenshot.

Do not mark the exercise complete until the recovery result and successful PDF opening have both been verified.

## Evidence

See [PM1 evidence folder](Evidence/README.md).

## Handling note

Do not publish the actual PDF hash, recovered password, source PDF, or personal files. Keep those items locally and include only redacted screenshots in the public repository.
