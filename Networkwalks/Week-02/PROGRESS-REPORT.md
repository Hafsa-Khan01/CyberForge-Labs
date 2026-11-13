# NetworkWalks Week 02 — Evidence-Based Progress Report

**Prepared by:** Hafsa Khan  
**Programme:** NetworkWalks Cybersecurity Internship  
**Assessment:** Week 02  
**Report status:** Evidence-review draft — not yet a submission-ready final report  
**Assignment deadline:** 23:00, Friday 13 November 2026 (Pakistan time, as stated in the assignment brief)

## 1. Executive summary

This report records the Week 02 practical work reviewed to date. The documented work covers:

- **W2-PM1:** Footprinting with multiple Kali Linux tools against `networkwalks.com`.
- **W2-PM4:** A theHarvester run against `github.com`. This is recorded as a tool demonstration only; it must not be counted as NetworkWalks-target assessment evidence unless the written authorization explicitly includes that domain.
- **W2-PM5:** Zenmap screenshots showing scans of private/local network ranges. The exact approved range and authorization coverage must be checked before these scans are represented as in-scope assessment results.

PM2 (GHDB) and PM3 (Maltego) were not completed because of a Kali desktop display issue. They are therefore excluded from completed-work claims.

The assignment brief requires at least one elective from PM1–PM4 and both essential modules, PM5 and PM-FINAL. PM1 provides an elective workstream. PM5 evidence and scope still require final validation, and this document is a draft rather than a claim that every submission requirement has been conclusively met.

## 2. Authorization and scope

The assignment PDF contains a **sample** Letter of Authorization. That sample is not the tester's own authorization.

The tester has stated that permission was provided separately by NetworkWalks. The signed authorization and its complete scope were not available for independent review while preparing this repository report. Consequently:

- The PM1 domain observations below are documented as the results of the commands shown.
- The theHarvester run against `github.com` is kept separate from NetworkWalks-target findings.
- Private IP ranges in Zenmap screenshots are not assumed to be authorized merely because they are private or reachable from the lab.
- No claim is made that a target, IP range, method, date, or scan intensity is authorized unless it is covered by the current written permission.

Keep the signed authorization private unless its issuer expressly permits publication. Before submission, privately compare every active scan target and method with the authorization's approved assets, testing window, exclusions, and rate limits.

## 3. Test environment and tools

The Kali environment information previously captured was:

| Item | Observed environment |
|---|---|
| Operating system | Kali GNU/Linux Rolling 2025.4 |
| Shell | zsh |
| Virtualization | VMware virtual machine |
| Kali interface | `eth0` |
| Previously observed Kali address | `192.168.239.128/24` (verify current address before any further scan) |
| Nmap | 7.95 (x86_64 Linux) |
| theHarvester | 4.21.2 |

The following PM1 tools were present in the Kali environment: WHOIS, WhatWeb, nslookup, cURL, wafw00f, and DNSRecon.

## 4. Module results

### 4.1 W2-PM1 — Footprinting with multiple Kali tools

**Objective:** Collect publicly available domain-registration, DNS, HTTP-response, technology-fingerprint, and DNS-security-control information for the specified domain.

**Target recorded:** `networkwalks.com`

**Commands recorded as executed:**

```bash
whois networkwalks.com
nslookup -type=A networkwalks.com
nslookup -type=AAAA networkwalks.com
nslookup -type=MX networkwalks.com
nslookup -type=NS networkwalks.com
nslookup -type=TXT networkwalks.com
curl -I https://networkwalks.com
curl -I http://networkwalks.com
whatweb --aggression=1 https://networkwalks.com
wafw00f https://networkwalks.com
dnsrecon -d networkwalks.com -t std
```

**Observed results from the reviewed screenshots/output:**

