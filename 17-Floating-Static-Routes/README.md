# Floating Static Route

## Objective

Configure a floating static route to provide a backup path when the primary route fails.

## Commands Used

- `ip route`
- `show ip route`
- `show running-config`
- `ping`
- `traceroute`

## What I Learned

- A floating static route is a backup static route.
- It is used only when the primary route becomes unavailable.
- A floating static route has a higher Administrative Distance (AD) than the primary route.
- The router always prefers the route with the lowest Administrative Distance.
- If the primary route fails, the floating static route is automatically installed in the routing table.
- Floating static routes provide redundancy and improve network reliability.

## Example Configuration

```bash
! Primary static route
ip route 192.168.3.0 255.255.255.0 10.0.12.2

! Backup (floating) static route
ip route 192.168.3.0 255.255.255.0 10.0.13.2 5
```

## Common Mistakes

- Configuring the same Administrative Distance for both routes.
- Using a lower Administrative Distance on the backup route.
- Forgetting that the floating route does not appear in the routing table while the primary route is available.

## Verification

- `show ip route`
- `ping`
- `traceroute`
