# Dynamic Trunking Protocol (DTP)

## Objective

Understand how Cisco switches automatically negotiate trunk links using DTP.

## Commands Used

- `switchport mode dynamic auto`
- `switchport mode dynamic desirable`
- `switchport mode trunk`
- `switchport mode access`
- `switchport nonegotiate`
- `show interfaces switchport`
- `show interfaces trunk`

## What I Learned

- DTP is a Cisco proprietary protocol used to negotiate trunk links.
- `dynamic auto` waits for the other switch to initiate trunking.
- `dynamic desirable` actively attempts to form a trunk.
- `trunk` forces the port to operate as a trunk.
- `access` forces the port to operate as an access port.
- `switchport nonegotiate` disables DTP negotiation.
- `show interfaces switchport` displays the administrative and operational mode.
- `show interfaces trunk` verifies active trunk links.

## Verification

- `show interfaces switchport`
- `show interfaces trunk`
