# Variable Length Subnet Masking (VLSM)

## Objective

Design a network using VLSM and configure router interfaces with the correct IP addresses.

## Commands Used

- `ip address <ip-address> <subnet-mask>`
- `no shutdown`
- `show ip interface brief`

## What I Learned

- VLSM allows subnetting based on different host requirements.
- Larger subnets should be allocated before smaller ones.
- Each subnet has a unique network address and broadcast address.
- Router interfaces must be configured with a valid IP address and subnet mask.
- The last usable IP address can be assigned to a router interface.
- Point-to-point links commonly use a `/30` subnet because only two usable IP addresses are required.
- `show ip interface brief` verifies interface status and IP addressing.

## Verification

- All router interfaces are `up/up`.
- Devices can communicate successfully after correct VLSM addressing.


| Network | Prefix | Subnet Mask     | Usable Hosts |
| ------- | ------ | --------------- | -----------: |
| LAN 1   | /25    | 255.255.255.128 |          126 |
| LAN 2   | /26    | 255.255.255.192 |           62 |
| LAN 3   | /27    | 255.255.255.224 |           30 |

