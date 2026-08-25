# Standard ACL

## Objective

Configure Standard Access Control Lists (ACLs) to control traffic based on the source IPv4 address.

## Commands Used

- `access-list <number> permit <source>`
- `access-list <number> deny <source>`
- `access-list <number> deny any`
- `access-list <number> permit any`
- `ip access-group <ACL-number> in`
- `ip access-group <ACL-number> out`
- `show access-lists`
- `show ip interface`

## What I Learned

- Standard ACLs filter traffic based only on the source IPv4 address.
- Standard ACLs use ACL numbers from `1–99` and `1300–1999`.
- ACL entries are processed from top to bottom.
- The first matching entry is applied.
- There is an implicit `deny any` at the end of every ACL.
- If traffic does not match any configured entry, it is denied.
- ACLs can be applied inbound or outbound on an interface.
- Standard ACLs should generally be placed as close to the destination as possible.
- The ACL does not filter traffic until it is applied to an interface using `ip access-group`.

## Example

```bash
access-list 10 deny 192.168.1.10
access-list 10 permit any

interface g0/0
ip access-group 10 out
