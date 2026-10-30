# TryHackMe Write-up — What Is Networking

## Objective
Understand how devices exchange data across local and routed networks.

## Concepts
A network connects endpoints so they can exchange data. Switches forward frames within a local network; routers forward packets between networks. IP addresses support logical addressing, MAC addresses support local link delivery, DNS resolves names, and DHCP provides network configuration.

## Investigation Approach
Identify the source and destination, determine whether they are on the same subnet, inspect the default gateway and DNS resolver, and test connectivity only within the authorized lab.

## Learning Reflection
Network troubleshooting becomes clearer when separating link-layer, IP routing, transport and application-layer problems.
