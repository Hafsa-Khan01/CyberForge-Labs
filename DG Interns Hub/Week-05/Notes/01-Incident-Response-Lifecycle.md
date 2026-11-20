# 01 — NIST Incident Response Lifecycle

NIST SP 800-61 Rev. 2 describes four connected phases. Preparation happens before an incident; the remaining phases guide the response and improvement.

| Phase | Purpose | Analyst actions | Outputs |
|---|---|---|---|
| Preparation | Build readiness before an incident | Define roles, contacts, escalation paths, playbooks, logging, backups, asset inventory, forensic tooling and exercises | Contact tree, response plan, baselines, tested tools |
| Detection and Analysis | Decide whether an event is an incident and understand scope | Validate alerts, preserve evidence, build timeline, identify affected users/hosts, collect IOCs, assess confidence and severity | Triage notes, incident declaration, scope and initial hypothesis |
| Containment, Eradication and Recovery | Limit damage, remove cause and restore safely | Isolate affected endpoint/account, block confirmed IOCs, disable compromised credentials, remove persistence, patch root cause, restore known-good systems and monitor | Containment record, eradication evidence, recovery approval |
| Post-Incident Activity | Learn and reduce recurrence | Conduct lessons-learned review, measure response, improve detections/playbooks, assign owners and due dates | Final report, corrective-action register, updated controls |

## Practical principles
- Preserve evidence before making changes where doing so will not increase harm.
- Containment should be proportionate: isolate a confirmed compromised host, but avoid broad blocking based on one weak indicator.
- Record who performed each action, when, why and the result.
- Recovery is not complete until monitoring shows the threat has not returned.

**Reference:** NIST SP 800-61 Rev. 2, Computer Security Incident Handling Guide.
