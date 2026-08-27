# Extended ACL

## Objective

Configure Extended Access Control Lists (ACLs) to control IPv4 traffic based on source, destination, protocol, and port number.

## Commands Used

```bash
access-list <number> permit <protocol> <source> <destination>
access-list <number> deny <protocol> <source> <destination>

ip access-group <ACL-number> in
ip access-group <ACL-number> out

show access-lists
show ip interface
```

## What I Learned

* Extended ACLs provide more precise traffic filtering than Standard ACLs.
* Extended ACLs can filter traffic based on:

  * Source IP address
  * Destination IP address
  * Protocol
  * Source port
  * Destination port
* Extended ACL numbers are:

  * `100–199`
  * `2000–2699`
* ACL entries are processed from top to bottom.
* The first matching statement is applied.
* Every ACL has an implicit `deny any` at the end.
* An ACL must be applied to an interface before it can filter traffic.
* ACLs can be applied inbound or outbound.

## Basic Example

```bash
access-list 100 deny tcp host 192.168.1.10 host 192.168.2.10 eq 80
access-list 100 permit ip any any

interface g0/0
ip access-group 100 in
```

This blocks HTTP traffic from `192.168.1.10` to `192.168.2.10` while allowing other IP traffic.

## Protocols

Common protocols used with Extended ACLs:

```text
ip
tcp
udp
icmp
```

## Ports

Extended ACLs can filter specific TCP/UDP ports.

Common examples:

```text
HTTP  → 80
HTTPS → 443
DNS   → 53
SSH   → 22
Telnet → 23
FTP   → 21
```

Example:

```bash
access-list 100 deny tcp any any eq 80
```

This denies HTTP traffic.

## Standard vs Extended ACL

| Standard ACL         | Extended ACL                            |
| -------------------- | --------------------------------------- |
| Source IP only       | Source + Destination + Protocol + Ports |
| Less specific        | More specific                           |
| `1–99`, `1300–1999`  | `100–199`, `2000–2699`                  |
| Close to destination | Close to source                         |

## Inbound vs Outbound

### Inbound

```bash
ip access-group 100 in
```

Checks packets as they enter the interface.

### Outbound

```bash
ip access-group 100 out
```

Checks packets as they leave the interface.

## Common Mistakes

* Forgetting the implicit `deny any`.
* Putting `permit ip any any` before a specific deny statement.
* Applying the ACL in the wrong direction.
* Using the wrong source or destination.
* Using the wrong protocol or port.
* Placing Extended ACLs too far from the source.
* Forgetting to apply the ACL to the interface.

## Verification

```bash
show access-lists
show ip interface
```

