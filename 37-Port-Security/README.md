# 37 - Port Security

## 🔹 What is Port Security?

**Port Security** is a Layer 2 security feature that controls which devices are allowed to connect to a switch port.

It uses **MAC addresses** to restrict unauthorized devices from accessing the network.

---

## 🔹 Basic Configuration

Port Security is configured on an access port.

    interface g0/1
    switchport mode access
    switchport port-security

Set the maximum number of secure MAC addresses:

    switchport port-security maximum 1

The default maximum number of secure MAC addresses is **1**.

---

## 🔹 Static Secure MAC Address

A MAC address can be manually configured as a secure MAC address.

    switchport port-security mac-address 0011.2233.4455

---

## 🔹 Sticky MAC Address

**Sticky MAC** allows the switch to dynamically learn a MAC address and add it to the running configuration.

    switchport port-security mac-address sticky

Example:

    interface g0/1
    switchport mode access
    switchport port-security
    switchport port-security maximum 1
    switchport port-security mac-address sticky

To save the learned sticky MAC address permanently:

    copy running-config startup-config

---

## 🔹 Port Security Violation Modes

A **violation** occurs when an unauthorized MAC address is detected on a port.

### Protect

    switchport port-security violation protect

- Drops frames from unauthorized MAC addresses
- Port remains up
- No violation notification

### Restrict

    switchport port-security violation restrict

- Drops frames from unauthorized MAC addresses
- Port remains up
- Increments the violation counter
- Generates notifications/logging

### Shutdown

    switchport port-security violation shutdown

- Drops unauthorized traffic
- Port is placed into **err-disabled** state
- Generates notifications/logging
- **Default violation mode**

---

## 🔹 Violation Mode Comparison

| Mode | Unauthorized Traffic | Port State | Violation Counter |
|---|---|---|---|
| **Protect** | Dropped | Up | No |
| **Restrict** | Dropped | Up | Yes |
| **Shutdown** | Dropped | Err-disabled | Yes |

---

## 🔹 Verification

Check Port Security status and secure MAC addresses:

    show port-security
    show port-security interface g0/1
    show port-security address

These commands can show:
- Port security status
- Maximum allowed MAC addresses
- Secure MAC addresses
- Security violations
- Violation mode

---

## 🧠 Key Points

    Port Security → Controls MAC addresses on switch ports
    Maximum → Limits the number of secure MAC addresses
    Static MAC → Manually configured secure MAC address
    Sticky MAC → Dynamically learns and stores MAC addresses

    Protect  → Drops unauthorized traffic, port stays up
    Restrict  → Drops + counts/logs violations, port stays up
    Shutdown  → Drops + puts port into err-disabled state

    Default violation mode → Shutdown

---

## 📌 Important Commands

    switchport mode access
    switchport port-security
    switchport port-security maximum 1
    switchport port-security mac-address <MAC>
    switchport port-security mac-address sticky

    switchport port-security violation protect
    switchport port-security violation restrict
    switchport port-security violation shutdown

    show port-security
    show port-security interface g0/1
    show port-security address
