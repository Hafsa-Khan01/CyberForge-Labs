# PENETRATION TESTING REPORT
## FOOTPRINTING, RECONNAISSANCE & NETWORK SCANNING

**W2-PM-FINAL | WEEK 02 | NETWORKWALKS**

| Report detail | Information |
|---|---|
| Prepared by | Hafsa Khan |
| Programme | Cybersecurity & Ethical Hacking — NetworkWalks |
| Reporting period | Week 02 |
| Report date | 13 November 2026 |
| Selected modules | W2-PM1 — Footprinting with Multiple Kali Tools; W2-PM4 — theHarvester (execution attempted; output not validated); W2-PM5 — Zenmap Network Scanning |
| Assessment targets | `networkwalks.com` (public footprinting); own local Wi-Fi network (host discovery) |
| Authorization | NetworkWalks permission was stated by the tester; signed authorization is retained separately and is not published in this repository |
| Report version | 1.0 |

> **Document status:** Final report for the the selected practical modules, including a documented PM4 attempt. Findings are limited to the commands and scan output recorded below. Original screenshots and the topology PDF must accompany the report as evidence; they are not embedded in this Markdown file.

---

## 1. Executive Summary

This report documents the Week 02 practical work completed for the NetworkWalks Cybersecurity & Ethical Hacking programme. The assessment covered two required workstreams:

- **W2-PM1 — Footprinting and Reconnaissance:** Six Kali Linux tools were used to review publicly observable domain-registration, DNS, web-technology, HTTP-response, and WAF-identification information for `networkwalks.com`.
- **W2-PM4 — theHarvester:** The official assignment target was `microsoft.com`, with the prescribed Baidu and all-source tasks. The user also reported running the tool against `networkwalks.com` as an additional target. The available record includes a Baidu source disconnection and subsequent XML/proxy or YAML-related errors; successful result files and final output counts were not available for verification. No email, subdomain, or host count is therefore asserted for PM4.
- **W2-PM5 — Network Scanning:** Windows network configuration information was used to identify the local Wi-Fi subnet. Zenmap's Ping Scan profile was then used to discover live hosts on that local subnet and create a network topology PDF.

The PM1 activities returned domain and website information, including an A-record result of `192.232.216.135`, an HTTP `200 OK` response, WordPress/Apache technology fingerprints, a WAF identification result, and DNS record information.

For PM5, the active Wi-Fi adapter had IPv4 address `Windows host (local Wi-Fi)/24` and default gateway `local router`. A Ping Scan of `local Wi-Fi subnet (/24)` checked 256 addresses and identified two live hosts: the gateway and the Windows computer running the scan. The output displayed a MAC address for the gateway only.

The work was limited to information gathering and host discovery. No exploitation, credential attacks, denial-of-service testing, or vulnerability validation is claimed. Tool fingerprints and publicly visible information are observations, not confirmed vulnerabilities.

## 2. Objectives

The objectives of the selected modules were to:

1. Collect publicly accessible information about the assigned website using multiple reconnaissance tools.
2. Examine DNS responses and HTTP headers.
3. Identify visible website technologies and a possible WAF technology.
4. Identify the active Windows network adapter, IPv4 address, subnet mask, and default gateway.
5. Discover live hosts on the user's own local Wi-Fi subnet using a Ping Scan.
6. Record available IP and MAC address information.
7. Generate and save a network topology graphic in PDF format.

## 3. Scope, Authorization and Rules of Engagement

### 3.1 Assessment scope

| Target | Activity | Boundary |
|---|---|---|
| `networkwalks.com` | Public footprinting using PM1 tools; also reported as an additional PM4 theHarvester target | PM1 observations are documented; PM4 output is not validated |
| `microsoft.com` | Official PM4 theHarvester assignment target | Prescribed commands documented; execution output not validated |
| Own local Wi-Fi network | Host discovery and topology visualization | Local subnet `local Wi-Fi subnet (/24)` |

### 3.2 Authorization

The tester stated that permission for the NetworkWalks exercise was provided separately. The assignment PDF's sample Letter of Authorization is not treated as the tester's own authorization. The signed authorization is not included in this repository; it should be retained privately and produced to the programme supervisor if requested.

