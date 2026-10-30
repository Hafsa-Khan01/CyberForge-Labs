# Practical Write-up — Nmap Scan Exercise

## Objective
Perform authorized host discovery and port/service identification against assigned Ubuntu and Windows lab VMs.

## Procedure
1. Confirm the exact target addresses and written scope.
2. Perform host discovery with `-sn`.
3. Compare an authorized SYN scan (`-sS`) or connect scan (`-sT`).
4. Use `-sV` for service/version identification and `-O` for OS fingerprinting where permitted.
5. Use `-A` only when the additional probes are within scope.
6. Save normal and XML output using `-oN` and `-oX`.

## Analysis
Document open, closed and filtered states separately. Record actual service names and version strings from the output. Do not infer a vulnerability solely from a port number or banner.

## Evidence
Attach the real command output and packet capture. Include target, date/time, command, scan limitations and remediation observations.
