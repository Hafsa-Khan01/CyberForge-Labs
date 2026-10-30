# NetworkWalks Cybersecurity Internship — Week 01
## Practical Lab Report: VirtualBox, Kali Linux & Wireshark Traffic Analysis

**Prepared by:** Hafsa Khan  
**Programme:** NetworkWalks Cybersecurity Internship  
**Reporting period:** Week 01  
**Practical scope:** Virtual lab setup and Wireshark SOC exercises (Labs 03–08)  
**Evidence source:** Week 01 practical screenshots and completed lab result cards

---

## 1. Executive Summary

This report documents the Week 01 practical work completed for the NetworkWalks cybersecurity internship. The work covered two connected areas: preparing a Kali Linux virtual lab in Oracle VirtualBox and analysing network traffic through six guided Wireshark exercises.

The Wireshark exercises focused on identifying suspicious TCP connection patterns, reconstructing TCP conversations, inspecting HTTP requests, recognising FTP authentication failures, and understanding SIP/RTP traffic used in VoIP communications. The supplied result cards record scores of **89%, 90%, 100%, 99%, 100%, and 98%**, respectively, producing an arithmetic mean of **96%** across the six exercises.

The practical exercises were completed using the assigned lab environment and guided Wireshark captures. Screenshots and result cards were captured as supporting evidence. The technical observations below summarise the work performed and the learning outcomes from each exercise.

## 2. Objectives

The Week 01 practical objectives were to:

1. Prepare a controlled Kali Linux environment using VirtualBox.
2. Understand virtual network adapter and shared-folder configuration.
3. Become familiar with Wireshark's packet-list, packet-detail and stream-analysis views.
4. Identify indicators of network scanning and suspicious authentication activity.
5. Inspect application-layer traffic and understand the exposure risks of unencrypted protocols.
6. Interpret basic SIP signalling and RTP media traffic.
7. Record results and technical observations in a traceable evidence-based format.

## 3. Virtual Lab Environment: Oracle VirtualBox & Kali Linux

The first part of the Week 01 work was preparing a Kali Linux virtual machine in Oracle VirtualBox for cybersecurity and network-analysis practice. The setup evidence records the VM running, its general configuration, network-adapter settings, shared-folder configuration, NAT Network manager, Kali network-interface details and connectivity-check activity.

| Component | Setup / role |
|---|---|
| Host platform | Windows |
| Virtualisation platform | Oracle VirtualBox |
| Guest operating system | Kali Linux |
| Virtual network | NAT Network, configured against the internship brief |
| Shared-folder location | `/downloads` (assignment reference path) |
| Network inspection | Kali terminal network-interface and connectivity checks |
| Subsequent analysis tool | Wireshark |

### 3.1 Setup and configuration workflow

1. **Virtual machine preparation:** Opened the Kali Linux virtual machine in Oracle VirtualBox and reviewed its general VM settings.
2. **Network configuration:** Reviewed the VM network adapter and the VirtualBox NAT Network configuration for the assigned lab environment.
3. **Shared-folder configuration:** Reviewed the shared-folder settings intended to make the host/guest working files accessible inside the Kali environment.
4. **Guest startup:** Started the Kali Linux VM and confirmed the guest desktop was available for practical work.
5. **Network inspection:** Used Kali network-interface and connectivity checks to inspect the guest's network configuration.
6. **Evidence capture:** Captured screenshots of the running VM, VirtualBox settings, adapter and NAT Network configuration, shared-folder settings, and Kali network checks.

### 3.2 Assignment network reference

The internship brief specifies a NAT Network of `10.0.0.0/24`, an expected Kali address of `10.0.0.2/24`, gateway `10.0.0.1`, and guest shared-folder path `/downloads`. These are the assignment's reference settings; the exact active IP address and successful shared-folder permissions should be read from the relevant configuration screenshots or terminal output rather than assumed from the brief alone.

### 3.3 Network and shared-folder checks