The local network scan was performed on the tester's own Wi-Fi network. No unrelated private or public target is included in the PM5 results in this report.

### 3.3 Testing constraints

- Only the targets and activities described in the report are represented.
- PM5 used a Ping Scan (`-sn`) for host discovery, not a port or service scan.
- No exploitation, password attacks, brute force, social engineering, denial-of-service, or intentional disruption was performed.
- The report does not claim that a tool-detected technology is vulnerable.
- The sample LOA and sample report supplied with the assignment were used as structural guidance only; sample names, dates, IPs, MACs, and findings were not copied as assessment results.

## 4. Environment and Tools

### 4.1 Operating environments

| Environment | Use |
|---|---|
| Kali Linux | PM1 footprinting and reconnaissance |
| Windows 10 | PM5 local network configuration and Zenmap |
| Active Windows adapter | Wi-Fi |
| Nmap/Zenmap | Host discovery and topology visualization |

### 4.2 Tools used

| Tool | Purpose |
|---|---|
| WHOIS | Retrieve publicly available domain registration information |
| WhatWeb | Fingerprint visible web technologies |
| Nslookup | Query DNS records and resolve domain information |
| cURL | Inspect HTTP response headers |
| Wafw00f | Identify a possible Web Application Firewall |
| DNSRecon | Enumerate DNS record information |
| Zenmap | Graphical interface for Nmap scanning and topology |
| Windows Command Prompt | Identify local IP configuration |
| Nmap | Perform host discovery on the local subnet |

## 5. W2-PM1 — Footprinting and Reconnaissance

### 5.1 Objective and target

The objective was to collect publicly accessible information about `networkwalks.com` using six Kali Linux tools. Each tool was selected to examine a different part of the public-facing footprint.

### 5.2 WHOIS — Domain registration information

**Command**

```bash
whois networkwalks.com
```

**Observation**

The reviewed WHOIS output identified GoDaddy as the registrar and displayed domain registration information, name-server information, and privacy-protected registrant details.

**Security relevance**

Registration metadata can help establish the administrative footprint of a domain. The presence of publicly available registration information is not, by itself, a vulnerability.

### 5.3 WhatWeb — Web technology fingerprinting

**Command**

```bash
whatweb --aggression=1 https://networkwalks.com
```

**Observation**

The reviewed output fingerprinted WordPress (reported version **7.1.4**), Apache-related server information, and WP Download Manager.

**Security relevance**

Technology fingerprints can help defenders maintain an accurate asset inventory and check whether installed components require updates. A fingerprint should be verified against the system owner's authoritative inventory before making version-specific security claims.

### 5.4 Nslookup — DNS queries

**Commands**

```bash
nslookup -type=A networkwalks.com
nslookup -type=AAAA networkwalks.com
nslookup -type=MX networkwalks.com
nslookup -type=NS networkwalks.com
nslookup -type=TXT networkwalks.com
```

**Observation**

The A-record lookup returned:

```text
192.232.216.135
```

The exercise also queried AAAA, MX, NS, and TXT record types.

**Security relevance**

DNS records help describe how a domain resolves and which supporting services are publicly referenced. DNS answers can change over time and should be treated as point-in-time observations.

### 5.5 cURL — HTTP response headers

**Commands**

```bash
curl -I https://networkwalks.com
curl -I http://networkwalks.com
```

**Observation**

The reviewed HTTPS response returned **HTTP 200 OK** and exposed Apache-related response-header information. WordPress REST API endpoint information was also visible in the response context.

**Security relevance**

HTTP headers can disclose implementation details. The system owner should decide which headers are operationally necessary and whether any unnecessary technical details can be reduced. A successful HTTP response is not a vulnerability.

### 5.6 Wafw00f — WAF identification

**Command**

```bash
wafw00f https://networkwalks.com
```

**Observation**

Wafw00f reported **ModSecurity (SpiderLabs)** as the detected WAF technology.

**Security relevance and limitation**

This is a tool-based identification result. It does not independently prove the WAF's complete deployment, ruleset, effectiveness, or coverage, and it does not establish that the application is protected against every attack class.

