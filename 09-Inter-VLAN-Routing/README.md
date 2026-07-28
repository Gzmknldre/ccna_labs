# Inter-VLAN Routing (Router-on-a-Stick)

## Objective

Configure Router-on-a-Stick to enable communication between different VLANs using router subinterfaces.

## Commands Used

- `interface g0/0.10`
- `encapsulation dot1Q`
- `encapsulation dot1Q native`
- `ip address`
- `no shutdown`
- `show ip interface brief`
- `show running-config`
- `show interfaces trunk`
- `ping`

## What I Learned

- Devices in different VLANs cannot communicate without Layer 3 routing.
- Router-on-a-Stick uses a single physical interface with multiple subinterfaces.
- Each VLAN requires its own subinterface.
- Subinterfaces are created using the format `interface g0/0.<VLAN-ID>`.
- `encapsulation dot1Q <VLAN-ID>` assigns a subinterface to a specific VLAN.
- The IP address configured on a subinterface acts as the default gateway for that VLAN.
- A trunk link is required between the router and the switch.
- Native VLANs can be configured using `encapsulation dot1Q <VLAN-ID> native`.
- Traffic from the native VLAN is sent untagged.
- `show ip interface brief` can be used to verify subinterface status and IP addresses.

## Example Configuration

```bash
interface g0/0
 no shutdown

interface g0/0.10
 encapsulation dot1Q 10
 ip address 10.0.0.62 255.255.255.192

interface g0/0.20
 encapsulation dot1Q 20
 ip address 10.0.0.126 255.255.255.192

interface g0/0.30
 encapsulation dot1Q 30 
 ip address 10.0.0.190 255.255.255.192
```

## Verification

- `show ip interface brief`
- `show running-config`
- `show interfaces trunk`
- Successful ping between devices in different VLANs.
