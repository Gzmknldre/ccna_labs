# Static NAT

## Objective

Understand how Static NAT maps a private IPv4 address to a public IPv4 address.

## What I Learned

- **NAT (Network Address Translation)** translates private IP addresses into public IP addresses.
- **Static NAT** creates a permanent one-to-one mapping between a private IP address and a public IP address.
- The mapping remains until it is manually removed.
- Static NAT is useful when an internal device needs to be reachable from the outside using a consistent public IP.
- Static NAT uses a **1:1 relationship**.

## Important Terms

- **Inside Local** → The private IP address assigned to the internal device.
- **Inside Global** → The public IP address representing the internal device to the outside network.
- **Outside Local** → The outside device's address as seen from the inside network.
- **Outside Global** → The actual public IP address of the outside device.

## Static NAT Configuration

```bash
ip nat inside source static <inside-local> <inside-global>
```

Example:

```bash
ip nat inside source static 192.168.1.10 203.0.113.10
```

This creates a permanent mapping:

```text
192.168.1.10  ↔  203.0.113.10
Private            Public
```

## Configure NAT Interfaces

The interface connected to the internal network is configured as **inside**:

```bash
interface g0/0
ip nat inside
```

The interface connected to the external network is configured as **outside**:

```bash
interface g0/1
ip nat outside
```

## Verification

```bash
show ip nat translations
show ip nat statistics
```

### Clear NAT Translations

```bash
clear ip nat translation *
```

## Key Points

```text
Static NAT
    ↓
Permanent Mapping
    ↓
Private IP ↔ Public IP
    ↓
1 : 1
```

- Static NAT = **one private IP ↔ one public IP**
- Mapping is manually configured.
- `ip nat inside` → Internal interface
- `ip nat outside` → External interface
- `show ip nat translations` → View NAT mappings

## Common Mistakes

- Configuring `ip nat inside` on the wrong interface.
- Configuring `ip nat outside` on the wrong interface.
- Mixing up inside local and inside global addresses.
- Forgetting that Static NAT uses a 1:1 mapping.
- Forgetting to verify the NAT translation table.
