# Enhanced Interior Gateway Routing Protocol (EIGRP)

## Objective

Configure EIGRP to dynamically exchange routing information between routers.

## Commands Used

- `router eigrp <AS-number>`
- `network`
- `no auto-summary`
- `passive-interface l0`
- `show ip protocols`
- `show ip route`
- `show ip eigrp neighbors`
- `show ip eigrp topology`
- `ping`

## What I Learned

- EIGRP is an advanced distance-vector routing protocol developed by Cisco.
- Routers must use the same Autonomous System (AS) number to become EIGRP neighbors.
- The `network` command enables EIGRP on matching interfaces.
- EIGRP forms neighbor relationships before exchanging routing information.
- EIGRP uses the DUAL (Diffusing Update Algorithm) algorithm to calculate the best path.
- EIGRP sends partial and triggered updates instead of periodic full updates.
- EIGRP supports equal-cost load balancing.
- `no auto-summary` disables automatic route summarization.
- `show ip eigrp neighbors` displays EIGRP neighbor relationships.
- `show ip eigrp topology` displays the EIGRP topology table.

## Example Configuration

```bash
router eigrp 100
 no auto-summary
 network 10.0.0.0 0.0.0.255
 network 192.168.1.0 0.0.0.255
```

## Common Mistakes

- Using different AS numbers on neighboring routers.
- Advertising the wrong network.
- Forgetting `no auto-summary` in lab environments.
- Interfaces are down or have incorrect IP addressing.

## Verification

- `show ip eigrp neighbors`
- `show ip eigrp topology`
- `show ip protocols`
- `show ip route`
- `ping`
