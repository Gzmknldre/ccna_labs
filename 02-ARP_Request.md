# ARP Request

## Objective
Understand how ARP resolves an IPv4 address to a MAC address.

## Topics
- ARP Request
- ARP Reply
- ARP Table
- Broadcast Frame
- MAC Address Resolution

## Commands Used
- arp -a
- show arp
- show mac adress-table
- clear mac adress-table dynamic

## What I Learned
- ARP is used to map an IPv4 address to a MAC address.
- ARP Request is sent as a broadcast.
- ARP Reply is sent as a unicast.
- Devices store learned mappings in the ARP table.
-  `show mac address-table` displays the learned MAC addresses and the associated ports.
- `clear mac address-table dynamic` removes dynamically learned MAC addresses.
- The switch relearns MAC addresses as new traffic passes through it.


<img width="452" height="201" alt="mac-adres-table" src="https://github.com/user-attachments/assets/cd47901c-94c6-46c0-bccb-35402a19cb20" />
<img width="658" height="612" alt="Ethernet_header" src="https://github.com/user-attachments/assets/8a7be1e7-7106-4ab5-86b2-5bac5cb2b656" />
