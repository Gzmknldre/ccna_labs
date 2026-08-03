# OSPF (Part 2)

## Objective

Understand how OSPF calculates the best path using cost and learn the OSPF neighbor states.

## Commands Used

- `show ip ospf neighbor`
- `show ip ospf interface`
- `show ip route`
- `ip ospf cost`
- `bandwidth`
- `auto-cost reference-bandwidth `

## What I Learned

- OSPF uses cost as its routing metric.
- OSPF always selects the path with the lowest total cost.
- By default, OSPF calculates cost based on interface bandwidth.
- The OSPF cost can be manually configured using the `ip ospf cost` command.
- Changing the interface bandwidth changes the calculated OSPF cost.
- OSPF routers must become neighbors before exchanging routing information.
- Hello messages are multicast 224.0.0.5

## OSPF Neighbor States

- Down
- Init
- Two-Way
- ExStart
- Exchange
- Loading
- Full

## Common Mistakes

- Assuming OSPF chooses the path with the fewest hops.
- Forgetting that OSPF uses cost instead of hop count.
- Misconfiguring the interface bandwidth.
- Configuring an incorrect manual OSPF cost.

## Verification

- `show ip ospf neighbor`
- `show ip ospf interface`
- `show ip route`
