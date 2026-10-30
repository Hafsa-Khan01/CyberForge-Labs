# TryHackMe Write-up — Basic Port Scans

## Objective
Understand TCP port states and common scan methods.

## Concepts
- Open: an application is accepting connections/probes.
- Closed: the host responds but no application is listening.
- Filtered: probes are blocked or no decisive response is received.
- SYN scan sends an initial SYN and interprets the response.
- Connect scan completes the operating system's TCP connection process.

## Method
Scan only the authorized practice host, record target and time, compare scan types, and save output for reproducibility.

## Learning Reflection
Port state is an observation from a specific vantage point and time. It should not be confused with a confirmed vulnerability.
