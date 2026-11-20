# 02 — Phishing Types and Red Flags

| Type | Target | Characteristics | Example red flags |
|---|---|---|---|
| Phishing | Broad audience | Bulk impersonation through email or web pages | Generic greeting, unexpected login link, urgent account warning |
| Spear phishing | Named person/team | Personalised details and tailored pretext | References a real project but uses an unusual sender or request |
| Whaling | Senior executives / finance leaders | High-value executive impersonation | Urgent confidential payment or approval request |
| Smishing | Mobile users | SMS/text message with link or callback number | Parcel/tax/bank warning, shortened URL, request for OTP |
| Vishing | People reached by phone/voice | Caller impersonates support, bank or authority | Pressure, secrecy, remote-access request, OTP/password request |
| BEC | Finance, HR, executives, suppliers | Fraud using spoofed or compromised business email | Changed bank details, invoice diversion, unusual gift-card/payment request |

## Red-flag checklist
- [ ] Display name and actual sender address do not match.
- [ ] Reply-To differs unexpectedly from From.
- [ ] Domain is lookalike, misspelled, newly seen or unrelated to the claimed organisation.
- [ ] Message creates urgency, fear, secrecy or unusual authority.
- [ ] Unexpected request for credentials, MFA code, payment or sensitive data.
- [ ] Link text and actual destination differ; shortened or encoded URL.
- [ ] Unexpected attachment, macro-enabled document, archive or executable.
- [ ] SPF, DKIM or DMARC fails or is misaligned (a pass does not prove the message is safe).
- [ ] Message thread, invoice or supplier bank details changed unexpectedly.
- [ ] Sender asks to bypass normal approval or verification.

## Analyst response
Do not click, reply, open attachments or forward the message as a normal attachment. Preserve the original message (preferably .eml with full headers), report it through the approved channel, and verify unusual requests using a known trusted contact method.