The following Kali commands are suitable for inspecting the configured environment:

```bash
ip -br address
ip route
ip neigh
ping -c 4 10.0.0.1
getent hosts example.com
findmnt
ls -la /downloads
```

Together, these checks help inspect interface addressing, routing, gateway reachability, DNS resolution, mounted filesystems and shared-folder visibility. A successful ping alone does not establish that every service or shared-folder permission is working.

**Setup evidence:** The VirtualBox/Kali evidence folder contains eight setup screenshots covering the running Kali VM, VM settings, network adapter, shared-folder configuration, network connectivity/interface checks, Snapshot Manager and NAT Network Manager.

## 4. Methodology

The practical workflow followed a repeatable analysis sequence:

1. **Prepare:** Open the assigned lab capture or the configured Kali virtual machine.
2. **Scope:** Identify the protocol, endpoints and question being investigated.
3. **Filter:** Apply a relevant Wireshark display filter to reduce unrelated traffic.
4. **Inspect:** Review packet-list entries and expand protocol fields in the packet-details pane.
5. **Correlate:** Compare source/destination addresses, ports, flags, response codes, timestamps and stream direction.
6. **Interpret:** Relate observed traffic to a network or application-security behaviour.
7. **Document:** Record the result, the security significance and the supporting evidence reference.

Useful Wireshark filters for revisiting these exercises include:

| Investigation | Example display filter |
|---|---|
| TCP SYN packets | `tcp.flags.syn == 1 && tcp.flags.ack == 0` |
| One endpoint | `ip.addr == 192.168.10.66` |
| HTTP requests | `http.request` |
| FTP control traffic | `ftp || ftp-response` |
| SIP signalling | `sip` |
| RTP media | `rtp` |

Filters are starting points; the correct filter depends on the capture and Wireshark's protocol dissection.

## 5. Practical Exercises & Technical Analysis

### 5.1 Lab 03 — Identify the Attacker's IP

**Recorded result:** 89%

**Investigation focus:** Recognising TCP SYN scanning and identifying the system initiating the connection attempts.

The supplied lab notes describe a 309-packet capture, with 73 packets matching the SYN-focused filter. The notes identify `192.168.10.66` as the suspected source and `192.168.10.20` as the target, with 40 ports probed. They report open ports 22, 80 and 443 and closed-port responses using TCP RST/ACK.

**Analysis:** A sequence of initial SYN packets directed at multiple destination ports can indicate port scanning. The analyst should correlate the source, target, destination-port spread, timing and response flags before classifying the behaviour. A single SYN packet is not sufficient evidence of malicious activity.

**Defensive relevance:** Monitor unusual connection rates and broad port coverage, baseline legitimate scanners, and correlate network detections with firewall and endpoint telemetry.

**Learning outcome:** Use TCP flags and endpoint/port patterns to recognise reconnaissance behaviour.

*Evidence reference: Lab 03 result card and corresponding packet-analysis screenshots.*

### 5.2 Lab 04 — Follow TCP Stream

**Recorded result:** 90%

**Investigation focus:** Reconstructing an application conversation carried over TCP.

The supplied notes describe a 246-packet capture involving TCP port 5000, with stream 5 containing a 413-byte conversation between the exercise endpoints.

**Analysis:** Wireshark's Follow TCP Stream feature reassembles application data in both directions, making it easier to understand a conversation than examining isolated packets. If an application sends sensitive information without encryption, a person with access to the traffic may be able to read it.

**Defensive relevance:** Use TLS for application protocols that carry sensitive data, avoid transmitting credentials or confidential content in clear text, and validate certificate and transport-security configuration.

**Learning outcome:** Reconstruct TCP conversations and explain the confidentiality risk of plaintext application protocols.

*Evidence reference: Lab 04 result card and TCP stream-analysis screenshots.*

### 5.3 Lab 05 — Follow TCP Stream, Part 2

**Recorded result:** 100%

