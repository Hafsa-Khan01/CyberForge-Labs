# 6. Turning a TTP into Detection Logic: SSH and Windows Brute Force

## Objective
Convert attacker behavior into a testable detection. This example focuses on repeated authentication failures from one source within a short time window.

## MITRE ATT&CK mapping
- **Tactic:** Credential Access
- **Technique:** **T1110 – Brute Force**
- Relevant sub-techniques depend on observed behavior:
  - **T1110.001 – Password Guessing:** repeated attempts to guess a password.
  - **T1110.003 – Password Spraying:** trying a small number of passwords against many accounts.

Do not assign a sub-technique based only on a generic failed-login event. Use the observed pattern and investigation context.

## Detection hypothesis
Alert when one source address produces at least five failed authentication attempts against a monitored system within a five-minute window. This is a starter lab threshold, not a universal production setting.

## Windows Security log approach
Windows Security Event ID **4625** records a failed logon. Depending on the event and logon type, useful fields may include:
- TargetUserName: account involved in the failed logon.
- IpAddress: remote source address, when populated.
- LogonType: type of logon attempt.
- Status and SubStatus: failure status information.
- Computer: system that recorded the event.

Example SPL for five or more failures from one source in a five-minute bucket:

    index=lab EventCode=4625
    | eval src_ip=IpAddress
    | where isnotnull(src_ip) AND src_ip!="-"
    | bin _time span=5m
    | stats count as failures dc(TargetUserName) as accounts values(TargetUserName) as users by _time src_ip
    | where failures >= 5
    | table _time src_ip failures accounts users

Field extraction varies by Windows input and add-on. Inspect sample events and confirm actual field names before using this as an alert. Fixed five-minute buckets can miss attempts crossing a bucket boundary; production logic may use a rolling window or overlapping scheduled searches.

## SSH log approach
On Ubuntu, failed SSH authentication messages are commonly written to /var/log/auth.log. Exact text and fields vary by OpenSSH version and configuration.

Illustrative SPL after confirming that the source IP is extracted as src_ip:

    index=lab sourcetype=linux_secure ("Failed password" OR "authentication failure")
    | where isnotnull(src_ip)
    | bin _time span=5m
    | stats count as failures values(user) as users by _time src_ip
    | where failures >= 5
    | table _time src_ip failures users

The sourcetype and field extraction are examples. If events use another sourcetype or have no extracted src_ip, inspect raw events and configure parsing first.

## Detection logic in plain language
1. Select failed authentication events from the relevant source.
2. Extract source IP and target account where available.
3. Group events by source IP and five-minute interval.
4. Count failures and optionally distinct target accounts.
5. Alert when the count reaches or exceeds five.
6. Include source, target accounts, time window and event count.
7. Investigate whether the activity is malicious, expected automation or a misconfigured service.

## L1 analyst checks
- Is the source internal, external, VPN or a known service?
- Is one account targeted repeatedly, or are many accounts being tested?
- Are there successful logons from the same source after failures?
- What is the target asset and account privilege level?
- Do firewall, VPN, endpoint or identity logs corroborate the activity?
- Is this an approved test or monitoring process?

## Limitations
- NAT, proxies and VPN gateways can make many users appear under one address.
- Missing source IP fields reduce detection usefulness.
- Distributed or slow attacks may stay below the threshold.
- Fixed buckets can split a burst across adjacent windows.
- High failure counts can result from forgotten passwords or misconfigured applications.

## Safe validation
Only simulate password guessing against systems you own or are explicitly authorized to test, preferably in an isolated lab. Use a disposable test account and a short test wordlist; never use real user passwords or production accounts.
