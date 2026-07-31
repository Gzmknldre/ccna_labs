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
-  The VTP revision number increases whenever the VLAN database is modified on a VTP Server.
- VTP Clients update their VLAN database when they receive advertisements with a higher revision number.
- A switch with a higher revision number can overwrite the VLAN database of other switches in the same VTP domain.

  ## Important Notes

- Always verify the VTP revision number before adding a switch to an existing VTP domain.
- A higher revision number can overwrite the VLAN database on other switches.

## Verification

- `show vtp status`
- `show vlan brief`
