# VirtualBox & Kali Linux — Troubleshooting Guide

This guide provides diagnostic steps for common lab-setup problems. It does not claim that every listed issue occurred during the Week 01 setup. Record only issues actually encountered.

## 1. Kali does not receive the expected IP address

1. Run `ip -br address` and `ip route` inside Kali.
2. Confirm the VM's selected adapter is connected to the intended VirtualBox NAT Network.
3. Review the NAT Network subnet and DHCP configuration against the assignment brief.
4. Reconnect the adapter or renew the guest network configuration only when appropriate.
5. Re-run the checks and record the address and route actually shown.

## 2. Gateway or internet connectivity fails

1. Check the guest IP address and subnet.
2. Inspect the default route with `ip route`.
3. Test the configured gateway separately.
4. Test external IP reachability separately from DNS.
5. Record exact errors; do not assume the cause from one failed ping.

## 3. DNS resolution fails

1. Check whether the gateway is reachable.
2. Run `getent hosts example.com`.
3. Compare name resolution with a direct connectivity test.
4. Record the resolver error and the observed result before changing settings.

## 4. Shared folder is not visible

1. Review the shared-folder name and path in VirtualBox settings.
2. Confirm the folder is enabled and the guest integration tools are available.
3. Inspect mounts with `findmnt` and available directories with `ls -la /media`.
4. Check the configured guest mount path; do not assume it must be `/downloads` or `/media/sf_Downloads`.
5. Verify read/write access only if the assignment requires it.

## 5. Record a real troubleshooting event

| Field | Record |
|---|---|
| Date/time | When the issue occurred |
| Expected behaviour | What the assignment required |
| Actual behaviour | Exact observed result or error |
| Diagnostic step | Command or setting inspected |
| Change made | Specific corrective action, if any |
| Verification | Evidence that the issue was resolved or remains open |
| Evidence | Screenshot/log filename |

If no issue occurred, do not invent one for the report or submission form.
