# First Hop Redundancy Protocols (FHRP)

## Objective

Understand how FHRP provides default gateway redundancy and improves network availability.

## Protocols

- HSRP (Hot Standby Router Protocol)
- VRRP (Virtual Router Redundancy Protocol)
- GLBP (Gateway Load Balancing Protocol)

## Commands Used

- `standby <group> ip <virtual-ip>`
- `standby <group> priority <value>`
- `standby <group> preempt`
- `show standby`
- `vrrp <group> ip <virtual-ip>`
- `vrrp <group> priority <value>`
- `show vrrp`
- `glbp <group> ip <virtual-ip>`
- `glbp <group> priority <value>`
- `show glbp`

## What I Learned

- FHRP provides redundancy for the default gateway.
- Hosts use a virtual IP address as their default gateway instead of depending on a single physical router.
- If the active/primary router fails, another router can take over the gateway function.
- HSRP is a Cisco proprietary FHRP.
- VRRP is an open-standard FHRP.
- GLBP is a Cisco proprietary FHRP that also provides load balancing.
- HSRP uses Active and Standby routers.
- The virtual IP address is shared between the participating routers.
- HSRP priority can be changed to influence which router becomes Active.
- `preempt` allows a higher-priority router to take back the Active role when it becomes available.
- GLBP can distribute traffic across multiple gateway routers.

## HSRP

- Active router forwards traffic.
- Standby router provides redundancy.
- Higher HSRP priority is preferred.
- `preempt` allows the higher-priority router to become Active again.

## VRRP

- VRRP provides first-hop redundancy using an open standard.
- A Master router forwards traffic.
- A Backup router provides redundancy.
- Priority is used during the election.

## GLBP

- GLBP provides gateway redundancy and load balancing.
- Multiple routers can actively forward traffic.
- This allows the available gateway resources to be used simultaneously.

## Verification

- `show standby`
- `show vrrp`
- `show glbp`
