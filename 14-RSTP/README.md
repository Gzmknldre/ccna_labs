# Rapid Spanning Tree Protocol (RSTP)

## Objective

Understand how Rapid Spanning Tree Protocol (RSTP) improves convergence time compared to STP.

## Commands Used

- `show spanning-tree`
- `show spanning-tree vlan`
- `show spanning-tree root`
- `spanning-tree mode rapid-pvst`

## What I Learned

- RSTP (Rapid Spanning Tree Protocol) is defined by IEEE 802.1w.
- RSTP provides much faster convergence than traditional STP.
- RSTP reduces network downtime after a topology change.
- Cisco implements RSTP as Rapid PVST+.
- RSTP keeps the Root Bridge election process used in STP.
- Root Ports and Designated Ports still exist in RSTP.
- Alternate Ports provide an immediate backup path if the Root Port fails.
- Backup Ports provide redundancy on shared network segments.
- RSTP combines the Blocking, Listening, and Disabled states into the Discarding state.
- Forwarding and Learning states are still used.
- RSTP uses proposal and agreement messages to speed up convergence.

## Port Roles

- Root Port (RP)
- Designated Port (DP)
- Alternate Port (AP)
- Backup Port (BP)

## Port States

- Discarding
- Learning
- Forwarding

## STP vs RSTP

| STP | RSTP |
|------|------|
| IEEE 802.1D | IEEE 802.1w |
| Slower convergence | Faster convergence |
| 5 port states | 3 port states |
| No Backup Port | Backup Port supported |
| Slower topology changes | Rapid topology changes |

## Verification

- `show spanning-tree`
- `show spanning-tree vlan`
- `show spanning-tree root`