### 5.7 DNSRecon — DNS enumeration

**Command**

```bash
dnsrecon -d networkwalks.com -t std
```

**Observation**

The reviewed output reported approximately eight DNS records and displayed record categories including SOA, NS, MX, A, TXT, and SRV.

The DNSSEC query did not provide a confirming response in the reviewed output. That observation alone is insufficient to conclude that DNSSEC is disabled.

**Security relevance**

DNS enumeration provides a view of publicly visible domain infrastructure. DNS records should be reviewed by the domain administrator for accuracy and continued operational need.

### 5.8 PM1 results summary

| Tool | Main observed result |
|---|---|
| WHOIS | GoDaddy registrar and public registration metadata |
| WhatWeb | WordPress 7.1.4, Apache-related information, WP Download Manager fingerprint |
| Nslookup | A-record result: `192.232.216.135`; additional DNS record queries performed |
| cURL | HTTPS response: `200 OK`; Apache-related header information |
| Wafw00f | ModSecurity (SpiderLabs) reported as detected |
| DNSRecon | Approximately eight DNS records reported; SOA, NS, MX, A, TXT and SRV categories observed |

## 6. W2-PM4 — theHarvester Footprinting Attempt

### 6.1 Official assignment target and tasks

The official W2-PM4 practical specifies `microsoft.com` as the target domain and requires the following commands:

```bash
theHarvester -d microsoft.com -l 1000 -b baidu
theHarvester -d microsoft.com -l 50 -b all
```

The exercise is intended to collect publicly available domain-related information from the selected data sources. The user also reported running theHarvester against `networkwalks.com` as an additional target; this is recorded as an additional activity, not as a replacement for the official `microsoft.com` task.

### 6.2 Execution notes and evidence limitation

During the recorded attempt, the Baidu source returned a server-disconnection error. Subsequent troubleshooting involved XML/proxy and YAML-related errors. The successful final output files, screenshots, and source-by-source result counts were not available for independent review when this report was updated.

Accordingly:
- The official PM4 commands and target are documented.
- The additional `networkwalks.com` target is noted as user-reported activity.
- No discovered email addresses, subdomains, hosts, IP addresses, or numeric result counts are asserted.
- PM4 is classified as **attempted — results not validated**, not as a verified successful enumeration.
- The raw terminal output and saved text files should be attached if available so the results can be accurately transcribed.

### 6.3 PM4 security relevance

theHarvester is a passive reconnaissance tool that can aggregate publicly indexed information associated with a domain. Any returned records should be checked for relevance and accuracy; absence of results from a particular source does not establish that no related public information exists.

## 7. W2-PM5 — Zenmap Network Scanning

### 6.1 Objective

The objective was to identify the active Windows network configuration, discover live hosts on the local Wi-Fi subnet, record available IP and MAC addresses, and save a network topology PDF.

### 6.2 Local network configuration

The Windows Command Prompt commands used were:

```cmd
ipconfig
ipconfig /all
```

The active adapter was identified as Wi-Fi. Other listed adapters included disconnected Ethernet and virtual adapters used by VirtualBox and VMware. Those virtual adapters were not selected as the target network for this PM5 scan.

**Active Wi-Fi configuration**

| Detail | Observed value |
|---|---|
| Adapter | Wi-Fi |
| IPv4 address | `Windows host (local Wi-Fi)` |
| Subnet mask | `255.255.255.0` |
| Default gateway | `local router` |
| Calculated subnet | `local Wi-Fi subnet (/24)` |

### 6.3 Zenmap scan configuration

| Setting | Value |
|---|---|
| Target | `local Wi-Fi subnet (/24)` |
| Profile | Ping Scan |
| Equivalent Nmap command | `nmap -sn local Wi-Fi subnet (/24)` |
| Scan purpose | Host discovery |
| Port/service scan | Not performed in this PM5 scan |

The `-sn` option performs host discovery without a port scan.

### 6.4 Actual scan output

The recorded Zenmap/Nmap output was:

