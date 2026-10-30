# Lab 08 — VoIP Call Analysis

## Objective
Follow VoIP signalling and media traffic to understand how call metadata and unencrypted voice content may be exposed.

## Reported result
- Result screenshot: 98%
- Capture size shown in the lab: 1,051 packets
- Call signalling: SIP
- Voice media: RTP
- Codec: PCMU (G.711)
- The exercise included SIP call setup/teardown and an RTP conversation.

## Analysis workflow
1. Apply the sip display filter to inspect call signalling.
2. Identify the INVITE, provisional/final responses, ACK, and BYE messages.
3. Apply the rtp filter to inspect media packets.
4. Review codec/payload information and use RTP stream analysis where available.
5. Avoid copying personal or payment data from the training conversation into reports.

## Security finding
Signalling and media protection are separate concerns. Without suitable encryption, call metadata and voice content may be exposed to someone able to capture the traffic.

## Defensive recommendation
Protect SIP signalling with TLS and voice media with SRTP. Apply network segmentation, access controls, and secure handling of sensitive information spoken during calls.

## Evidence and limitation
The learner supplied the result screenshot and Wireshark screenshots in the source archive. Personal/payment details from the training conversation are intentionally omitted. The original PCAP was not independently re-analysed.
