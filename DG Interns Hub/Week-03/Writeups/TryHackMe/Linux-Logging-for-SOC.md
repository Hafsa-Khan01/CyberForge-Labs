# TryHackMe — Linux Logging for SOC

## Scope
Linux logging sources, authentication records, system activity and the value of centralized log review in SOC operations.

## Technical focus
- Identify authentication and system log locations used by common Linux distributions.
- Read timestamps, host/process context, severity and event messages.
- Distinguish authentication activity from general service and kernel messages.
- Correlate related records by timestamp, account, source address and process context.

## Investigation workflow
1. Identify the distribution and its logging configuration.
2. Review relevant files under `/var/log/` and the systemd journal where applicable.
3. Filter a narrow time window and preserve the original event context.
4. Compare successful and failed authentication activity; look for unusual source addresses, repeated failures and unexpected privilege use.
5. Record the evidence, interpretation, limitations and follow-up checks.

## SOC relevance
Authentication logs can support investigations into brute-force attempts, account misuse, privilege escalation and suspicious remote access. A single event is rarely sufficient to establish malicious activity; correlate with endpoint, network and identity telemetry.

## Evidence record
Attach the original TryHackMe room-completion screenshot and any permitted task evidence. Record the completion state and date accurately. Do not substitute illustrative terminal output for room evidence.

## References
- Linux Audit documentation: https://github.com/linux-audit/audit-documentation
- systemd journal: https://www.freedesktop.org/software/systemd/man/latest/journalctl.html
