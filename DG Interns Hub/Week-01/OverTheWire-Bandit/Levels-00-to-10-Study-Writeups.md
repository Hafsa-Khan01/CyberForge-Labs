# OverTheWire Bandit — Levels 0–10 Study Write-ups

These notes describe the Linux concepts used across the early Bandit levels. Follow the level instructions on the official platform and record the exact command sequence you personally used. **Never publish level passwords, tokens or credentials.**

| Level | Core concept / technique to practise |
|---|---|
| 0 | Connect to the Bandit host using SSH with the supplied initial account details. |
| 1 | Read a file whose name begins with a special character; use a safe path such as `./-`. |
| 2 | Handle filenames containing spaces by quoting or escaping the path. |
| 3 | Show hidden directory entries with `ls -la`. |
| 4 | Identify the human-readable file among files with different types; `file` can help. |
| 5 | Search files by required attributes such as size, permissions or ownership using `find`. |
| 6 | Search a wider filesystem while handling permission errors; use appropriate `find` predicates. |
| 7 | Search file content for a known keyword with `grep`. |
| 8 | Identify a unique line in a file using sorting and duplicate counting, e.g. `sort` and `uniq -u`. |
| 9 | Extract readable strings from binary-like data with `strings` and inspect the surrounding output. |
| 10 | Decode Base64 content with `base64 -d` after confirming the input format. |

## Write-up Format for Each Level
1. **Objective:** paraphrase the level goal without revealing the password.
2. **Observation:** describe the file, directory or data property given by the task.
3. **Method:** list the commands you ran and explain each option.
4. **Verification:** describe how you confirmed the intended result without reproducing credentials.
5. **Lesson learned:** note the Linux skill practised.

## Safety and Sharing
Do not commit passwords, private keys, session tokens or screenshots that expose credentials. Keep platform-specific answers within the platform's rules.
