# VLAN (Virtual Local Area Network)

## Objective

Create VLANs, assign switch ports to VLANs, and verify communication between devices in the same VLAN.

## Commands Used

- `vlan`
- `name`
- `interface`
- `switchport mode access`
- `switchport access vlan`
- `show vlan brief`

## What I Learned

- VLANs logically divide a switch into separate broadcast domains.
- Devices in the same VLAN can communicate directly through the switch.
- Devices in different VLANs require inter-VLAN routing to communicate.
- Access ports belong to a single VLAN.
- `show vlan brief` displays VLAN IDs, names, and assigned interfaces.
- Switch ports are assigned to VLANs using the `switchport access vlan` command.
-  VLAN 1 is the default VLAN on Cisco switches.
- VLANs 1002–1005 are reserved legacy VLANs and exist by default.

## Verification

- `show vlan brief`
- Successful ping between devices in the same VLAN.
