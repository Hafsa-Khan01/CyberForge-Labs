# Practical Write-up — Wireshark Capture Exercise

## Objective
Capture and identify DNS, ICMP, TCP handshake and HTTP traffic between authorized lab virtual machines.

## Procedure
1. Confirm the Kali and Ubuntu VMs are on the intended isolated lab network.
2. Identify the active capture interface and begin a Wireshark capture.
3. Generate permitted DNS lookup, ping and HTTP client traffic from the test VM to the lab host.
4. Stop and save the capture as PCAPNG.
5. Apply filters such as `dns`, `icmp`, `tcp`, `http` and `tcp.flags.syn == 1 && tcp.flags.ack == 0`.

## Analysis
For TCP, identify SYN, SYN/ACK and ACK packets. For DNS, inspect query and response fields. For ICMP, identify echo request/reply. For HTTP, inspect request method and response status where plaintext HTTP is used.

## Evidence and Limitations
Attach the actual capture file and screenshots. Record the interface, timestamp, lab endpoints and exact filters. Do not claim a packet was captured unless it exists in the saved file.
