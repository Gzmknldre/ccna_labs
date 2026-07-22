# Static Routing

## Objective

Configure static routes between three routers and verify end-to-end connectivity.

## Topology

- R1 LAN: `192.168.1.0/24`
- R1-R2: `192.168.12.0/24`
- R2-R3: `192.168.13.0/24`
- R3 LAN: `192.168.3.0/24`

## Configuration

### R1

```bash
ip route 192.168.3.0 255.255.255.0 192.168.12.2
```

### R2

```bash
ip route 192.168.1.0 255.255.255.0 192.168.12.1
ip route 192.168.3.0 255.255.255.0 192.168.13.3
```

### R3

```bash
ip route 192.168.1.0 255.255.255.0 192.168.13.2
```

## Verification

- `show ip route`
- `show ip interface brief`
- Successful ping between PC1 and PC2

## What I Learned

- Static routes must be configured on every router that needs to reach a remote network.
- The next-hop IP address must point to the neighboring router.
- `show ip route` verifies whether static routes have been installed.
- `show ip interface brief` verifies interface IP addresses and status.
- End devices require a correct **default gateway** to communicate with remote networks.

## Troubleshooting

### Issue

PC1 could not ping PC2 even though the routers were configured correctly.

### Cause

The PCs did not have a **default gateway** configured.

### Solution

Configured the default gateways:

- PC1 → `192.168.1.254`
- PC2 → `192.168.3.254`

After configuring the default gateways, end-to-end connectivity was successful.
