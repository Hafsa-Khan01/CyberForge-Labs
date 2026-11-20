# Week 03 — Evidence Index

**Prepared by:** Hafsa Khan  
**Programme:** NetworkWalks Academy — Cybersecurity & Ethical Hacking  
**Overall status:** All compulsory practicals and verification activities completed

This index records the evidence for both compulsory Week 03 modules: PM1 (John the Ripper) and PM2 (NetworkWalks Tools). Evidence files have been renamed consistently and arranged by module.

## Repository evidence structure

```text
Networkwalks/Week-03/
├── Evidence/
│   ├── PM1-JTR/
│   └── PM2-NW-Tools/
├── Report/
├── README.md
├── FINAL-REPORT.md
└── EVIDENCE-INDEX.md
```

## Evidence register

| Evidence ID | Module | Required artifact | What it demonstrates | Repository location | Status |
|---|---|---|---|---|---|
| PM1-E01 | PM1 | [Johnny/JTR setup and executable configuration](Evidence/PM1-JTR/PM1-03-Johnny-Jumbo-Executable-Configured.jpeg) | Johnny detects the John Jumbo executable from the extracted `run` directory | `Evidence/PM1-JTR/` | Completed |
| PM1-E02 | PM1 | [Johnny installation and configuration evidence](Evidence/PM1-JTR/PM1-02-Johnny-Installer-Ready.jpeg) and [configured executable](Evidence/PM1-JTR/PM1-03-Johnny-Jumbo-Executable-Configured.jpeg) | Johnny installation and correct JTR engine configuration | `Evidence/PM1-JTR/` | Completed |
| PM1-E03 | PM1 | JTR hash-input and recovery workflow | Supplied PDF hash preparation and successful JTR recovery workflow; password-bearing result image intentionally withheld from the public repository | Private lab evidence; public setup context in `Evidence/PM1-JTR/` | Completed |
| PM1-E04 | PM1 | [Successful protected-PDF opening](Evidence/PM1-JTR/PM1-05-PDF-Recovery-Verified.jpeg) | Recovered password successfully opened the supplied training PDF | `Evidence/PM1-JTR/` | Completed |
| PM2-E01 | PM2 | PDF hash extraction in NetworkWalks Hash Calculator | PDF-mode hash extraction was performed; raw hash screenshot is intentionally withheld from the public repository | Private lab evidence | Completed |
| PM2-E02 | PM2 | NetworkWalks Password Cracker results | Password recovery was completed for all three supplied PDFs; screenshots displaying passwords or raw hashes are intentionally withheld | Private lab evidence | Completed |
| PM2-E03 | PM2 | [PDF 1 opened successfully](Evidence/PM2-NW-Tools/PM2-04-PDF1-Opened.jpeg) and [PDF 2 opened successfully](Evidence/PM2-NW-Tools/PM2-06-PDF2-Opened.jpeg) | Successful document access verification for PDFs 1 and 2 | `Evidence/PM2-NW-Tools/` | Completed |
| PM2-E04 | PM2 | [PDF 3 opened successfully](Evidence/PM2-NW-Tools/PM2-08-PDF3-Opened.jpeg) | Successful document access verification for PDF 3 | `Evidence/PM2-NW-Tools/` | Completed |

## Completion checklist

- [x] John the Ripper Jumbo and Johnny installed and configured.
- [x] Johnny configured to use the correct John Jumbo executable.
- [x] PM1 PDF hash preparation and recovery workflow completed.
- [x] PM1 protected PDF opened successfully.
- [x] NetworkWalks Hash Calculator used in PDF mode.
- [x] Password Cracker used for all three supplied PDFs.
- [x] PDF 1 opened successfully.
- [x] PDF 2 opened successfully.
- [x] PDF 3 opened successfully.
- [x] Evidence reviewed, renamed, and organized by module.
- [x] Exact duplicate copies removed.
- [x] Public evidence reviewed for sensitive values.

## Evidence handling

The practical work is complete. Screenshots that expose recovered passwords or raw PDF hashes have been excluded from the public repository to avoid publishing sensitive exercise data. The corresponding activities are recorded as completed; the original unredacted evidence should remain in private lab storage. Public screenshots show setup and successful document verification without publishing recovered credentials or raw hashes.

All activities were performed only on the files supplied for the NetworkWalks training exercise. Optional activities were not attempted and are intentionally excluded.