**Investigation focus:** Inspecting HTTP content and understanding information exposed in client-delivered web pages.

The supplied notes refer to a request for `/staff.html`, stream 7 and an HTTP 200 response. The exercise highlighted information present in an HTML comment.

**Analysis:** HTML comments and other client-side content are delivered to the browser and can be inspected. Hiding a value in a comment, JavaScript file or page source does not make it secret. Access restrictions must be enforced by the server, not by obscuring client-side content.

**Defensive relevance:** Never place passwords, API keys, internal notes or sensitive business information in client-delivered source. Apply server-side authorization and keep secrets in protected server-side configuration.

**Learning outcome:** Inspect HTTP responses and distinguish visible client-side content from properly protected server-side resources.

*Evidence reference: Lab 05 result card and HTTP stream/page-source screenshots.*

### 5.4 Lab 06 — HTTP Plain-Text Credentials

**Recorded result:** 99%

**Investigation focus:** Identifying login submissions and understanding why HTTP is unsuitable for transmitting credentials.

The supplied notes describe a 255-packet capture containing an HTTP POST request to `/login` and two login attempts. Credential values are intentionally excluded from this report.

**Analysis:** Standard HTTP does not encrypt request contents. Form submissions can therefore be exposed to an observer who can capture traffic along the communication path. The presence of a POST request does not itself make data secure; transport encryption and secure application handling are required.

**Defensive relevance:** Enforce HTTPS across the application, redirect HTTP to HTTPS, configure modern TLS, set secure session-cookie attributes, and avoid logging passwords or authentication tokens.

**Learning outcome:** Recognise HTTP form submissions in packet captures and explain the risk of transmitting authentication data without TLS.

*Evidence reference: Lab 06 result card and HTTP request-analysis screenshots. Sensitive form values are not reproduced.*

### 5.5 Lab 07 — FTP Brute-Force Detection

**Recorded result:** 100%

**Investigation focus:** Recognising repeated FTP authentication failures and a subsequent successful response.

The supplied notes describe a 369-packet capture, 24 FTP failure responses (code 530) and a later success response (code 230). Account and password details are not reproduced.

**Analysis:** Repeated authentication failures followed by a successful login may indicate password guessing or credential abuse. The analyst should correlate the attempts by source, account, timing and destination, then check whether the successful session performed unusual actions.

**Defensive relevance:** Replace legacy FTP with SFTP or appropriately configured FTPS, enforce strong unique credentials and multi-factor authentication where available, apply rate limiting or lockout controls carefully, and alert on repeated failures followed by success.

**Learning outcome:** Interpret FTP response codes and identify an authentication pattern that merits investigation.

*Evidence reference: Lab 07 result card and FTP control-channel screenshots.*

### 5.6 Lab 08 — VoIP Call Analysis

**Recorded result:** 98%

**Investigation focus:** Separating call signalling from media traffic in a VoIP capture.

The supplied notes describe a 1,051-packet capture containing SIP signalling and RTP media, with PCMU identified as the codec. Personal conversation and payment-related details from the training material are intentionally excluded.

**Analysis:** SIP is commonly used to establish, manage and terminate sessions, while RTP carries real-time audio/video media. Analysing both protocol layers helps an analyst understand call setup and media flow. Exposed signalling or media can create privacy and confidentiality risks.

**Defensive relevance:** Use SIP over TLS where supported and SRTP for media protection, restrict access to voice infrastructure, segment voice networks appropriately, and monitor unusual call patterns.

**Learning outcome:** Identify the roles of SIP and RTP and explain why signalling and media require appropriate protection.

*Evidence reference: Lab 08 result card and SIP/RTP analysis screenshots.*

## 6. Results Summary

