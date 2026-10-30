# TryHackMe Write-up — Further Nmap

## Objective
Extend basic Nmap knowledge to service/version detection, OS detection, scan behaviour and output handling.

## Techniques to Understand
- `-sS`: TCP SYN scan.
- `-sT`: TCP connect scan.
- `-sU`: UDP scan.
- `-sV`: service/version detection.
- `-O`: OS detection.
- `-A`: enables several advanced detection features.

## Method
Confirm written authorization and target scope, identify the lab host, choose the least intrusive scan that answers the question, save normal/XML output, and review the results. Interpret filtered and closed ports carefully.

## Learning Reflection
Nmap output is evidence about the scan's observations at a particular time, not a guarantee that a service is always available or vulnerable. Validate versions and findings independently.
