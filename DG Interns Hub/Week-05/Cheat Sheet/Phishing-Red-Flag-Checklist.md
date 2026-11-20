# Phishing Red-Flag Checklist

## Sender and routing
- [ ] Display name matches actual sender.
- [ ] Sender domain is correctly spelled and expected.
- [ ] Reply-To and Return-Path are consistent with the claimed organisation.
- [ ] Received chain and timestamps are plausible.
- [ ] SPF, DKIM and DMARC results and alignment reviewed.

## Message content
- [ ] Unexpected urgency, fear, secrecy or authority.
- [ ] Request for password, MFA code, payment or sensitive data.
- [ ] Unusual invoice or supplier bank-detail change.
- [ ] Context does not match normal business process.
- [ ] Unexpected attachment or request to enable macros/run content.

## Links and files
- [ ] Actual URL destination inspected without clicking.
- [ ] Shortened links, lookalike domains and punycode reviewed.
- [ ] URLs/domains defanged in notes.
- [ ] Attachment filename, type and SHA-256 recorded without opening.
- [ ] Reputation results timestamped.

## Response
- [ ] Original .eml preserved and hashed.
- [ ] Reported through approved channel.
- [ ] Similar messages/recipients searched.
- [ ] No reply, click, execution or public upload of confidential data.
- [ ] Verdict explains evidence and uncertainty.

One failed authentication check is a warning, not a final verdict. One pass does not guarantee safety.
