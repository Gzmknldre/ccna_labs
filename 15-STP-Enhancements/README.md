# STP Enhancements

## Objective

Learn how STP enhancements improve network performance and protect the network from Layer 2 issues.

## Commands Used

- `spanning-tree portfast`
- `spanning-tree portfast default`
- `spanning-tree bpduguard enable`
- `spanning-tree portfast bpduguard default`
- `spanning-tree bpdufilter enable`
- `spanning-tree guard root`
- `show spanning-tree interface`
- `spanning-tree link-type point-to-point`
- `show spanning-tree summary`
- `spanning-tree vlan 1 cost`
- `spanning-tree vlan 1 priority `

## What I Learned

- PortFast allows an access port to transition directly to the Forwarding state.
- PortFast should only be enabled on ports connected to end devices.
- PortFast should never be enabled on ports connected to another switch.
- BPDU Guard automatically disables a PortFast port if it receives a BPDU.
- BPDU Guard protects the network from accidental switch connections.
- BPDU Filter prevents a port from sending or receiving BPDUs.
- BPDU Filter should be used carefully because it can disable STP protection.
- Root Guard prevents another switch from becoming the Root Bridge.
- If a superior BPDU is received on a Root Guard port, the port enters the Root-Inconsistent state.
- These features improve both network security and stability.

## Features

### PortFast
- Used on access ports.
- Immediately enters the Forwarding state.
- Reduces device startup time.

### BPDU Guard
- Protects PortFast ports.
- Err-disables the port if a BPDU is received.

### BPDU Filter
- Stops BPDU transmission and reception.
- Can cause Layer 2 loops if used incorrectly.

### Root Guard
- Prevents unauthorized switches from becoming the Root Bridge.
- Places the port into the Root-Inconsistent state when necessary.

## Root Bridge Configuration

### Commands Used

- `spanning-tree vlan <VLAN-ID> root primary`
- `spanning-tree vlan <VLAN-ID> root secondary`

### What I Learned

- `spanning-tree vlan 1 root primary` configures the switch as the preferred Root Bridge for VLAN 1.
- `spanning-tree vlan 1 root secondary` configures the switch as the backup Root Bridge.
- Cisco automatically adjusts the bridge priority when these commands are used.
- These commands are easier than manually configuring the bridge priority.

## Common Mistakes

- Enabling PortFast on trunk links or switch-to-switch links.
- Using BPDU Filter without understanding its risks.
- Forgetting to enable BPDU Guard on PortFast ports.
- Assuming Root Guard blocks all BPDUs (it only blocks superior BPDUs).

## Verification

- `show spanning-tree interface`
- `show spanning-tree summary`
- `show spanning-tree`
