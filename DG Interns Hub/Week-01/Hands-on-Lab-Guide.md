# Week 01 | Linux & Network Fundamentals — Practical Procedure

## 1. Exercise controls

**Purpose:** Prepare a controlled virtual lab and validate foundational Linux and network-administration tasks.

**Scope:** Only virtual machines and addresses assigned for this exercise.

**Preconditions**
- Virtualization software and guest operating systems are installed.
- Administrative access to the lab VMs is available.
- A dedicated NAT Network or Host-only network is configured where practical.
- A clean VM snapshot is available before configuration changes.

Do not connect intentionally vulnerable systems to a production or shared network.

## 2. Record the lab topology

Before testing, document:

| Field | Value to record |
|---|---|
| Hypervisor | Actual product and version |
| Guest systems | OS name and version for each VM |
| Network mode | NAT, NAT Network, Host-only or Bridged |
| Interface | Interface name inside each guest |
| Addressing | Actual IP address and prefix |
| Gateway / DNS | Actual configured values |
| Snapshot | Snapshot name or date |

Use the following commands to inspect configuration:

```bash
ip -br address
ip route
resolvectl status
```

If `resolvectl` is not installed, inspect the resolver configuration using the tools provided by the guest OS.

## 3. Validate connectivity

Run only against the assigned lab host:

```bash
ping -c 4 <lab-target>
traceroute <lab-target>
```

On systems without `traceroute`, use the equivalent approved diagnostic utility. Record packet loss, response times and any routing errors. A failed ping does not by itself prove that a host is offline; ICMP may be filtered.

For DNS validation:

```bash
nslookup <authorized-hostname>
dig <authorized-hostname>
```

Record the query, resolver and returned records. Do not substitute example addresses for observed values.

## 4. Linux account and permission exercise

Perform the following in a disposable Linux VM:

1. Create three dedicated test accounts and two test groups.
2. Assign the test accounts to the intended groups.
3. Create a shared working directory.
4. Set directory ownership and permissions so access is limited to the intended group.
5. Verify access using the relevant test accounts.
6. Record the commands and the resulting ownership/permission state.

Useful inspection commands:

```bash
id <test-user>
getent group <test-group>
ls -ld <shared-directory>
stat <shared-directory>
getfacl <shared-directory>
```

Use `getfacl` only if ACL utilities are installed. Explain the effective access rather than merely copying the permission string.

## 5. Process, socket and file-system inspection

Use the following commands to inspect the guest system:

| Command | Purpose |
|---|---|
| `ps aux` | Process inventory |
| `ss -tulpn` | Listening TCP/UDP sockets and associated process details where permitted |
| `find <path> -type f` | File discovery within a specified path |
| `grep -Rni <term> <path>` | Search text recursively |
| `df -h` | Filesystem capacity |
| `du -sh <path>` | Directory space usage |

Limit recursive searches to relevant lab paths to avoid unnecessary system load or disclosure.

## 6. Scheduled task validation

Create a harmless scheduled task in the test account's crontab. The task should write a timestamp to a file in the user's home directory. Verify the crontab entry and resulting file. Record the schedule, execution evidence and any environment-specific limitations.

## 7. Evidence package

Use descriptive filenames and retain original captures:

- VM configuration and topology.
- Interface and routing output.
- Connectivity and DNS test output.
- User/group and directory-permission verification.
- Process/socket inspection output.
- Cron configuration and execution result.

For each artifact, record its filename, capture date, associated exercise and a one-sentence description. Redact credentials, tokens and personal data before publication.

## 8. Result reporting

For each exercise, separate:
- **Procedure:** what was executed.
- **Observation:** what the system actually returned.
- **Interpretation:** what the result supports.
- **Limitation:** what was not tested or could not be confirmed.

Do not report a task as successful without corresponding verification evidence.
