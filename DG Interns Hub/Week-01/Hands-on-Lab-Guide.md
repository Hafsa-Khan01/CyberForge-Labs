# Week 1 — Hands-on Lab Guide

## Safe Lab Preparation
1. Create isolated VirtualBox VMs for Kali, Ubuntu and/or Windows.
2. Prefer Host-only or a dedicated NAT Network for intentionally vulnerable practice targets.
3. Take a clean snapshot before exercises.
4. Confirm the target belongs to your lab and document its assigned address.

## Connectivity and Network Discovery
Use commands appropriate to the installed operating system:
- Linux interface and routes: `ip a`, `ip route`
- Reachability: `ping <lab-target>`
- Route path: `traceroute <lab-target>`
- DNS lookup: `nslookup <name>` or `dig <name>`

Record the actual output, interface, gateway and DNS resolver. Do not replace real results with example values.

## Linux Administration Practice
In a disposable lab VM:
- Create three test users and two test groups.
- Create a shared directory and configure group ownership and least-privilege permissions.
- Practice `find`, `grep`, `ps` and `ss -tulpn`.
- Create and verify a simple cron job.
- Capture terminal output for the command exercise.

## Evidence Checklist
- VM network mode and topology diagram.
- Snapshot / VM configuration evidence.
- User, group and shared-directory permission evidence.
- Command outputs and cron verification.
- Network discovery outputs.
- Short notes explaining what each result demonstrates.

Only include genuine screenshots and command output from the lab. Redact credentials, tokens and personal data.
