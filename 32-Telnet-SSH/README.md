# SSH and Telnet

## Objective

Understand remote access to Cisco devices using Telnet and SSH, and configure both methods.

## Telnet

- Telnet provides remote CLI access to a network device.
- Telnet sends data, including credentials, in **plain text**.
- It is therefore considered insecure.
- Telnet uses **TCP port 23**.

### Telnet Configuration

```bash
enable
configure terminal

line vty 0 4
password cisco
login
transport input telnet
```

## SSH

- SSH provides secure remote CLI access to a network device.
- SSH encrypts the communication between the client and the device.
- SSH uses **TCP port 22**.
- SSH requires a hostname and domain name for RSA key generation.
- A local username and password can be used for authentication.

### SSH Configuration

```bash
enable
configure terminal

hostname R1
ip domain-name example.com

username admin secret cisco123

crypto key generate rsa
```

Set the VTY lines to use SSH:

```bash
line vty 0 4
login local
transport input ssh
```

## SSH + Telnet Configuration

Both protocols can be allowed:

```bash
line vty 0 4
login local
transport input telnet ssh
```

Only SSH:

```bash
line vty 0 4
login local
transport input ssh
```

## Restrict VTY Access with Standard ACL

First, create a Standard ACL to permit the source network/host:

```bash
access-list 1 permit <source-network> <wildcard-mask>

## SSH Version

```bash
ip ssh version 2
```

- SSH version 2 provides improved security compared to SSH version 1.

  
```bash
access-list 1 permit 192.168.1.0 0.0.0.255

line vty 0 4
access-class 1 in
login local


## Verification

```bash
show ip ssh
show users
show running-config
```

Test remote access:

```bash
ssh -l admin <IP-address>
telnet <IP-address>
```

## Telnet vs SSH

| Telnet | SSH |
|---|---|
| TCP 23 | TCP 22 |
| Plain text | Encrypted |
| Insecure | Secure |
| Remote CLI access | Secure remote CLI access |

## Common Mistakes

- Forgetting to configure `hostname` and `ip domain-name` before generating RSA keys.
- Forgetting to create a local username for `login local`.
- Forgetting `transport input ssh`.
- Using `login` when local username authentication with `login local` is intended.
- Forgetting to generate RSA keys.
- Using Telnet when a secure SSH connection should be used.
