# DHCP

## Objective

Understand how DHCP automatically provides IP addressing information to network clients.

## Commands Used

```bash
ip dhcp excluded-address <start-ip> <end-ip>
ip dhcp pool <pool-name>
network <network-address> <subnet-mask>
default-router <gateway-ip>
dns-server <dns-server-ip>

show ip dhcp binding
show ip dhcp pool
show ip dhcp server statistics
```

## What I Learned

- DHCP (Dynamic Host Configuration Protocol) automatically assigns IP configuration to clients.
- DHCP can provide:
  - IP address
  - Subnet mask
  - Default gateway
  - DNS server
- A Cisco router can be configured to act as a DHCP server.
- `ip dhcp excluded-address` prevents specific addresses from being assigned to clients.
- `ip dhcp pool` creates a DHCP pool.
- `network` defines the address range that DHCP can assign.
- `default-router` specifies the default gateway given to clients.
- `dns-server` specifies the DNS server given to clients.

## DHCP DORA Process

```text
Discover
    ↓
Offer
    ↓
Request
    ↓
ACK
```

- **Discover** → Client searches for a DHCP server.
- **Offer** → DHCP server offers an IP address.
- **Request** → Client requests the offered address.
- **ACK** → DHCP server confirms the assignment.

## Basic Configuration

```bash
ip dhcp excluded-address 192.168.1.1 192.168.1.10

ip dhcp pool LAN
network 192.168.1.0 255.255.255.0
default-router 192.168.1.1
dns-server 8.8.8.8
```

## DHCP Relay

When the DHCP server is on a different network, a router can forward DHCP requests using:

```bash
ip helper-address <DHCP-server-IP>
```

- DHCP clients initially use broadcast messages.
- Routers do not normally forward broadcasts.
- `ip helper-address` forwards the DHCP request toward the DHCP server.

## Verification

```bash
show ip dhcp binding
show ip dhcp pool
show ip dhcp server statistics
```

## Common Mistakes

- Forgetting to exclude addresses that should be reserved.
- Using the wrong network address or subnet mask.
- Configuring the wrong default gateway.
- Forgetting `ip helper-address` when the DHCP server is on another network.
- Checking the wrong DHCP pool or interface.
