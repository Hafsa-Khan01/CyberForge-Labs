# DG Interns Hub | Week 02
## Network Traffic Analysis, Nmap & Windows Security Telemetry

**Workstream:** Cybersecurity Internship  
**Coverage:** Packet analysis · Network discovery and scanning · Windows internals · Event logging · Introductory SOC investigation  
**Repository scope:** DG Interns Hub only

---

## 1. Technical scope

Week 02 focuses on observing network behaviour, interpreting scan activity and understanding the Windows event records used during security monitoring.

| Work area | Coverage |
|---|---|
| Packet analysis | Ethernet/IP/TCP fundamentals, TCP handshake and teardown, DNS, HTTP/TLS, ARP, ICMP and packet-level observations |
| Wireshark | Capture and display filters, protocol inspection, stream analysis and traffic interpretation |
| Nmap | Host discovery, port-scanning fundamentals, scan behaviour and output handling |
| Windows fundamentals | Processes, services, users and groups, registry, UAC, Event Viewer and core operating-system concepts |
| Security telemetry | Windows Security Event IDs, logon types, event interpretation and baseline awareness |
| Investigation practice | Reviewing packet captures, scan output, Windows events and PowerShell-collected records |

## 2. Repository structure

- **Study notes:** Topic-based technical reference material for networking, Nmap and Windows.
- **TryHackMe writeups:** Individual writeups for the assigned Further Nmap, host-discovery, port-scan and Windows learning rooms.
- **Practical writeups:** Wireshark, Nmap, Windows Event Viewer and PowerShell investigation exercises.
- **Capture analysis:** Notes for the supplied sample traffic captures, in the corresponding evidence set.
- **Cheat sheets:** Wireshark display-filter reference and Windows Event ID reference.
- **Evidence and reporting:** Original PCAP/PCAPNG files, screenshots, scan exports, CSV records, weekly report, presentation and LinkedIn drafts in the corresponding submission package.

## 3. Investigation and evidence standard

For each practical exercise, record:

1. **Objective and authorization** — define the lab task and confirm that the target or data source is in scope.
2. **Environment** — record the relevant host, operating system, tool and capture context.
3. **Method** — document the filters, scan options, commands or event queries used.
4. **Raw observation** — preserve the actual packet, scan output or event fields.
5. **Interpretation** — explain what the evidence supports; distinguish observation from inference.
6. **Limitations** — note visibility gaps, log-visibility constraints, encrypted payloads or other constraints.
7. **Evidence reference** — identify the original screenshot, capture or export.

Do not infer a vulnerability from an open port alone. Do not label traffic malicious without supporting indicators and context. Keep example commands separate from verified execution results.

## 4. Evidence handling

- Preserve original PCAP/PCAPNG files and exported scan or event records.
- Retain Nmap normal and XML output when those files are part of the original exercise.
- Keep PowerShell exports in their original format in the corresponding evidence set.
- Reference screenshots by their actual filenames and connect them to the relevant practical.
- Avoid publishing credentials, personal data or unrelated internship material.
- Perform intrusive or destructive actions only in an explicitly authorized, disposable lab environment.

## 5. Review checklist

- [ ] Packet-analysis notes explain the observed protocol behaviour.
- [ ] Wireshark filters are identified as capture filters or display filters correctly.
- [ ] Nmap procedures identify the scan purpose and options used.
- [ ] Windows notes distinguish event source, Event ID and event meaning.
- [ ] Logon types and event interpretations are not conflated.
- [ ] Practical conclusions are supported by the original evidence.
- [ ] Report and presentation accurately reflect completed work.

## 6. Scope and integrity

This directory is reserved for **DG Interns Hub Week 02**. NetworkWalks is a separate internship workstream and must remain completely untouched. Do not edit, rename, move, delete or reorganize any NetworkWalks files or folders.

Only DG Week 02 materials belong here. If an artifact is missing or an observation cannot be verified, state that limitation explicitly; never fabricate packet details, IP addresses, scan results, event records or completion claims.
