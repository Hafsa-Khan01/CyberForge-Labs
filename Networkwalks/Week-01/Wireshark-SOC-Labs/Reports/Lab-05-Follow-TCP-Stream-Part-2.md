# Lab 05 — Follow TCP Stream, Part 2

## Objective
Inspect HTTP traffic and identify a hidden note embedded in a web page response.

## Reported result
- Result screenshot: 100%
- Capture size shown in the lab: 282 packets
- Relevant resource: /staff.html
- Hidden note location: HTML comment
- Relevant conversation: TCP stream 7
- HTTP response status: 200
- Additional exercise artefacts included a downloaded report file and server information.

## Analysis workflow
1. Apply the HTTP display filter.
2. Identify requests for the intranet pages.
3. Locate the request for /staff.html.
4. Follow the corresponding TCP stream.
5. Inspect the server response source, including HTML comments.
6. Confirm the response status and inspect the download request separately.

## Security finding
Sensitive notes placed in HTML comments are still delivered to the browser and can be read by anyone who can retrieve the page source. A hidden comment is not an access-control mechanism.

## Defensive recommendation
Do not place secrets or internal-only information in client-delivered HTML, comments, JavaScript, or other public response content. Enforce server-side authorisation.

## Evidence and limitation
The completed Lab 05 result card is published in the corresponding GitHub Evidence folder. Additional practical screenshots are retained in the Week 01 source evidence archive.