```text
Starting Nmap 7.991 ( https://nmap.org ) at 2026-11-13 09:58 +0500
Nmap scan report for local router
Host is up (0.0075s latency).
MAC Address: [redacted] (Huawei Technologies)
Nmap scan report for Windows host (local Wi-Fi)
Host is up.
Nmap done: 256 IP addresses (2 hosts up) scanned in 13.84 seconds.
```

### 6.5 Live hosts identified

| Host | IPv4 address | MAC address | Vendor / identification |
|---|---|---|---|
| Default gateway / router | `local router` | `[redacted]` | Huawei Technologies |
| Windows computer running the scan | `Windows host (local Wi-Fi)` | Not displayed in the recorded Nmap output | Local Windows Wi-Fi adapter |

The second host is identified as the Windows computer because its address matches the active Wi-Fi adapter's IPv4 address from `ipconfig`. Its MAC address is not claimed here because it was not displayed in the supplied scan output.

### 6.6 Scan summary

| Metric | Actual result |
|---|---|
| Subnet scanned | `local Wi-Fi subnet (/24)` |
| Total IP addresses scanned | 256 |
| Live hosts detected | **2** |
| Scan duration | 13.84 seconds |
| Scan type | Ping Scan |
| MAC addresses displayed by Nmap | 1 |

### 6.7 Network topology

After the Ping Scan, the Zenmap **Topology** tab was used to view the discovered hosts. The topology graphic was saved in PDF format as required by the practical task.

**Evidence file to attach:** `PM5-Network-Topology.pdf`

The topology represents the hosts discovered in this scan. It is not a complete inventory of all possible devices or network segments beyond the scanned subnet.

## 8. Security Observations and Risk Considerations

The following are preliminary observations from information gathering and host discovery. They are **not confirmed vulnerabilities**.

| ID | Observation | Potential relevance | Recommended action |
|---|---|---|---|
| OBS-01 | WHOIS returned registrar and domain-registration metadata. | Public metadata can contribute to external reconnaissance. | Review registrar account security, renewal controls, and registration contacts. |
| OBS-02 | DNS queries returned domain and service-related information. | DNS records can reveal service relationships and infrastructure details. | Review public DNS records periodically and remove obsolete entries through normal change control. |
| OBS-03 | cURL returned HTTP 200 OK and Apache-related header information. | Response headers can disclose implementation details. | Review headers and limit unnecessary technical disclosure without affecting application functionality. |
| OBS-04 | WhatWeb fingerprinted WordPress and WP Download Manager. | Component fingerprints can inform software inventory and patch review. | Confirm installed versions from the authoritative asset inventory and apply supported updates where required. |
| OBS-05 | Wafw00f reported ModSecurity detection. | The result reveals a possible defensive technology in use. | Confirm WAF coverage, ruleset maintenance, logging, and alert monitoring with the system owner. |
| OBS-06 | Two hosts responded on the local Wi-Fi subnet. | Host discovery supports local asset visibility. | Maintain a device inventory and verify unfamiliar devices with the network owner. |

### Risk interpretation

No Critical, High, Medium, or Low vulnerability rating is assigned because the exercises did not validate exploitable weaknesses. The observations above should be treated as informational review items. A formal risk rating would require confirmation of asset ownership, business context, exposure, exploitability, and compensating controls.

## 9. Recommendations

1. **Maintain an accurate technology inventory.** Verify CMS, plugin, and web server versions from authoritative administrative records.
2. **Apply supported security updates.** Review WordPress, plugins, and server components against vendor security advisories and update through the normal change process.
3. **Review HTTP headers.** Remove unnecessary implementation details where feasible while retaining headers required for secure operation.
4. **Maintain DNS hygiene.** Periodically verify A, AAAA, MX, NS, TXT, SRV, and other published records; remove stale entries only after owner approval.
5. **Validate WAF configuration.** Confirm ModSecurity deployment, ruleset updates, logging, alerting, and application coverage with the responsible administrator.
6. **Maintain local device inventory.** Record authorized devices and investigate unexpected devices through approved administrative procedures.
7. **Keep network topology documentation current.** Update diagrams when network devices or addressing change.
8. **Retest only within written scope.** Any additional scanning, service detection, or validation should be covered by current authorization and agreed testing constraints.

## 10. Limitations

