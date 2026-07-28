# Layer 3 Switch Inter-VLAN Routing

## Objective

Configure inter-VLAN routing using a Layer 3 switch instead of Router-on-a-Stick.

## Commands Used

- `no interface g0/0.<VLAN-ID>`
- `default interface g0/0`
- `no switchport`
- `ip address`
- `interface vlan`
- `no shutdown`
- `ip routing`
- `ip route 0.0.0.0 0.0.0.0 <next-hop-ip>`
- `show ip interface brief`
- `show ip route`
- `ping`

## Configuration Steps

1. Removed the Router-on-a-Stick subinterfaces.
2. Converted the switch port into a Layer 3 routed port using `no switchport`.
3. Assigned an IP address to the routed port.
4. Created an SVI (Switch Virtual Interface) for each VLAN.
5. Assigned an IP address to each SVI.
6. Enabled all SVIs using `no shutdown`.
7. Enabled Layer 3 routing with `ip routing`.
8. Configured a default route to the next-hop router.
9. Verified connectivity using `show` commands and `ping`.

## What I Learned

- A Layer 3 switch can route traffic between VLANs.
- Router subinterfaces are not required when using a Layer 3 switch.
- `no switchport` converts a Layer 2 interface into a Layer 3 routed port.
- Routed ports can be assigned an IP address directly.
- Each VLAN requires its own Switch Virtual Interface (SVI).
- The IP address of an SVI acts as the default gateway for hosts in that VLAN.
- `ip routing` enables routing on the Layer 3 switch.
- A default route (`0.0.0.0/0`) forwards traffic destined for unknown networks to the next-hop router.
- Layer 3 switching provides faster inter-VLAN routing than Router-on-a-Stick.

## Common Mistakes

- I tried to assign an IP address before using `no switchport`.
- A Layer 2 switch port cannot be assigned an IP address directly.
- The issue was resolved by converting the interface into a routed port using `no switchport`.

## Verification

- `show ip interface brief`
- `show ip route`
- Successful ping between devices in different VLANs.