| Tool | Observation | Interpretation / caution |
|---|---|---|
| WHOIS | GoDaddy was shown as registrar; registration and expiry information appeared in the output; registrant details were privacy-protected. | Registration metadata is informational and does not establish a security weakness. |
| NSLOOKUP | An A record was shown resolving to `192.232.216.135`; MX information was also visible in the reviewed output. | DNS answers can change; preserve the original dated capture with the report. |
| cURL | The HTTPS response returned HTTP `200 OK`; the response headers identified Apache. | A successful HTTP response is not a vulnerability finding. Header observations are limited to the response captured at test time. |
| WhatWeb | The output identified WordPress `7.1.4`, Apache, and WP Download Manager. | This is a tool fingerprint, not independent confirmation that every component/version is accurate or vulnerable. Verify versions with an authoritative source before making a vulnerability claim. |
| WAFW00F | The tool reported ModSecurity (SpiderLabs) as detected. | This is a detection result from the tool, not proof of the WAF's complete configuration, effectiveness, or coverage. |
| DNSRecon | The output reported eight DNS records and displayed SOA, NS, MX, A, TXT and SRV-related information. | Record counts and values should be checked against the original output. A missing DNSSEC response in a query is not, by itself, proof that DNSSEC is disabled. |

**Analysis:** The collected information provides a basic public-facing footprint of the domain, including registration metadata, DNS records, HTTP response headers, web-technology fingerprints, and a WAF detection result. These observations can inform later defensive review, but none of the results above independently proves an exploitable vulnerability.

**Limitations:** The report does not claim exploitation, authenticated testing, vulnerability validation, or access to private resources. DNS and web fingerprints are time-sensitive and may change. The original screenshots/output should be retained privately and attached to the final submission after redaction.

### 4.2 W2-PM2 — GHDB-based Footprinting Attacks

**Status:** Not completed.

No Google Hacking Database queries or search-result screenshots were reviewed for this report. This module is not represented as completed.

### 4.3 W2-PM3 — Maltego-based Footprinting Attacks

**Status:** Not completed.

No Maltego graph, transform output, or screenshots were reviewed for this report. This module is not represented as completed.

### 4.4 W2-PM4 — theHarvester-based Footprinting Attacks

**Objective:** Demonstrate theHarvester's collection of publicly indexed domain-related OSINT from selected sources.

**Target in reviewed screenshot:** `github.com` — not `networkwalks.com`.

**Tool/version:** theHarvester 4.21.2.

**Sources visible in the reviewed output:** DuckDuckGo, CertSpotter, and crt.sh.

**Observed result:** The screenshot showed 59 hosts/subdomains. The displayed output did not show IP addresses, email addresses, or people.

**Scope classification:** This run is recorded as a separate tool demonstration. It is not counted as NetworkWalks-target footprinting evidence unless the current written authorization or assignment instructions expressly include `github.com`. A module requirement to use theHarvester does not, by itself, authorize scanning or collecting information about an unrelated third-party domain.

**Limitations:** Only the displayed output is summarized here. No claim is made that the result is exhaustive or that the discovered hostnames are live, owned by the same organization, or in scope.

### 4.5 W2-PM5 — Zenmap-based Network Scanning

**Status:** Screenshots were captured and reviewed, but the target/scope and scan-profile checks remain open.

**Targets/ranges visible in the screenshot set included private/local addresses and ranges such as:**

- `192.168.56.0/24`
- `10.0.0.0/28`
- individual private IP addresses, including `10.0.0.4`

At least one screenshot showed an aggressive Nmap option set containing `-T4 -A`.

**Analysis:** The screenshots demonstrate use of Zenmap/Nmap against private or local network targets and include scan/topology views. However, the screenshots alone do not establish that each range belongs to the approved assessment scope. A private address is not automatically an authorized target.

**Required verification before final submission:**

1. Compare each target/range with the signed authorization and the actual lab network configuration.
2. Record the exact Zenmap profile/command, scan date/time, and target for each screenshot.
3. Confirm that any service/version or aggressive scan was explicitly permitted.
4. Do not report ports, services, operating systems, or vulnerabilities unless the corresponding output is legible and captured.
5. If a scan was outside the approved scope, retain it as a separate lab exercise and do not present it as a NetworkWalks assessment result.

No port/service findings are asserted in this report because a complete, unambiguous result set was not available for verification here.

## 5. Findings and recommendations

The following are observations, not confirmed vulnerabilities.

