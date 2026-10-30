# Practical Investigation — Windows Security Event Analysis

## 1. Objective

Review selected Windows Security and System events in an authorized lab VM, understand what each record represents and correlate related activity before forming an investigative conclusion.

## 2. Scope and safety

Use only the assigned Windows VM and the time window specified by the exercise. Any action that intentionally changes audit settings, creates accounts, installs services or clears logs must be performed only when explicitly authorized in a disposable lab. Never clear logs or alter security controls on production or third-party systems.

## 3. Event reference

| Event ID | Log channel | Meaning |
|---:|---|---|
| 4624 | Security | Successful logon |
| 4625 | Security | Failed logon |
| 4634 | Security | Logoff |
| 4648 | Security | Logon attempt using explicit credentials |
| 4672 | Security | Special privileges assigned to a new logon |
| 4688 | Security | Process creation |
| 4697 | Security | Service installed |
| 4720 | Security | User account created |
| 4722 | Security | User account enabled |
| 4724 | Security | Attempt to reset an account password |
| 4732 | Security | Member added to a security-enabled local group |
| 4768 | Security | Kerberos TGT requested |
| 4769 | Security | Kerberos service ticket requested |
| 4776 | Security | NTLM credential validation |
| 1102 | Security | Security audit log cleared |
| 7045 | System | Service installed |

Security event 4697 and System event 7045 are separate records from different channels. Their presence, fields and availability depend on Windows version, audit policy and configuration.

## 4. Investigation procedure

1. Open Event Viewer on the assigned VM.
2. Review the Security channel and, for service-installation context, the System channel.
3. Filter by the assigned Event ID and a defined time window.
4. Open each relevant record and review both General and Details/XML views.
5. Record the provider, channel, Event ID, timestamp, computer, account and other fields that are present.
6. Identify related events around the same time and determine whether they correspond to expected lab activity.
7. Export or capture the evidence and redact sensitive information before publication.

## 5. Analytical approach

For a logon event, consider the account, logon type, source/workstation, authentication package and neighbouring events. For account or group changes, identify the actor and target, then verify whether the change was expected. For service installation, correlate the service name, image path, account and installation time with authorized administrative activity.

Event 1102 is an audit-integrity signal that warrants contextual review. It does not, by itself, identify who cleared the log or establish the reason. Examine surrounding records and other available telemetry.

## 6. Correlation worksheet

| Question | Evidence to review |
|---|---|
| What happened? | Event ID, provider and event description |
| When did it happen? | Timestamp and time zone |
| Which system recorded it? | Computer name and channel |
| Which identity was involved? | Subject and target account fields |
| Where did it originate? | Source/workstation fields, when present |
| Was it expected? | Lab actions, approved changes and baseline |
| What corroborates it? | Related events, endpoint or network records |
| What remains uncertain? | Missing fields, retention gaps and visibility limits |

## 7. Evidence handling

Preserve original event exports where generated. Capture the event's General and XML details when relevant. Keep the time window and filter criteria with the artifact. Do not publish credentials, tokens or unnecessary personal data.

## 8. Conclusion

State the event records actually observed, their context and any corroborating evidence. Separate direct observations from interpretation and identify what further evidence would be needed to support a stronger conclusion. Do not label an isolated Event ID as proof of compromise.
