# Worked Example — Simulated Phishing Attempt

**FICTIONAL TRAINING SCENARIO. Not a real incident, captured sample or completed lab.**

## Summary
An employee reports an unexpected mailbox-warning email containing an unfamiliar sign-in link. Assume the employee did not click or submit credentials. Provisional severity is Medium (P3) until headers and URL evidence are validated.

## Illustrative timeline (PKT)
| Time | Event |
|---|---|
| 09:02 | Employee receives unexpected warning |
| 09:06 | Employee reports without clicking |
| 09:10 | Tier 1 preserves original .eml and headers |
| 09:18 | Analyst reviews sender alignment and safely enriches defanged URL |
| 09:30 | Mail administrator searches recipients and removes confirmed malicious copies |

## IOCs
No real indicators are supplied. Insert only values extracted from an actual sample; do not invent domains, hashes or IPs.

## ATT&CK
T1566.002 — Spearphishing Link, only if evidence confirms link-based phishing delivery. Do not map credential compromise without evidence.

## Severity and containment
P3 is provisional because the message was reported before interaction. Escalate if credentials were submitted, MFA abused, mailbox rules changed, privileged accounts affected or data accessed. Preserve the message, search recipients, quarantine confirmed copies, block verified indicators, revoke sessions/reset credentials if compromise is suspected, and inspect sign-in/mailbox-rule logs.

## Recommendations
Improve sender-authentication monitoring, phishing reporting, suspicious inbox-rule detections and out-of-band verification for payment or credential requests.

This example demonstrates structure only. Replace with an evidence-led case before submission.
