# Repository Map

This page is the navigation guide for CyberForge Labs. Existing files remain in their current locations so that evidence history and established links are preserved.

## Top-level layout

```text
CyberForge-Labs/
├── DG Interns Hub/
│   ├── Week-01/       # Linux and networking foundations
│   ├── Week-02/       # Nmap, Wireshark and Windows security telemetry
│   ├── Week-03/       # Sysmon, auditd, Snort and log analysis
│   └── Week-04/       # SIEM and SOC study notes
├── Networkwalks/
│   ├── Week-01/       # VirtualBox/Kali and Wireshark SOC labs
│   └── Week-02/       # Footprinting, reconnaissance and scanning
├── Progress-Log/     # Chronological progress records
├── Skills-and-Notes/ # General technical reference material
├── docs/             # Existing portfolio/site assets
├── README.md         # Main entry point
├── SECURITY.md       # Responsible-use and security policy
└── .gitignore        # Local files and sensitive artifact exclusions
```

## Where new material belongs

| Material | Preferred location |
|---|---|
| DG Interns Hub weekly notes and write-ups | `DG Interns Hub/Week-XX/` |
| DG Interns Hub screenshots and lab evidence | The relevant week's `Evidence/` directory |
| NetworkWalks weekly deliverables | `Networkwalks/Week-XX/` |
| NetworkWalks screenshots and supporting files | The relevant practical's `Evidence/` directory |
| General reusable reference notes | `Skills-and-Notes/` |
| Dated progress entries | `Progress-Log/README.md` |
| Repository-wide navigation | Root `README.md` and this map |

## Maintenance rules

1. Do not delete evidence, reports, notes or code as part of routine organization.
2. Avoid moving or renaming established files; update navigation links instead.
3. Keep DG Interns Hub and NetworkWalks deliverables separate.
4. Preserve original evidence. If a clearer filename or index is needed, add a reference rather than silently replacing the source.
5. Verify every new relative link against the repository tree.
6. Keep credentials, tokens, private keys, VM images and unreviewed packet captures out of the public repository.
7. Record only verified work and clearly label incomplete or attempted tasks.

## Programme entry points

- [DG Interns Hub](DG%20Interns%20Hub/README.md)
- [NetworkWalks](Networkwalks/README.md)
- [Progress Log](Progress-Log/README.md)
- [Skills and Notes](Skills-and-Notes/README.md)
- [Security Policy](SECURITY.md)