| ID | Evidence-based observation | Relevance | Recommendation |
|---|---|---|---|
| OBS-01 | WHOIS output showed registrar and registration metadata, with registrant details privacy-protected. | Public registration metadata can help map an organization's domain footprint. | Review registration contacts, renewal settings, and registrar account security through the domain owner's normal administrative process. |
| OBS-02 | DNS output displayed A and MX information, with additional DNS record types reported by DNSRecon. | DNS records expose service-routing and infrastructure relationships. | Have the domain administrator review records for accuracy and remove obsolete entries through normal change control. |
| OBS-03 | cURL returned HTTP 200 and identified Apache in response headers. | Response headers disclose limited server information. | Review whether server-identifying headers are needed; do not treat their presence alone as a vulnerability. |
| OBS-04 | WhatWeb fingerprinted WordPress 7.1.4, Apache, and WP Download Manager. | Technology fingerprints can help defenders maintain an asset and patch inventory. | Confirm installed versions from the authoritative server inventory and apply vendor-supported updates where required. |
| OBS-05 | WAFW00F reported ModSecurity detection. | A WAF was identified by the tool's fingerprinting logic. | Confirm WAF deployment, ruleset maintenance, logging, and coverage with the system owner. |
| OBS-06 | theHarvester displayed 59 hosts/subdomains for `github.com`. | This demonstrates passive OSINT collection but is not a NetworkWalks finding. | Keep this result separate unless the domain is explicitly in scope; verify discovered assets with their owner before any further testing. |

No confirmed exploitable vulnerability is established by these observations.

## 6. Evidence register

The screenshots were supplied in conversation ZIP uploads and reviewed there. They have **not** been committed into this GitHub branch as image files. Add the original, redacted screenshots to the matching folders before treating this register as a complete submission evidence pack.

| Evidence ID | Module | Evidence described | Repository status |
|---|---|---|---|
| PM1-01 | PM1 | WHOIS output for `networkwalks.com` | Reviewed in conversation; image not committed |
| PM1-02 | PM1 | NSLOOKUP DNS query output | Reviewed in conversation; image not committed |
| PM1-03 | PM1 | cURL HTTP response headers | Reviewed in conversation; image not committed |
| PM1-04 | PM1 | WhatWeb fingerprint output | Reviewed in conversation; image not committed |
| PM1-05 | PM1 | WAFW00F detection output | Reviewed in conversation; image not committed |
| PM1-06 | PM1 | DNSRecon output | Reviewed in conversation; image not committed |
| PM4-01 | PM4 | theHarvester 4.21.2 output for `github.com` | Reviewed in conversation; image not committed; scope not established |
| PM5-01 | PM5 | Zenmap host/scan screenshots for private/local ranges | Reviewed in conversation; images not committed; scope/profile checks pending |

Before uploading screenshots, redact unrelated hostnames, personal data, credentials, tokens, public IPs or internal details that the authorization does not permit publishing. Keep original captures privately.

## 7. Limitations and outstanding checks

- PM2 and PM3 were not completed.
- The signed authorization and exact scope were not available for independent review while preparing this report.
- The theHarvester screenshot used `github.com`; it is not treated as a NetworkWalks target result.
- Zenmap screenshots include private/local ranges, and at least one shows `-T4 -A`; scope and method authorization must be verified.
- Screenshots have not yet been added to this GitHub branch.
- Some DNS and technology-fingerprint details are point-in-time observations and should not be treated as current without rechecking.
- No exploitation or vulnerability validation is claimed.

## 8. Conclusion

PM1 provides the completed elective footprinting work documented in this report. A theHarvester tool run and Zenmap scan screenshots are also recorded, with explicit scope and evidence limitations. PM2 and PM3 remain incomplete and are not claimed as completed.

This report should be treated as an evidence-review draft until the current authorization is checked privately, PM5 target/method scope is confirmed, and the redacted original screenshots are added to the repository or submitted through the approved private channel. The report deliberately avoids unsupported vulnerability claims and distinguishes tool output from verified security findings.

## 9. Pre-submission checklist

- [ ] Confirm the current signed authorization privately and check all PM5 targets/methods against it.
- [ ] Confirm whether `github.com` is explicitly within the permitted scope before counting PM4 as assessment evidence.
- [ ] Add redacted original screenshots to the repository's evidence folders or the approved submission channel.
- [ ] Verify every observation against the original screenshot/output.
- [ ] Do not publish the signed authorization or confidential scope without permission.
- [ ] Keep PM2 and PM3 marked incomplete unless actually performed and evidenced.
- [ ] Confirm the final report and evidence pack are submitted before the assignment deadline.
