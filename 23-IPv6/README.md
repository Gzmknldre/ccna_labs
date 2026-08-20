# IPv6

## Objective

Understand IPv6 addressing, address types, EUI-64, IPv6 routing, multicast scopes, and how IPv6 is enabled on Cisco devices.

## Commands Used

- `ipv6 address <IPv6-address>/<prefix-length>`
- `ipv6 address <prefix>/<prefix-length> eui-64`
- `ipv6 enable`
- `ipv6 route <destination-prefix>/<prefix-length> <next-hop>`
- `show ipv6 interface`
- `show ipv6 interface brief`
- `show ipv6 route`
- `ping`

## What I Learned

- IPv6 uses 128-bit addresses.
- IPv6 addresses are written in hexadecimal and separated by colons.
- IPv6 does not use broadcast addresses.
- IPv6 uses multicast and anycast for specific communication purposes.
- The prefix identifies the network portion of the address.
- The interface ID identifies the interface within the network.

## IPv6 Address Types

### Unicast

- Global Unicast Address (GUA)
- Link-Local Address
- Unique Local Address (ULA)

### Multicast

- Multicast addresses begin with `FF00::/8`.
- IPv6 multicast addresses use different scopes to define how far multicast traffic can reach.

### Anycast

- An anycast address can be assigned to multiple interfaces.
- Traffic is delivered to the nearest interface according to the routing topology.

## EUI-64

- EUI-64 automatically generates the interface ID using the interface MAC address.
- The MAC address is split into two 24-bit parts.
- `FFFE` is inserted between the two parts.
- The Universal/Local (U/L) bit is inverted.

Example:

```bash
ipv6 address 2001:DB8:1:1::/64 eui-64



##IPv6 Enable

interface g0/0
ipv6 enable
ipv6 enable enables IPv6 processing on the interface.
It automatically generates a link-local IPv6 address.
A global IPv6 address does not have to be configured for the interface to have a link-local address.
IPv6 Static Routing
ipv6 route 2001:DB8:2:2::/64 2001:DB8:1:2::2
IPv6 static routes are configured using ipv6 route.
The destination is specified using an IPv6 prefix and prefix length.
A next-hop IPv6 address can be specified.

##Multicast Scopes

IPv6 multicast addresses contain a scope field.
The scope determines the range within which multicast traffic is valid.
Different scopes are used for different communication ranges.

##Common Mistakes

Forgetting that IPv6 does not use broadcast.
Confusing link-local addresses with global unicast addresses.
Forgetting the prefix length when configuring IPv6 addresses.
Using ip route instead of ipv6 route for IPv6 static routing.
Forgetting that ipv6 enable automatically creates a link-local address.
Confusing multicast scopes and their ranges.


##Verification

show ipv6 interface
show ipv6 interface brief
show ipv6 route
ping
