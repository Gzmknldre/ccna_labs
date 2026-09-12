# 38 - DHCP Spoofing

## 🔹 What is DHCP Spoofing?

**DHCP Spoofing** is a Layer 2 attack where an unauthorized DHCP server responds to DHCP requests from clients.

The attacker can provide malicious network configuration such as:
- IP address
- Default gateway
- DNS server

This can redirect client traffic through the attacker's device.

---

## 🔹 DHCP Snooping

**DHCP Snooping** is a switch security feature used to protect the network against unauthorized DHCP servers.

The switch classifies ports as:

- **Trusted** → DHCP server/uplink side
- **Untrusted** → Client-facing ports

DHCP server messages are only allowed through **trusted ports**.

If a DHCP server response arrives on an **untrusted port**, the switch drops it.

---

## 🔹 DHCP Snooping Configuration

Enable DHCP Snooping globally:

    ip dhcp snooping

Enable it for a VLAN:

    ip dhcp snooping vlan 10

Configure the interface connected to the legitimate DHCP server as trusted:

    interface g0/1
    ip dhcp snooping trust

Client-facing ports remain **untrusted** by default.

---

## 🔹 Verification

Check DHCP Snooping status:

    show ip dhcp snooping

Check the DHCP Snooping binding table:

    show ip dhcp snooping binding

The binding table contains information such as:

- Client MAC address
- Client IP address
- VLAN
- Interface
- Lease information

---

## 🧠 Key Points

    DHCP Spoofing → Unauthorized DHCP server attack

    DHCP Snooping → Protects against unauthorized DHCP servers

    Trusted port   → Legitimate DHCP server/uplink
    Untrusted port → Client-facing port

    DHCP server responses from an untrusted port → Dropped

    ip dhcp snooping
    ip dhcp snooping vlan <VLAN>
    ip dhcp snooping trust

---

## 📌 Important Commands

    ip dhcp snooping
    ip dhcp snooping vlan <VLAN>

    interface <interface>
    ip dhcp snooping trust

    show ip dhcp snooping
    show ip dhcp snooping binding
