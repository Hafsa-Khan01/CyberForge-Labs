# VirtualBox & Kali Linux — Evidence Notes

The supplied source archive contains one Kali desktop screenshot and seven additional VirtualBox configuration screenshots. The visible material includes VM settings, network adapter configuration and shared-folder configuration.

## Assignment reference configuration

The NetworkWalks brief specifies a NAT Network of 10.0.0.0/24, expected Kali address 10.0.0.2/24, gateway 10.0.0.1 and guest shared-folder path /downloads. These are assignment expectations unless the specific value is visible in evidence or actual command output.

## Verification commands

```bash
ip -br address
ip route
ping -c 4 10.0.0.1
getent hosts example.com
findmnt
ls -la /downloads
```

Record actual output and date. A configured adapter does not by itself prove connectivity or shared-folder read/write access.

## Screenshot destination

Place reviewed screenshots in this folder. Before public release, redact host usernames, local paths, MAC addresses, credentials and unrelated device details. Do not add VM disk images or saved-state files.
