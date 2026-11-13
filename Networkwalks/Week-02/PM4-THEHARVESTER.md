# W2-PM4 — theHarvester Footprinting

**Programme:** NetworkWalks Cybersecurity & Ethical Hacking  
**Week:** 02  
**Status:** Attempted — output not independently validated

## Official assignment

The official PM4 task uses `microsoft.com` and specifies these commands:

```bash
theHarvester -d microsoft.com -l 1000 -b baidu
theHarvester -d microsoft.com -l 50 -b all
```

The task is to collect publicly available domain-related information using theHarvester data sources.

## Additional target reported

The user also reported running theHarvester against `networkwalks.com`. This is an additional target and does not replace the official `microsoft.com` assignment.

## Execution notes

- The Baidu source returned a server-disconnection error during the recorded attempt.
- Subsequent troubleshooting involved XML/proxy and YAML-related errors.
- Successful final output files and screenshots were not available for verification at the time this document was prepared.
- No email addresses, subdomains, IP addresses, host counts, or other findings are claimed without the original output.

## Evidence required to finalize findings

- [ ] Screenshot of the Microsoft Baidu-source command and complete output.
- [ ] Saved text output for the Microsoft Baidu-source task, if generated.
- [ ] Screenshot of the Microsoft all-sources command and complete output.
- [ ] Saved text output for the Microsoft all-sources task, if generated.
- [ ] Output/screenshot for the additional NetworkWalks-domain run, if retained.

**Reporting note:** PM4 is recorded as attempted, not as a verified successful enumeration. Update the findings only after reviewing the original terminal output or saved result files.
