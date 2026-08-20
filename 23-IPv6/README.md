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


## IPv6 Enable

```bash
interface g0/0
ipv6 enable
```

* Enables IPv6 processing on the interface.
* Automatically generates a **Link-Local** IPv6 address.
* A Global Unicast address does not need to be configured to have a Link-Local address.

---

## IPv6 Static Routing

```bash
ipv6 route 2001:DB8:2:2::/64 2001:DB8:1:2::2
```

* IPv6 static routes are configured using `ipv6 route`.
* The destination is specified using an IPv6 prefix and prefix length.
* A next-hop IPv6 address can be specified.
* Use `ipv6 route`, **not** `ip route`, for IPv6 networks.

---

## IPv6 Multicast Scopes

IPv6 does **not use broadcast**. Multicast is used instead.

IPv6 multicast addresses contain a **Scope** field that determines the range within which multicast traffic is valid.

Common scopes:

* **1 – Interface-Local:** Limited to a single interface.
* **2 – Link-Local:** Limited to the local link.
* **5 – Site-Local:** Limited to a site/organization.
* **8 – Organization-Local:** Limited to an organization.
* **E – Global:** Global scope.

---

## IPv6 Address Types

* **Global Unicast:** Routable on the Internet.
* **Link-Local:** `FE80::/10` — used for communication on the local link.
* **Unique Local:** `FC00::/7` — private IPv6 addressing.
* **Multicast:** `FF00::/8` — one-to-many communication.
* **Loopback:** `::1`
* **Unspecified:** `::`

---

## Common Mistakes

* Forgetting that IPv6 does **not use broadcast**.
* Confusing **Link-Local** and **Global Unicast** addresses.
* Forgetting the **prefix length** when configuring IPv6 addresses.
* Using `ip route` instead of `ipv6 route`.
* Forgetting that `ipv6 enable` automatically creates a Link-Local address.
* Confusing multicast scopes and their ranges.

---

## Verification

```bash
show ipv6 interface
show ipv6 interface brief
show ipv6 interface g0/0
show ipv6 route
ping
```

### Key Point

> IPv6 uses **multicast instead of broadcast**, Link-Local addresses are automatically generated with `ipv6 enable`, and IPv6 static routes use `ipv6 route`.
