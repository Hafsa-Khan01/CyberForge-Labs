# 03 — SPF, DKIM and DMARC

| Control | What it checks | What it does not prove |
|---|---|---|
| SPF | Whether the sending IP is authorised by the envelope-sender domain's SPF policy | It does not authenticate the visible From address by itself; forwarding can affect results |
| DKIM | Whether a cryptographic signature validates and signed message parts have not changed | A valid signature does not automatically mean the sender is trustworthy |
| DMARC | Whether SPF or DKIM passes with alignment to the visible From domain, and applies the domain's policy | A DMARC pass is not a malware or content verdict |

## Example Authentication-Results snippets

**Illustrative pass:**
```
Authentication-Results: mx.example.net;
 spf=pass smtp.mailfrom=mailer.example.org;
 dkim=pass header.d=example.org header.s=s1;
 dmarc=pass header.from=example.org
```

**Illustrative fail:**
```
Authentication-Results: mx.example.net;
 spf=fail smtp.mailfrom=untrusted.invalid;
 dkim=fail header.d=untrusted.invalid;
 dmarc=fail header.from=example.org
```

These are synthetic teaching examples, not captured headers. In a real message, identify which receiving server added the Authentication-Results field and assess alignment, not just the words pass/fail. A malicious message can pass authentication if it comes from a compromised or attacker-controlled but properly configured domain.
