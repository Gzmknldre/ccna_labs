# Spanning Tree Protocol (STP)

## Objective

Understand how Spanning Tree Protocol (STP) prevents Layer 2 loops and creates a loop-free network topology.

## Commands Used

- `show spanning-tree`
- `show spanning-tree detail`
- `show spanning-tree summaary`
- `show spanning-tree vlan`
- `show spanning-tree root`
- `spanning-tree vlan <VLAN-ID> priority <value>`
- `spanning-tree vlan <VLAN-ID> root primary`
- `spanning-tree vlan <VLAN-ID> root secondary`

## What I Learned

- STP (Spanning Tree Protocol) prevents Layer 2 switching loops.
- STP creates a loop-free topology by blocking redundant links.
- Broadcast storms can occur when Layer 2 loops exist.
- Duplicate frames and MAC address table instability can also occur because of loops.
- STP elects one switch as the Root Bridge.
- The Root Bridge is the switch with the lowest Bridge ID (BID).
- A Bridge ID consists of the Bridge Priority and the MAC address.
- If two switches have the same priority, the switch with the lower MAC address becomes the Root Bridge.
- All ports on the Root Bridge are Designated Ports (DP).
- Every non-root switch selects one Root Port (RP), which is the lowest-cost path to the Root Bridge.
- Each network segment has one Designated Port responsible for forwarding traffic.
- Redundant ports become Alternate Ports and remain in the Blocking state.
- STP automatically recalculates the topology if a link fails.
- Path Cost is used to determine the best path to the Root Bridge.
- Lower path cost is preferred.
- Bridge Priority can be manually changed to influence the Root Bridge election.

## Port Roles

- Root Port (RP): Best path toward the Root Bridge.
- Designated Port (DP): Forwards traffic for a network segment.
- Alternate Port (AP): Backup path that remains blocked until needed.

## Port States

- Blocking
- Listening
- Learning
- Forwarding
- Disabled

## Common Mistakes

- Creating Layer 2 loops without STP can cause broadcast storms.
- Forgetting that the lowest Bridge ID wins the Root Bridge election.
- Assuming the lowest MAC address always wins (priority is compared first).
- Confusing Root Ports with Designated Ports.

## Verification

- `show spanning-tree`
- `show spanning-tree vlan`
- `show spanning-tree root`
