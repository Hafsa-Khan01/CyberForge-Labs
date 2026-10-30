# TryHackMe Write-up — Networking Concepts

## Objective
Understand how network components and protocols work together to deliver traffic.

## Concepts
A frame is carried on a local link; an IP packet is routed between networks; TCP or UDP carries application data. DNS resolves hostnames, ARP discovers a local IPv4-to-MAC mapping, and ICMP supports diagnostics and error reporting.

## Approach
Map the communication path from source host to destination, identify the relevant layer and protocol, then use basic tools such as `ip a`, `ip route`, `ping`, `traceroute` and `nslookup` in the lab.

## Learning Reflection
Understanding encapsulation helps interpret packet captures and narrow down connectivity issues.
