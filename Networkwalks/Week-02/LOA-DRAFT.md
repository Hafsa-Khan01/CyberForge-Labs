# Letter of Authorization — Draft for Issuer Review

<aside>
**DRAFT / NOT APPROVED / NOT AN AUTHORIZATION**

This document is a preparation template based on the sample LOA shown in the NetworkWalks Week 02 assignment. It does not grant permission to test any system. Testing must not begin until the target owner / NetworkWalks issues and signs a current authorization with a clearly defined scope.
</aside>

## 1. Reference details

| Field | To be completed by issuer |
|---|---|
| Reference number | [Issuer to assign] |
| Issue date | [DD Month YYYY] |
| Client / target owner | [Confirm legal / organisation name] |
| Authorized tester | Hafsa Khan — [issuer to verify identity and details] |
| Programme / batch | NetworkWalks Cybersecurity Internship — [confirm batch] |
| Valid from | [Start date and time, timezone] |
| Valid until | [End date and time, timezone] |
| Issuing authority / contact | [Name, role and official contact] |

## 2. Exact authorized scope

The issuer must explicitly list each approved asset. Do not assume that the sample letter's scope automatically applies.

| Asset type | Exact value to be approved |
|---|---|
| Domain / subdomain names | [Exact FQDNs; list each one] |
| IP addresses / CIDR ranges | [Exact addresses/ranges, if applicable] |
| DNS records / services | [Specify permitted record types and limits] |
| Local lab assets | [Exact VM names/IPs and network range, if applicable] |
| Third-party hosted assets | [Explicitly include only with provider/owner approval] |
| Out-of-scope assets | [List exclusions] |

**Scope confirmation:** No wildcard, adjacent host, third-party service, shared hosting tenant, cloud platform or discovered asset is included unless the issuer explicitly lists or approves it in writing.

## 3. Authorized activities

The issuer must mark and define each permitted activity. These are proposed categories for review, not pre-approved actions.

- [ ] Passive footprinting / public-source research
- [ ] DNS lookups / specified DNS enumeration
- [ ] GHDB query research limited to approved scope and non-invasive verification
- [ ] Maltego relationship mapping using approved data sources
- [ ] theHarvester collection for explicitly approved domains
- [ ] Zenmap / Nmap host discovery and port or service scanning on explicitly approved IPs
- [ ] Other: [Describe exact technique and limits]

## 4. Prohibited activities unless separately and explicitly authorized

- Exploitation, gaining unauthorized access or privilege escalation.
- Denial-of-service, stress testing or actions that may disrupt availability.
- Password guessing, brute-force, credential stuffing or authentication attacks.
- Social engineering, phishing or contacting staff/users under false pretences.
- Accessing, copying, modifying or deleting data that is not necessary and explicitly approved.
- Testing third-party systems or infrastructure outside the written scope.
- Any activity prohibited by the issuer or applicable law.

## 5. Operational conditions

| Condition | Issuer-approved value |
|---|---|
| Approved testing window / timezone | [Specify] |
| Source IP / testing environment | [Specify] |
| Rate limits / concurrency | [Specify] |
| Emergency contact | [Specify] |
| Stop-work trigger and reporting channel | [Specify] |
| Evidence retention / deletion | [Specify] |
| Data handling and disclosure requirements | [Specify] |

The tester must stop immediately if requested by the issuer, if an unexpected disruption occurs, or if activity appears to leave the approved scope. Findings must be handled confidentially and reported only through the agreed channel.

## 6. Acknowledgement and approval

**Authorized by target owner / NetworkWalks**

- Name: [Issuer]
- Title: [Role]
- Organisation: [Organisation]
- Signature / official approval: [Issuer completes]
- Date and time: [Issuer completes]

**Acknowledged by tester**

- Name: Hafsa Khan
- Signature: [Tester completes after reviewing the final approved scope]
- Date: [DD Month YYYY]

---

## Important handling note

Keep the signed authorization in a private, access-controlled location. Do not publish the signed copy, signatures, personal phone numbers, email addresses or confidential asset lists in this public GitHub repository unless the issuer has expressly approved publication. A redacted proof of authorization may be referenced in the final report only if publication is permitted.

**Current status: Awaiting issuer confirmation. No active testing permission is represented by this draft.**
