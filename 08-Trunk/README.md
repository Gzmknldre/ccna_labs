# Trunk

## Objective

Configure trunk links between switches and control which VLANs are allowed to pass through the trunk.

## Commands Used

- `switchport mode trunk`
- `switchport trunk native vlan`
- `switchport trunk allowed vlan`
- `switchport trunk allowed vlan add`
- `switchport trunk allowed vlan remove`
- `show interfaces trunk`
- `show interfaces switchport`
- `show vlan brief`

## What I Learned

- A trunk link carries traffic for multiple VLANs.
- IEEE 802.1Q (dot1Q) is the standard trunking protocol used on Cisco switches.
- Trunk ports allow multiple VLANs to travel over a single physical link.
- Native VLAN traffic is sent untagged.
- Both ends of a trunk should have the same native VLAN.
- By default, all VLANs are allowed on a trunk.
- `switchport trunk allowed vlan` specifies which VLANs are allowed on the trunk.
- `switchport trunk allowed vlan add` adds VLANs to the existing allowed VLAN list.
- `switchport trunk allowed vlan remove` removes VLANs from the allowed VLAN list.
- `show interfaces trunk` displays trunk ports, native VLAN, and allowed VLANs.
- `show interfaces switchport` displays the administrative and operational mode of a switch port.
- `show vlan brief` displays existing VLANs and access port assignments.

## Example Configuration

```bash
interface g0/1
 switchport mode trunk
 switchport trunk native vlan 999
 switchport trunk allowed vlan 10,20

switchport trunk allowed vlan add 30
switchport trunk allowed vlan remove 20
```

## Verification

- `show interfaces trunk`
- `show interfaces switchport`
- `show vlan brief`
- Verify that only the configured VLANs are allowed across the trunk.
