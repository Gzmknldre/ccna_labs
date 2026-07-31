# VLAN Trunking Protocol (VTP)

## Objective

Configure VTP to synchronize VLAN information between Cisco switches.

## Commands Used

- `vtp domain`
- `vtp mode server`
- `vtp mode client`
- `vtp mode transparent`
- `vtp password`
- `vtp version`
- `show vtp status`
- `show vlan brief`

## What I Learned

- VTP is a Cisco proprietary protocol used to distribute VLAN information.
- VTP operates only over trunk links.
- VTP Server can create, modify, and delete VLANs.
- VTP Client receives VLAN information but cannot modify VLANs.
- VTP Transparent does not synchronize VLANs but forwards VTP advertisements.
- All switches must have the same VTP domain name.
- A VTP password can be configured for authentication.
- `show vtp status` displays the VTP operating mode, domain name, and revision number.
- VLAN changes made on a VTP Server are propagated to VTP Clients.

## Verification

- `show vtp status`
- `show vlan brief`
