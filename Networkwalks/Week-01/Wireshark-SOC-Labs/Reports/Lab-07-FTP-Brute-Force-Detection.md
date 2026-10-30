# Lab 07 — FTP Brute-Force Detection

## Objective
Recognise repeated FTP authentication failures and identify the pattern that indicates a password-guessing attempt.

## Reported result
- Result screenshot: 100%
- Capture size shown in the lab: 369 packets
- Protocol: FTP
- FTP server: 192.168.10.20
- Suspected source: 192.168.10.66
- Target account: admin
- Failed authentication responses: 24
- The exercise then showed a successful FTP authentication response.

## Analysis workflow
1. Apply the ftp display filter.
2. Inspect USER and PASS commands to identify the attempted account and source.
3. Filter server replies with ftp.response.code == 530 to count failed logins.
4. Identify the success response code 230.
5. Correlate repeated failures followed by success.

## Security finding
A high volume of failed logins against one account, followed by a successful authentication, is consistent with a brute-force or password-guessing pattern.

## Defensive recommendation
Disable clear-text FTP in production. Prefer SFTP or FTPS, enforce strong unique passwords and MFA where supported, rate-limit authentication attempts, and alert on repeated failures.

## Evidence and limitation
The learner supplied the result screenshot and Wireshark screenshots in the source archive. Password values are intentionally omitted. The original PCAP was not independently re-analysed.
