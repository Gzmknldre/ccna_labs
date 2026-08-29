# DNS

## Objective

Understand how DNS resolves domain names to IP addresses and how DNS queries work.

## Commands Used

```bash
ip name-server <IP-address>
ip host <hostname> <IP-address>
show hosts
nslookup
ping <hostname>
show running-config
show ip dns view
show ip dns statistics
show ip dns database
```
## Windows DNS Commands

```cmd
ipconfig /displaydns
ipconfig /flushdns


## What I Learned

- DNS (Domain Name System) translates domain names into IP addresses.
- DNS uses a hierarchical naming system.
- DNS primarily uses **UDP port 53**.
- DNS can also use **TCP port 53** when required.
- DNS servers can cache DNS information to reduce lookup time.
- A DNS client can be configured with a DNS server to perform name resolution.

## DNS Records

| Record | Purpose |
|---|---|
| A | Maps a hostname to an IPv4 address |
| AAAA | Maps a hostname to an IPv6 address |
| CNAME | Alias for another hostname |
| MX | Specifies mail servers |
| NS | Specifies name servers |
| PTR | Reverse DNS lookup |



## Cisco DNS Configuration

```bash
ip name-server 8.8.8.8
```
Configures a DNS server that the device can use for name resolution.

## Verification

```bash
show hosts
nslookup
ping <hostname>
```

## Common Mistakes

- Confusing A and AAAA records.
- Forgetting that DNS primarily uses UDP port 53.
- Confusing DNS with a routing protocol.
- Forgetting to configure a DNS server when name resolution is required.