- The findings reflect the output reviewed at the time of the exercises and may change as DNS records and website technologies are updated.
- WHOIS, WhatWeb, Wafw00f, and DNSRecon results are tool observations and were not independently validated against administrative systems.
- The absence of a DNSSEC confirmation in the observed query is not proof that DNSSEC is disabled.
- The PM5 scan covered only `local Wi-Fi subnet (/24)`.
- The recorded PM5 Nmap output displayed the router's MAC address but did not display the Windows host's MAC address.
- PM5 used Ping Scan host discovery; it did not enumerate ports or services.
- No exploitation, credential testing, vulnerability validation, or intrusive testing is claimed.
- Original screenshots and the topology PDF are separate evidence artifacts and must be attached to the submission. Their presence in the GitHub repository is not claimed unless the files are uploaded.

## 11. Conclusion

The Week 02 work documented in this report covered PM1 footprinting with six Kali Linux tools, a PM4 theHarvester attempt against the official Microsoft target (with NetworkWalks reported as an additional target), and local network discovery using Zenmap.

PM1 provided practical experience in reviewing domain-registration metadata, DNS information, HTTP response headers, website technology fingerprints, and WAF identification. PM4 documented the prescribed theHarvester tasks and troubleshooting, but its results remain unvalidated because the successful output files were not available for review. PM5 provided experience in identifying a Windows Wi-Fi network configuration, selecting the correct local subnet, running a Ping Scan, recording live hosts, and generating a network topology PDF.

The PM5 scan checked 256 addresses in `local Wi-Fi subnet (/24)` and identified two live hosts: `local router` and `Windows host (local Wi-Fi)`. The router's MAC address was displayed as `[redacted]`, with Huawei Technologies identified as the vendor.

The exercises reinforced the importance of using the correct scope, preserving actual tool output, separating observations from confirmed vulnerabilities, and documenting limitations clearly. All activities described here were limited to the stated educational and local-network scope.

## 12. Evidence Register

Attach the original screenshots and the saved topology PDF to the final submission. Suggested filenames are provided below; use the actual filenames if they differ.

| Evidence ID | Module | Evidence artifact | Status |
|---|---|---|---|
| PM1-E01 | PM1 | WHOIS command and output screenshot | Captured/reviewed; repository upload pending |
| PM1-E02 | PM1 | Nslookup DNS query screenshots | Captured/reviewed; repository upload pending |
| PM1-E03 | PM1 | cURL HTTP response header screenshots | Captured/reviewed; repository upload pending |
| PM1-E04 | PM1 | WhatWeb output screenshot | Captured/reviewed; repository upload pending |
| PM1-E05 | PM1 | Wafw00f output screenshot | Captured/reviewed; repository upload pending |
| PM1-E06 | PM1 | DNSRecon output screenshot | Captured/reviewed; repository upload pending |
| PM4-E01 | PM4 | Microsoft Baidu-source command and complete terminal output | Execution attempt noted; successful output/evidence not verified |
| PM4-E02 | PM4 | Microsoft all-sources command and complete terminal output | Execution attempt noted; successful output/evidence not verified |
| PM4-E03 | PM4 | Additional NetworkWalks-domain theHarvester output, if retained | User-reported additional run; output not verified |
| PM5-E01 | PM5 | Windows `ipconfig` / `ipconfig /all` output | Captured in terminal; screenshot upload pending |
| PM5-E02 | PM5 | Zenmap Ping Scan configuration and Nmap output | Scan output supplied; screenshot upload pending |
| PM5-E03 | PM5 | Zenmap Topology tab screenshot | Capture/upload pending |
| PM5-E04 | PM5 | `PM5-Network-Topology.pdf` | Saved locally; repository upload pending |

### Evidence handling

Before publishing evidence, review screenshots for credentials, tokens, personal information, unrelated devices, and any network details not approved for public disclosure. Keep the signed authorization private unless the issuing organization expressly permits publication.

---

**Prepared by:** Hafsa Khan  
**Programme:** NetworkWalks — Cybersecurity & Ethical Hacking  
**Module:** W2-PM-FINAL | Week 02  
**Report date:** 13 November 2026
