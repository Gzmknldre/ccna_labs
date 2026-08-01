# OSPF (Part 1)

## Objective

Configure OSPF to dynamically exchange routing information between routers.

## Commands Used

- `router ospf <process-id>`
- `network <network-address> <wildcard-mask> area <area-id>`
- `show ip ospf neighbor`
- `show ip ospf interface brief`
- `show ip protocols`
- `show ip route`
- `ping`

## What I Learned

- OSPF (Open Shortest Path First) is a link-state routing protocol.
- OSPF is an open standard and works with different vendors.
- OSPF uses the SPF (Shortest Path First) algorithm developed by Dijkstra.
- Routers exchange Link-State Advertisements (LSAs) to build the network topology.
- OSPF forms neighbor relationships before exchanging routing information.
- OSPF uses Areas to improve scalability.
- All routers must belong to the same Area to become neighbors.
- Area 0 is the backbone area and is required in multi-area OSPF networks.
- The `network` command enables OSPF on matching interfaces.
- OSPF uses Router IDs (RID) to uniquely identify routers.

## Example Configuration

```bash
router ospf 1
 network 10.0.12.0 0.0.0.3 area 0
 network 192.168.1.0 0.0.0.255 area 0
```

## Common Mistakes

- Using incorrect wildcard masks.
- Placing neighboring interfaces in different OSPF areas.
- Forgetting to advertise a connected network.
- Duplicate Router IDs.

## Verification

- `show ip ospf neighbor`
- `show ip ospf interface brief`
- `show ip protocols`
- `show ip route`
- `ping`
