# EtherChannel

## Objective

Configure EtherChannel to combine multiple physical links into a single logical link for increased bandwidth and redundancy.

## Commands Used

- `channel-group <number> mode active`
- `channel-group <number> mode passive`
- `channel-group <number> mode desirable`
- `channel-group <number> mode auto`
- `interface port-channel <number>`
- `switchport mode trunk`
- `switchport trunk allowed vlan`
- `show etherchannel summary`
- `show etherchannel port-channel`
- `show interfaces port-channel`
- `show interfaces trunk`

## What I Learned

- EtherChannel combines multiple physical interfaces into one logical interface.
- EtherChannel provides increased bandwidth and link redundancy.
- STP treats an EtherChannel as a single logical link.
- All interfaces in an EtherChannel must have the same speed and duplex settings.
- All interfaces must have the same switchport configuration.
- LACP (IEEE 802.3ad) is an open standard.
- PAgP is a Cisco proprietary protocol.
- LACP Active actively negotiates an EtherChannel.
- LACP Passive waits for the other side to initiate negotiation.
- PAgP Desirable actively negotiates an EtherChannel.
- PAgP Auto waits for the other side to initiate negotiation.
- "On" mode creates a static EtherChannel without negotiation.

## EtherChannel Modes

### LACP
- `active`
- `passive`

### PAgP
- `desirable`
- `auto`

### Static
- `on`

## Common Mistakes

- Interfaces have different speeds or duplex settings.
- Interfaces belong to different VLANs.
- One interface is configured as a trunk while another is an access port.
- Using incompatible EtherChannel negotiation modes.
- Forgetting to configure the Port-Channel interface.

## Verification

- `show etherchannel summary`
- `show etherchannel port-channel`
- `show interfaces trunk`
