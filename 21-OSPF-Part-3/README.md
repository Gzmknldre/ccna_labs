
# OSPF (Part 3)

## Objective

Understand OSPF neighbor relationships, Hello and Dead timers, DR/BDR elections, OSPF network types, and Router ID selection.

## Commands Used

- `show ip ospf neighbor`
- `show ip ospf interface`
- `show ip route`
- `ip ospf priority`
- `ip ospf network point-to-point`
- `ip ospf hello-interval`
- `ip ospf dead-interval`
- `router-id`
- `clear ip ospf process`
- `clock rate`

## What I Learned

- OSPF routers discover and maintain neighbors by exchanging Hello packets.
- Hello packets are sent periodically to maintain neighbor relationships.
- The Hello Timer determines how often Hello packets are sent.
- The Dead Timer determines how long a router waits before declaring a neighbor down.
- Neighboring routers must have matching Hello and Dead timer values.
- The default Hello and Dead timers are 10 and 40 seconds on broadcast and point-to-point networks.
- Hello and Dead timers can be manually configured.
- The default timer values can be restored using the `no` form of the commands.
- OSPF elects a Designated Router (DR) and Backup Designated Router (BDR) on broadcast multi-access networks.
- The DR reduces the number of OSPF adjacencies and LSAs exchanged.
- The BDR takes over if the DR fails.
- OSPF priority influences the DR/BDR election.
- An interface with an OSPF priority of 0 can never become the DR or BDR.
- OSPF network types affect neighbor formation and DR/BDR elections.
- Ethernet interfaces use the Broadcast network type by default.
- Point-to-Point network types do not perform DR/BDR elections.
- The OSPF network type can be changed manually.
- Every OSPF router requires a unique Router ID (RID).
- Router ID selection order:
  1. Manually configured Router ID
  2. Highest Loopback IP address
  3. Highest active physical interface IP address
- If the Router ID is changed after OSPF starts, the OSPF process must be restarted using `clear ip ospf process`.
- On serial DCE interfaces, the `clock rate` command provides clocking for the connection.

## Neighbor Requirements

- Same Area ID
- Matching Hello Timer
- Matching Dead Timer
- Compatible Network Type
- Unique Router ID
- Interfaces must be in the same subnet

## Common Mistakes

- Configuring different Hello or Dead timer values on neighboring routers.
- Forgetting that DR/BDR elections occur only on broadcast multi-access networks.
- Assuming the router with the highest Router ID always becomes the DR (priority is considered first).
- Configuring an OSPF priority of 0 and expecting the router to become the DR or BDR.
- Forgetting to restart the OSPF process after changing the Router ID.
- Forgetting to configure `clock rate` on the DCE side of a serial connection.

## Verification

- `show ip ospf neighbor`
- `show ip ospf interface`
- `show ip route`
