# LinkedIn Drafts

## Concept — How to spot a phishing email using headers

A phishing email can look convincing in the inbox. The raw headers provide useful clues before anyone interacts with the message.

Five checks I use when reviewing a suspicious email:

1. **Check the real sender:** compare the visible From address with the actual sending domain.
2. **Review Reply-To and Return-Path:** an unexpected mismatch deserves investigation.
3. **Follow the Received chain:** check mail-server hops and timestamps for inconsistencies.
4. **Read SPF, DKIM and DMARC together:** review both result and domain alignment. A pass alone does not make a message safe.
5. **Inspect links safely:** review the destination without clicking and keep URLs defanged in investigation notes.

The goal is to preserve evidence, verify context and make a decision using multiple signals—not one suspicious-looking field.

#PhishingAnalysis #EmailSecurity #SOC #CyberSecurity

## Weekly post — incident response summary

This week I focused on the analyst workflow behind phishing and endpoint investigations: preserving email evidence, checking authentication results, enriching indicators, reviewing safe malware-triage evidence and mapping observed behaviour to MITRE ATT&CK.

One important lesson: an IOC is useful, but understanding the behaviour behind it helps build detections that are harder to evade. I also worked on structuring an incident report around a timeline, scope, evidence, severity, containment and recommendations.

[Insert a short, evidence-backed summary of your actual incident case.]

[Attach your own ATT&CK Navigator screenshot after exporting the layer.]

Thanks to DG Interns Hub for the weekly learning structure.

#ThreatIntelligence #IncidentResponse #MITREATTACK #BlueTeam #DGInternsHub
