# Week 01 — Command Reference

Run these inside the Kali VM unless noted. Compare outputs with the internship brief and your actual environment.

## Host and network configuration
`whoami`  
`hostname`  
`cat /etc/os-release`  
`ip -br addr`  
`ip route`  
`ip link show`  
`ip neigh show`

## Connectivity checks
`ping -c 4 10.0.0.1`  
`ping -c 4 8.8.8.8`  
`nslookup www.networkwalks.com`  
`curl -I https://www.networkwalks.com`

A failed ping alone does not always prove a host is offline; ICMP may be filtered.

## Tool versions
`nmap --version`  
`wireshark --version`  
`tshark --version`

## Authorized lab host discovery
Only if the brief authorizes discovery on this virtual subnet: `nmap -sn 10.0.0.0/24`

## Evidence directory
`mkdir -p ~/Documents/Networkwalks-Week1/Evidence`  
`ls -la ~/Documents/Networkwalks-Week1/Evidence`

## Shared folder check
The mount path depends on the VirtualBox shared-folder name and guest integration: `ls -la /media` and `ls -la /media/sf_Downloads`

## Wireshark display filters
Enter these in Wireshark's display-filter bar, not the terminal: `dns`, `tls`, `tcp`, `icmp`, `ip.addr == 10.0.0.2`

Record the date, command, short result, and screenshot filename. Remove sensitive information before publishing evidence.
