# 08 — Incident Reports, Severity and Escalation

## Required incident report content
1. Executive summary: what happened, when, affected service/users and current status.
2. Scope and timeline: timestamp with timezone, source, action and analyst interpretation.
3. Evidence and IOCs: defanged values, hashes, reputation sources, confidence and collection time.
4. ATT&CK mapping: technique ID, observed behaviour and supporting telemetry.
5. Impact: confidentiality, integrity, availability, business process and data exposure.
6. Containment and eradication: action, owner, timestamp, result and residual risk.
7. Recovery: validation, monitoring period and approval.
8. Recommendations: preventive, detective and response improvements with owners/priorities.

## Example severity model (adapt to organisation policy)

| Severity | Typical criteria | Escalation |
|---|---|---|
| Critical / P1 | Confirmed widespread compromise, privileged account takeover, active ransomware or major sensitive-data exfiltration | Immediate incident commander, security leadership and business continuity |
| High / P2 | Confirmed endpoint compromise, successful credential theft, lateral movement or high-impact targeted BEC | Urgent Tier 2/IR escalation; isolate affected assets and notify owners |
| Medium / P3 | Credible malicious attempt blocked, limited scope, no confirmed execution or impact | Tier 1 investigation with Tier 2 review as needed |
| Low / P4 | Benign event, low-confidence indicator or policy violation with no compromise evidence | Document, tune and close under standard workflow |

Severity depends on business impact, confidence, scope, asset criticality and active threat—not merely the number of alerts. Follow local escalation policy.

## Copy-ready report template
Use [Incident Report/Incident-Report-Template.md](../Incident%20Report/Incident-Report-Template.md).
