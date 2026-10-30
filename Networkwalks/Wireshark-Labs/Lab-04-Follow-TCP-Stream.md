# Lab 04 — Follow TCP Stream

## Objective
Inspect a plain-text TCP chat conversation by identifying the client/server endpoints and following the TCP stream.

## Reported result
- Result screenshot: 90%
- Capture size shown in the lab: 246 packets
- Application conversation: TCP port 5000
- Client: 192.168.10.45
- Server: 192.168.10.20
- Followed stream: TCP stream 5
- Conversation size reported by the lab: 413 bytes
- Client messages appeared red; server messages appeared blue in Follow TCP Stream.

## Analysis workflow
1. Select the Wi-Fi capture interface as directed by the browser lab.
2. Apply the display filter tcp.port == 5000.
3. Inspect the initial TCP handshake and endpoint addresses.
4. Right-click a matching packet and select Follow → TCP Stream.
5. Review the direction and content of each side of the conversation.

## Security finding
The exercise demonstrates that application messages sent without transport encryption can expose internal conversation content and sensitive operational information to anyone able to capture the traffic.

## Defensive recommendation
Use an authenticated encrypted application protocol, protect credentials, and avoid sharing secrets in chat messages.

## Evidence
The learner supplied a Lab 4 result screenshot and additional Wireshark screenshots in the source evidence archive. Original screenshots should be placed in this lab's Evidence folder after privacy review.

## Limitations
This report records the supplied lab solution and result. The original PCAP was not independently re-analysed for this write-up.
