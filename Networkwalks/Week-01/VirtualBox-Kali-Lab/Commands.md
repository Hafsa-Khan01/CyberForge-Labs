# Kali Linux — Week 01 Command Reference

Run commands inside the assigned Kali VM. These commands are inspection aids; record the actual output, date and environment when reporting a result.

## 1. System and interface inventory

```bash
whoami
hostname
cat /etc/os-release
ip -br address
ip link show
```

Avoid publishing usernames, hostnames or other identifiers if they reveal personal information.

## 2. Routing and connectivity

```bash
ip route
ip neigh
ping -c 4 10.0.0.1
ping -c 4 1.1.1.1
getent hosts example.com
```

Test the gateway, external IP reachability and DNS resolution as separate checks. A failed ping alone does not prove a host is offline because ICMP may be filtered.

## 3. Shared-folder inspection

```bash
findmnt
ls -la /downloads
ls -la /media
```

The actual mount path depends on the VirtualBox shared-folder name and guest integration. Do not assume that configuration alone proves the folder is mounted or writable.

## 4. Tool versions

```bash
nmap --version
wireshark --version
tshark --version
```

Run only where the tool is installed and relevant to the assigned task.

## 5. Wireshark display filters

Enter these in Wireshark's display-filter bar, not the terminal:

| Purpose | Filter |
|---|---|
| TCP traffic | `tcp` |
| Initial SYN packets | `tcp.flags.syn == 1 && tcp.flags.ack == 0` |
| DNS | `dns` |
| TLS | `tls` |
| ICMP | `icmp` |
| One host | `ip.addr == 10.0.0.2` |

## 6. Scope reminder

Only perform discovery or scanning when the internship brief explicitly authorises it for the assigned lab network. Do not scan public or third-party systems.

## Evidence note

For every check included in a report, record the command, a concise result, the date and the corresponding screenshot filename. Redact personal and sensitive information before publishing.
