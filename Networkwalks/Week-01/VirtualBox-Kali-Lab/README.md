# Week 01 — VirtualBox and Kali Linux Lab

## Practical objective

Prepare a local Kali Linux virtual environment in Oracle VirtualBox for the NetworkWalks Week 01 cybersecurity exercises. The setup work covered VM configuration, virtual networking, shared-folder settings, guest startup and basic network inspection.

## Environment

| Component | Details |
|---|---|
| Host platform | Windows |
| Virtualisation platform | Oracle VirtualBox |
| Guest operating system | Kali Linux |
| Virtual network | NAT Network |
| Shared-folder reference path | `/downloads` |
| Network inspection | Kali terminal interface and connectivity checks |

## Setup workflow

1. Prepared and opened the Kali Linux VM in Oracle VirtualBox.
2. Reviewed the VM's general settings.
3. Configured/reviewed the VM network adapter and the VirtualBox NAT Network.
4. Reviewed the shared-folder configuration for the guest.
5. Started Kali Linux and inspected the guest environment.
6. Performed network-interface and connectivity checks from Kali.
7. Captured screenshots of the VM, configuration panels and network checks.

## Assignment network reference

The internship brief specifies a NAT Network of `10.0.0.0/24`, expected Kali address `10.0.0.2/24`, gateway `10.0.0.1` and guest shared-folder path `/downloads`. These values describe the assignment's reference configuration. Use the relevant screenshots or terminal output when stating the exact active address or confirming shared-folder access.

## Evidence

The [Evidence folder](Evidence/) contains eight screenshots documenting:

- Kali Linux running in the VirtualBox VM
- VirtualBox general VM settings
- VM network-adapter settings
- Shared-folder configuration
- Kali network connectivity and interface checks
- VirtualBox Snapshot Manager
- VirtualBox NAT Network Manager

See [EVIDENCE.md](EVIDENCE.md) for evidence notes and verification guidance, and the [Week 01 practical report](../Wireshark-SOC-Labs/REPORT.md) for the combined VirtualBox/Kali and Wireshark report.

## Verification commands

```bash
ip -br address
ip route
ip neigh
ping -c 4 10.0.0.1
getent hosts example.com
findmnt
ls -la /downloads
```

These commands inspect addressing, routing, gateway reachability, DNS resolution, mounted filesystems and shared-folder visibility. Do not infer a successful check unless its output is available.

## Safety

Do not commit VM disk images, saved-state files, passwords, private keys or unredacted personal information.
