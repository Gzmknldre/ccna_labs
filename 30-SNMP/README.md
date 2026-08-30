# SNMP

## Objective

Understand how SNMP is used to monitor and manage network devices.

## What I Learned

- SNMP (Simple Network Management Protocol) is used to monitor and manage network devices.
- SNMP allows a network management system (NMS) to collect information from network devices.
- The monitored device is called an **SNMP agent**.
- The management system is called an **SNMP manager**.
- SNMP uses **UDP**.
- SNMP uses UDP port **161** for queries.
- SNMP uses UDP port **162** for traps.

## SNMP Components

### SNMP Manager

- Central system used to monitor network devices.
- Requests information from SNMP agents.

### SNMP Agent

- Runs on the network device.
- Collects information about the device.
- Responds to requests from the SNMP manager.
- Can send notifications called traps.

### MIB

- **Management Information Base (MIB)** contains information about the objects that can be monitored.
- Each monitored object is identified using an **OID (Object Identifier)**.

## SNMP Operations


### GET

The SNMP manager requests information from the SNMP agent.

### GETNEXT

The manager requests the next object in the MIB.

### SET

The SNMP manager changes a value on the SNMP agent.

### RESPONSE

The SNMP agent sends a response back to the SNMP manager after receiving a GET, GETNEXT, or SET request.

### TRAP

The SNMP agent sends an unsolicited notification to the SNMP manager when an event occurs.

### INFORM

Similar to a TRAP, but the SNMP manager sends an acknowledgment (response) to confirm that the notification was received.



## SNMP Versions

### SNMPv1

- Original SNMP version.
- Uses community strings for authentication.
- Provides limited security.

### SNMPv2c

- Improved performance compared to SNMPv1.
- Uses community strings.
- Still does not provide strong security.

### SNMPv3

- Provides stronger security.
- Supports authentication and encryption.

## Ports

```text
UDP 161 → SNMP queries
UDP 162 → SNMP traps
```

## Common Mistakes

- Confusing SNMP with a routing protocol.
- Confusing the SNMP manager with the SNMP agent.
- Mixing up UDP ports 161 and 162.
- Confusing a TRAP with a normal SNMP request.
- Assuming SNMP is only used for configuration; it is primarily used for monitoring and management.

## Key Points

```text
NMS / Manager
      ↓
   SNMP
      ↓
SNMP Agent
      ↓
Network Device
```

- **Manager → Agent:** GET / SET
- **Agent → Manager:** TRAP
- **UDP 161:** Queries
- **UDP 162:** Traps
