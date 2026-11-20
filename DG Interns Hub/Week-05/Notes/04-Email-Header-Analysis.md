# 04 — Reading an Email Header

Read raw headers from the original .eml file. The Received chain is normally read from the bottom (earlier hop) towards the top (later hop), while remembering that individual header lines can be forged before trusted infrastructure receives the message.

| Header field | Purpose | Red-flag indicator |
|---|---|---|
| Received | Records mail-server hops and timestamps | Unexpected relay, suspicious originating host, impossible chronology or timezone inconsistency |
| Return-Path | Envelope return address used for bounces | Unrelated domain or mismatch requiring explanation |
| Reply-To | Address replies are directed to | Different or lookalike domain, especially for payment or credential requests |
| Message-ID | Message identifier, often containing a generating host/domain | Odd domain, malformed value or mismatch with claimed sender (context matters) |
| Authentication-Results | Receiving system's SPF/DKIM/DMARC results | Failures, alignment failures or result added by an untrusted intermediary |

## Workflow
1. Preserve the original message and calculate a SHA-256 hash of the .eml file.
2. Record From, To, Subject and Date; note timezone.
3. Inspect Received lines from oldest to newest and identify trusted receiving infrastructure.
4. Compare From, Return-Path and Reply-To domains.
5. Read Authentication-Results and check SPF/DKIM/DMARC alignment.
6. Inspect URLs and attachments without opening them; defang indicators in notes.
7. Correlate reputation results with context and record source/time. Reputation is one input, not a verdict by itself.
