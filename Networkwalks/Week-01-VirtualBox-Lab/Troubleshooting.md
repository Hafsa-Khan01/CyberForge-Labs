# Week 01 — Troubleshooting Notes

Use this file to record real issues and fixes that worked. The entries below are diagnostic suggestions, not claims that these issues occurred.

## Kali has no expected IP
1. Run `ip -br addr` and `ip route`.
2. Confirm the VM adapter uses the intended VirtualBox NAT Network.
3. Confirm the NAT Network subnet and DHCP settings match the brief.
4. Reconnect the guest adapter or restart NetworkManager only if appropriate.
5. Re-check the assigned address and route.

## Gateway or internet check fails
1. Verify guest IP, subnet mask, and default route.
2. Check VirtualBox NAT Network configuration.
3. Test gateway, then public IP, then DNS separately.
4. Record exact errors rather than assuming the cause.

## DNS or website check fails
Compare `nslookup www.networkwalks.com` with `curl -I https://www.networkwalks.com` to identify the failing layer.

## Shared folder is missing
1. Confirm the shared-folder name and path in VirtualBox settings.
2. Confirm the folder is enabled and guest integration tools are available.
3. Check `ls -la /media` for the actual mount path.
4. Do not assume the path is `/media/sf_Downloads` if configured differently.

## Lab log template
- Date:
- Expected behavior:
- Actual behavior:
- Command / setting checked:
- Error or observation:
- Fix attempted:
- Verification after fix:
- Evidence filename:
