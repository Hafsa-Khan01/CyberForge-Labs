# 06 — MITRE ATT&CK vs Cyber Kill Chain

## Structure
- **Tactic:** the adversary's goal or “why” (for example Initial Access, Execution, Persistence).
- **Technique:** the general method used to achieve a goal.
- **Sub-technique:** a more specific method under a technique, such as PowerShell (T1059.001).
- ATT&CK is a knowledge base of behaviours across tactics; it is not a strictly linear sequence.

The **Cyber Kill Chain** is a seven-stage intrusion model: Reconnaissance, Weaponization, Delivery, Exploitation, Installation, Command and Control, and Actions on Objectives. It gives a high-level progression view; real attacks may skip, repeat or combine phases. ATT&CK provides more granular behaviours and defensive mappings.

## Example mapping to earlier lab themes

| Attack observed / lab activity | Kill Chain phase (approx.) | ATT&CK technique |
|---|---|---|
| Nmap service discovery in an authorised lab | Reconnaissance | T1046 — Network Service Discovery |
| Repeated authentication failures / brute-force simulation | Exploitation / credential access stage (context-dependent) | T1110 — Brute Force |
| PowerShell execution during endpoint testing | Exploitation / execution | T1059.001 — PowerShell |
| Creation of a local account during an atomic test | Installation / persistence or privilege setup (context-dependent) | T1136.001 — Create Account: Local Account |
| Scheduled task creation during an atomic test | Installation / persistence | T1053.005 — Scheduled Task |

These are mappings of lab themes and intended tests, not claims that each event was observed. In the final layer, keep only techniques supported by actual evidence and cite the log source/rule.
