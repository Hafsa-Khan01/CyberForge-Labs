# VirtualBox & Kali Linux — Evidence Notes

The Week 01 submission includes eight VirtualBox/Kali setup screenshots. They are organised in the [Evidence folder](Evidence/) and cover the running Kali desktop, VM settings, network adapter, shared-folder configuration, guest network checks, Snapshot Manager and NAT Network Manager.

## Assignment reference configuration

The NetworkWalks brief specifies a NAT Network of `10.0.0.0/24`, expected Kali address `10.0.0.2/24`, gateway `10.0.0.1` and guest shared-folder path `/downloads`. These are assignment expectations unless the specific value is visible in evidence or actual command output.

## Verification commands

```bash
ip -br address
ip route
ping -c 4 10.0.0.1
getent hosts example.com
findmnt
ls -la /downloads
```

Record actual output and date when repeating a check. A configured adapter does not by itself prove connectivity or shared-folder read/write access.

## Evidence handling

Keep screenshots in this folder and preserve their relationship to the setup steps they document. Before public release, redact host usernames, local paths, MAC addresses, credentials and unrelated device details. Do not add VM disk images or saved-state files.
