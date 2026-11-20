# 05 — IOC vs IOA and the Pyramid of Pain

- **IOC (Indicator of Compromise):** an artefact associated with a possible or confirmed compromise, such as a file hash, IP, domain, URL or registry key. IOCs are useful for searching and blocking but can be copied, rotated or shared by benign infrastructure.
- **IOA (Indicator of Attack):** a behaviour or sequence suggesting an attack is happening, such as Office spawning PowerShell followed by suspicious network activity. IOAs focus on actions and context rather than a single artefact.

## Pyramid of Pain

| Level (bottom to top) | Example | Attacker effort to change | Defensive value |
|---|---|---|---|
| Hash values | SHA-256 of a payload | Trivial: rebuild or modify file | Low |
| IP addresses | C2 or staging IP | Easy: rotate infrastructure | Low–moderate |
| Domain names | C2 or phishing domain | Easy–moderate: register another domain | Moderate |
| Network/host artefacts | Specific URI, mutex, registry path | Moderate: alter implementation | Moderate–high |
| Tools | Malware family or operator toolset | Harder: replace tooling and workflows | High |
| TTPs | Credential theft, scheduled task persistence, lateral movement pattern | Hard: change behaviour and operational method | Very high |

The Pyramid of Pain is a prioritisation model, not a guarantee. Behavioural detections can be more durable, but they need quality telemetry and tuning to avoid false positives.
