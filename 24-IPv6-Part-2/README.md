# IPv6 Static Route

## Objective

Configure static routes to manually define a path to remote IPv6 networks.

## 1. Network Route

A network route is used to reach an entire IPv6 network.

```bash
ipv6 route 2001:DB8:2:2::/64 2001:DB8:1:2::2
```

- `2001:DB8:2:2::/64` → Destination network
- `2001:DB8:1:2::2` → Next-hop IPv6 address

## 2. Host Route

A host route is used to reach a specific IPv6 host.

```bash
ipv6 route 2001:DB8:2:2::10/128 2001:DB8:1:2::2
```

- `/128` identifies a single IPv6 host.
- IPv6 host routes use a `/128` prefix.

## 3. Fully Specified Route

A fully specified static route specifies both the exit interface and the next-hop IPv6 address.

```bash
ipv6 route 2001:DB8:2:2::/64 g0/1 2001:DB8:1:2::2
```

- `2001:DB8:2:2::/64` → Destination network
- `g0/1` → Exit interface
- `2001:DB8:1:2::2` → Next-hop IPv6 address

## What I Learned

- IPv6 static routes are configured using the `ipv6 route` command.
- A network route uses the network prefix.
- A host route uses `/128` to identify one specific host.
- A fully specified route includes both the exit interface and next-hop address.
- Static routes manually define the path to a destination.

## IPv4 vs IPv6

```text
IPv4 → ip route
IPv6 → ipv6 route
```

## Verification

```bash
show ipv6 route
ping
```

## Common Mistakes

- Using `ip route` instead of `ipv6 route`.
- Forgetting the prefix length.
- Using the wrong next-hop IPv6 address.
- Forgetting the exit interface when configuring a fully specified route.
