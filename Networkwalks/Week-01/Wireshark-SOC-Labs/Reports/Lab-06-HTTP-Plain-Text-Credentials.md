# Lab 06 — HTTP Plain-Text Credentials

## Objective
Identify login requests and understand why credentials submitted over unencrypted HTTP can be exposed in packet captures.

## Reported result
- Result screenshot: 99%
- Capture size shown in the lab: 255 packets
- Protocol: HTTP
- Request: POST /login
- Source host: 192.168.10.45
- Number of login attempts shown: 2
- The lab exposed form data in the HTTP request body.

## Analysis workflow
1. Apply the HTTP display filter.
2. Use http.request.method == "POST" to locate form submissions.
3. Inspect the request URI and packet details.
4. Expand the HTML Form URL Encoded section when reviewing the training capture.
5. Compare the two attempts and identify the successful/failed outcome from the lab context.

## Security finding
HTTP does not encrypt request contents. Credentials submitted through an HTTP form may be readable by an observer who can capture the traffic.

## Defensive recommendation
Use HTTPS with valid TLS configuration, secure session cookies, and never send authentication secrets over plain HTTP.

## Evidence and limitation
The completed Lab 06 result card is published in the corresponding GitHub Evidence folder, with additional practical screenshots retained in the Week 01 source evidence archive. Credentials are intentionally omitted from this public report.
