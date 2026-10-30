# Week 01 — VirtualBox and Kali Linux Lab

## Objective

Prepare a Kali Linux virtual machine in Oracle VirtualBox for the assigned networking and packet-analysis exercises. The documented work covers VM settings, virtual networking, shared-folder configuration, guest startup and basic network inspection.

## Environment

| Component | Recorded environment |
|---|---|
| Host platform | Windows |
| Virtualisation platform | Oracle VirtualBox |
| Guest operating system | Kali Linux |
| Virtual network | NAT Network |
| Shared-folder reference path | `/downloads` |
| Guest inspection | Kali terminal and network checks |

## Setup workflow

1. Opened the Kali Linux virtual machine in Oracle VirtualBox.
2. Reviewed the VM's general settings.
3. Reviewed the VM network adapter and NAT Network configuration against the internship brief.
4. Reviewed the configured shared-folder settings.
5. Started the Kali guest and inspected the desktop.
6. Performed network-interface and connectivity checks.
7. Captured screenshots of the VM and relevant configuration/verification views.

## Assignment reference configuration

The internship brief specifies a NAT Network of `10.0.0.0/24`, expected Kali address `10.0.0.2/24`, gateway `10.0.0.1` and guest shared-folder path `/downloads`. These are assignment reference values. Do not report them as independently verified active settings unless the relevant screenshot or command output shows them.

## Evidence

The [Evidence folder](Evidence/) contains eight setup screenshots covering the running Kali VM, VM settings, adapter settings, shared-folder configuration, guest network checks, Snapshot Manager and NAT Network Manager.

See [EVIDENCE.md](EVIDENCE.md) for evidence scope, [Commands.md](Commands.md) for repeatable inspection commands and [Troubleshooting.md](Troubleshooting.md) for diagnostic guidance.

## Verification approach

Use the commands in [Commands.md](Commands.md) to inspect addressing, routing, gateway reachability, DNS and shared-folder mounting. Record actual output and date when repeating a check. A configured adapter does not prove end-to-end connectivity or shared-folder read/write access.

## Safety

Do not commit VM disk images, saved-state files, passwords, private keys or unredacted personal information.