| Lab | Exercise | Score | Main skill demonstrated |
|---|---|---:|---|
| 03 | Identify the Attacker's IP | 89% | TCP scan pattern recognition |
| 04 | Follow TCP Stream | 90% | TCP conversation reconstruction |
| 05 | Follow TCP Stream, Part 2 | 100% | HTTP response and source inspection |
| 06 | HTTP Plain-Text Credentials | 99% | HTTP authentication exposure analysis |
| 07 | FTP Brute-Force Detection | 100% | Authentication-failure pattern analysis |
| 08 | VoIP Call Analysis | 98% | SIP signalling and RTP media inspection |
| **Overall mean** | **6 exercises** | **96%** | |

The mean is calculated from the six recorded exercise scores.

## 7. Evidence Register

The Week 01 submission uses a curated set of **41 screenshots**: eight VirtualBox/Kali setup screenshots, 27 Windows-host Wireshark practical screenshots and six learner result cards. The [Week 01 Evidence Register](../EVIDENCE-INDEX.md) provides the complete evidence count and navigation links.

| Evidence group | Quantity | Recommended use |
|---|---:|---|
| Wireshark result cards | 6 | One compact results panel/table; retain originals in each lab folder |
| Kali desktop / VM view and VirtualBox setup | 8 | Select representative environment, network-adapter and shared-folder views |
| Windows-host Wireshark practical screenshots | 27 | Use the clearest packet-analysis views that directly support the lab findings |

**Recommended report visuals:** one Kali/VirtualBox environment image, one VirtualBox network configuration image, and a small selection of Wireshark analysis images that directly support the most important findings. Avoid repeating near-identical screenshots.

**Repository evidence paths:**
- `VirtualBox-Kali-Lab/Evidence/` — VM and network configuration images.
- `Wireshark-SOC-Labs/Evidence/Lab-03/` through `Lab-08/` — learner result-card screenshots.
- `Windows-Wireshark/Evidence/` — Windows-host practical screenshots.
- `Wireshark-SOC-Labs/Reports/` — individual exercise reports.

The evidence set is organised by practical area and lab number. The six result cards and eight setup screenshots are in their dedicated folders; the Windows-host practical screenshots are maintained in a separate supporting-evidence folder.

## 8. Security Recommendations Derived from the Exercises

1. Prefer encrypted protocols and enforce TLS for web and application traffic.
2. Avoid exposing secrets in HTML, JavaScript, comments, URLs or client-side configuration.
3. Monitor SYN patterns and unusual port coverage to detect reconnaissance.
4. Correlate repeated authentication failures with subsequent successful logins.
5. Protect voice signalling and media with supported encryption mechanisms.
6. Retain relevant network telemetry and investigate suspicious events with endpoint and firewall context.
7. Keep lab environments isolated and perform testing only on systems for which explicit authorization exists.

## 9. Evidence Integrity

- The Week 01 VirtualBox/Kali setup and six guided Wireshark exercises are documented in this report.
- Published screenshots are organised in the corresponding setup, Windows-host and lab result-card evidence folders.
- The six result percentages are transcribed from the completed learner result cards; they are not independent packet-capture validation.
- The evidence register lists the complete curated screenshot set used for this submission.
- Training credentials, passwords, personal conversation content and payment information are deliberately omitted from this report to protect sensitive information.
- Evidence is grouped by lab so that the setup process, packet-analysis work and final results can be reviewed in context.

## 10. Conclusion

Week 01 provided practical exposure to virtual lab preparation and network traffic analysis. The work progressed from understanding the Kali/VirtualBox environment to examining TCP behaviour, application streams, web authentication exposure, FTP login patterns and VoIP traffic.

The six supplied Wireshark result cards show an average score of **96%**. More importantly, the exercises demonstrate how packet-level observations can be translated into defensive security insights: recognising reconnaissance, identifying plaintext exposure, detecting suspicious authentication patterns and understanding the need to protect real-time communications.

The supporting screenshots and result cards are maintained in the structured Week 01 evidence folders for review.

---

**Report prepared for:** NetworkWalks Cybersecurity Internship — Week 01  
**Author:** Hafsa Khan  
**Use:** Educational and authorized cybersecurity training
