# Week 01 — VirtualBox and Kali Linux Lab

## Objective
Set up a local virtual cybersecurity lab and prepare Kali Linux for networking and packet-analysis exercises.

## Environment recorded in the internship brief
- Virtualisation platform: Oracle VirtualBox
- Guest operating system: Kali Linux
- NAT Network: 10.0.0.0/24
- Expected Kali address: 10.0.0.2/24
- Expected gateway: 10.0.0.1
- Shared folder path inside the guest: /downloads

These are the assignment's expected settings. Refer to screenshots and actual command outputs before treating an individual setting as independently verified.

## Work and evidence supplied
The supplied evidence package includes screenshots showing VirtualBox VM configuration, network adapter settings, shared-folder configuration, Kali Linux running in VirtualBox, and terminal/network-analysis activity.

## Practical verification commands
    ip -br address
    ip route
    ping -c 4 10.0.0.1
    ping -c 4 1.1.1.1
    getent hosts example.com

For a configured shared folder, verify the mount and read/write access using the actual guest mount path.

## Evidence and safety
See the [Week 01 evidence index](../EVIDENCE-INDEX.md). Do not commit VM disk files, saved-state files, passwords, private keys, or unredacted personal data.
