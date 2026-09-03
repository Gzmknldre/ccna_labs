
# Dynamic NAT and PAT

## Objective

Understand how Dynamic NAT and PAT translate private IPv4 addresses into public IPv4 addresses.

## Dynamic NAT

- Dynamic NAT maps private IP addresses to public IP addresses from a configured **NAT pool**.
- The mapping is created dynamically when an internal host needs translation.
- Dynamic NAT uses a **pool of public addresses**.
- Unlike Static NAT, the mapping is not permanent.
- Dynamic NAT is typically **many-to-many**, depending on the size of the pool.

### Configuration

```bash
access-list 1 permit 192.168.1.0 0.0.0.255

ip nat pool PUBLIC_POOL 203.0.113.10 203.0.113.20 netmask 255.255.255.0

ip nat inside source list 1 pool PUBLIC_POOL
```

### NAT Interfaces

```bash
interface g0/0
ip nat inside
```

```bash
interface g0/1
ip nat outside
```

- `ip nat inside` → Internal/private network interface
- `ip nat outside` → External/public network interface

---

## PAT

**PAT (Port Address Translation)** allows multiple private IP addresses to share a **single public IP address** by using different port numbers.

- PAT is also called **NAT Overload**.
- PAT allows many internal devices to use one public IPv4 address.
- Port numbers distinguish the different connections.
- PAT is commonly used for Internet access.

### Configuration

```bash
access-list 1 permit 192.168.1.0 0.0.0.255

ip nat inside source list 1 interface g0/1 overload
```

- `interface g0/1` → Uses the IP address configured on the outside interface.
- `overload` → Enables PAT.

---

## Dynamic NAT vs PAT

| Dynamic NAT | PAT |
|---|---|
| Uses a pool of public IPs | Can use a single public IP |
| Dynamic mapping | Uses port numbers |
| Multiple public IPs may be required | Many private hosts share one public IP |
| No `overload` | Uses `overload` |
| Many-to-many | Many-to-one |

## Important Terms

### Inside Local

Private IP address of the internal host.

### Inside Global

Public IP address representing the internal host to the outside network.

### Outside Local

Outside device's address as seen from the inside network.

### Outside Global

Actual public IP address of the outside device.

---

## Verification

```bash
show ip nat translations
show ip nat statistics
```

Clear translations:

```bash
clear ip nat translation *
```

## Key Points

```text
Static NAT
Private IP ↔ Public IP
1 : 1
Permanent mapping

Dynamic NAT
Private IP → Public IP from a pool
Dynamic mapping

PAT
Many Private IPs → One Public IP
Uses Port Numbers
NAT Overload
```

## Common Mistakes

- Forgetting `ip nat inside` and `ip nat outside`.
- Using the wrong ACL or NAT pool.
- Forgetting `overload` when configuring PAT.
- Confusing Dynamic NAT with Static NAT.
- Confusing PAT with Dynamic NAT.
- Forgetting that PAT uses port numbers to distinguish connections.

## Verification Flow

```text
Private Host
     ↓
ACL identifies traffic
     ↓
NAT / PAT translation
     ↓
Public IP
     ↓
Internet
```
