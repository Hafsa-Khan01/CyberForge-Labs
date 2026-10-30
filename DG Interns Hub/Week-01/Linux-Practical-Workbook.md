# Week 1 — Linux Practical Workbook

## User and Group Administration
In a disposable Linux VM, create test users and groups using the distribution's supported account-management commands. Verify membership with `id <user>` and inspect group definitions with `getent group`. Do not use real personal accounts for exercises.

## Shared Directory Permissions
Create a lab directory, assign a dedicated group, enable group collaboration with the setgid directory bit where appropriate, and apply least-privilege permissions. Verify with `ls -ld <directory>` and test access as a permitted test user.

## Process and Socket Inspection
- `ps aux`: list processes.
- `top`: observe live process activity.
- `ss -tulpn`: inspect listening TCP/UDP sockets (process details may require elevated privileges).

## File Search
- `find /home -type f -name '*.txt'`: locate text files.
- `grep -Rni 'keyword' <lab-directory>`: search text recursively.
Use a bounded lab directory rather than searching the entire host without need.

## Cron
Create a harmless scheduled task that writes a timestamp to a lab log. Verify the crontab entry and resulting log. Remove the test entry after the exercise.

## Network Mapping
Record interface addresses with `ip a`, routes with `ip route`, reachability with `ping`, path with `traceroute`, and DNS with `nslookup` or `dig`. Use actual observed values in the lab report.

## Evidence
Capture terminal output, explain the purpose of each command and redact usernames or data that should not be public.
