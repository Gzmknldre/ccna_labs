# FTP and TFTP

## Objective

Understand how FTP and TFTP are used to transfer files between network devices and servers.

## What I Learned

- **FTP (File Transfer Protocol)** is used to transfer files between a client and server.
- FTP provides authentication using a username and password.
- FTP uses **TCP** and provides reliable file transfer.
- FTP uses **TCP port 20-21** for control connections.
- **TFTP (Trivial File Transfer Protocol)** is a simpler file transfer protocol.
- TFTP does not use authentication.
- TFTP uses **UDP port 69**.
- TFTP is commonly used to transfer Cisco configuration files and IOS images.
- TFTP is simpler and less secure than FTP.

## FTP vs TFTP

| FTP | TFTP |
|---|---|
| TCP | UDP |
| Port 20-21 | Port 69 |
| Username/password | No authentication |
| More secure | Less secure |
| More features | Simple file transfer |
| Reliable TCP transfer | Lightweight UDP transfer |

## Common Cisco Commands

### Copy Configuration to TFTP Server

```bash
copy running-config tftp:
```

```bash
copy startup-config tftp:
```

### Copy Configuration from TFTP Server

```bash
copy tftp: running-config
```

```bash
copy tftp: startup-config
```

### Copy IOS Image

```bash
copy flash: tftp:
```

```bash
copy tftp: flash:
```

## FTP

Cisco devices can also use FTP to transfer files.

```bash
copy ftp: flash:
```

```bash
copy flash: ftp:
```

## Important Files

### Running Configuration

```text
running-config
```

- Current configuration stored in RAM.
- Lost after reboot if it has not been saved.

### Startup Configuration

```text
startup-config
```

- Saved configuration stored in NVRAM.
- Used when the device boots.

### IOS Image

```text
flash:
```

- Cisco IOS image is normally stored in flash memory.

## Common Mistakes

- Confusing FTP's TCP port 21 with TFTP's UDP port 69.
- Forgetting that TFTP does not use authentication.
- Confusing `running-config` with `startup-config`.
- Forgetting that `running-config` is stored in RAM.
- Forgetting to specify the correct source and destination when using `copy`.

## Key Points

```text
FTP  → TCP 20-21 → Authentication → Reliable
TFTP → UDP 69 → No Authentication → Simple
```
