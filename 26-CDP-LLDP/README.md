# CDP and LLDP

## Objective

Understand how CDP and LLDP discover information about directly connected network devices.

## Commands Used

```bash
show cdp neighbors
show cdp neighbors detail
show cdp interface

cdp run
no cdp enable

show lldp neighbors
show lldp neighbors detail

lldp run
lldp transmit
lldp receive
```

## What I Learned

* **CDP (Cisco Discovery Protocol)** is a Cisco proprietary Layer 2 discovery protocol.
* CDP discovers information about directly connected Cisco devices.
* CDP is enabled by default on many Cisco devices.
* CDP can be disabled globally or on individual interfaces.
* **LLDP (Link Layer Discovery Protocol)** is an open-standard Layer 2 discovery protocol.
* LLDP can discover information from devices from different vendors.
* LLDP must be enabled before LLDP information can be exchanged.
* Both protocols provide information about directly connected neighbors.
* CDP and LLDP do not discover devices several hops away; they operate with directly connected neighbors.

## CDP vs LLDP

| CDP                  | LLDP                  |
| -------------------- | --------------------- |
| Cisco proprietary    | Open standard         |
| Mainly Cisco devices | Multi-vendor          |
| Layer 2 discovery    | Layer 2 discovery     |
| `show cdp neighbors` | `show lldp neighbors` |
| `cdp run`            | `lldp run`            |

## CDP Information

`show cdp neighbors` can show:

* Device ID
* Local Interface
* Holdtime
* Capability
* Platform
* Port ID

`show cdp neighbors detail` provides more detailed information such as:

* IP address
* Device ID
* Platform
* Software version
* Local interface
* Remote port

## LLDP Information

`show lldp neighbors` can show:

* Device ID
* Local Interface
* Holdtime
* Capability
* Port ID

`show lldp neighbors detail` provides detailed neighbor information.

## Advertisement & Holdtime

| Protocol | Advertisement Timer | Holdtime |
|----------|--------------------|----------|
| CDP | 60 seconds | 180 seconds |
| LLDP | 30 seconds | 120 seconds |

- CDP sends advertisements every 60 seconds.
- CDP keeps neighbor information for 180 seconds if no new advertisement is received.
- LLDP sends advertisements every 30 seconds.
- LLDP keeps neighbor information for 120 seconds if no new advertisement is received.
- If the holdtime expires, the neighbor entry is removed from the neighbor table.

## Common Mistakes

* Confusing CDP with a routing protocol.
* Assuming CDP/LLDP discovers remote devices across multiple hops.
* Forgetting that CDP is Cisco proprietary.
* Forgetting that LLDP is vendor-neutral.
* Using CDP commands to verify LLDP neighbors or vice versa.

## Verification

```bash
show cdp neighbors
show cdp neighbors detail
show cdp interface

show lldp neighbors
show lldp neighbors detail
```

