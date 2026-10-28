# Security and Responsible Use

This repository documents learning and authorized defensive/security testing.

- Use scanning and assessment tools only on systems for which you have explicit authorization and within the approved scope.
- Never commit passwords, API keys, access tokens, private keys, session cookies, or personal records.
- Do not commit VM images, large generated artifacts, or packet captures that may contain private traffic.
- Review screenshots and logs before committing; redact sensitive values without altering the technical conclusion.
- If a secret is accidentally committed, removing it from the latest file is not enough. Revoke/rotate the exposed credential and follow GitHub's guidance for removing sensitive data from history.
- Report vulnerabilities through the program's approved channel and follow its disclosure policy.
