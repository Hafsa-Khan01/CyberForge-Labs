# TryHackMe Write-up — Live Host Discovery

## Objective
Understand how to identify active hosts within an authorized network range.

## Concepts
Host discovery can use ICMP echo, TCP probes, UDP probes and ARP on a local Ethernet segment. Firewalls may block probes, so a host that does not respond is not necessarily offline.

## Method
Verify the assigned subnet and authorization, use a bounded host-discovery scan, record the exact command and output, and compare results with known lab inventory.

## Learning Reflection
Discovery results depend on network location, filtering and probe type. Record limitations rather than assuming silence means absence.
