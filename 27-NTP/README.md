# Network Time Protocol (NTP)

## Objective

Understand how NTP synchronizes the time between network devices.

## Commands Used

```bash
ntp server <IP-address>
ntp master <stratum>
show clock
show ntp status
show ntp associations
show ntp servers
```

## What I Learned

* NTP (Network Time Protocol) synchronizes the time of network devices.
* Accurate time synchronization is important for logging, troubleshooting, and security.
* An NTP client synchronizes its clock with an NTP server.
* NTP uses **UDP port 123**.
* NTP uses **Stratum** values to indicate the distance from the reference clock.
* A lower stratum value indicates a clock closer to the original reference clock.
* **Stratum 0** represents the reference clock itself, such as an atomic clock or GPS source.
* An NTP server synchronized directly to a Stratum 0 source is **Stratum 1**.
* Each additional NTP level increases the stratum by 1.
* An NTP device configured as `ntp master` can act as an NTP server for other devices.

## Stratum

```text
Stratum 0 → Reference clock
     ↓
Stratum 1 → Directly connected to reference clock
     ↓
Stratum 2 → Synchronizes from Stratum 1
     ↓
Stratum 3 → Synchronizes from Stratum 2
```

* The NTP stratum value shown on a device represents its own stratum.
* A device synchronizing from an NTP server generally has a stratum **one higher** than that server.

## NTP Server Configuration

```bash
ntp server 192.168.1.1
```

This configures the device to synchronize its time with the specified NTP server.

## NTP Master

```bash
ntp master 3
```

This configures the router to act as an NTP master with the specified stratum.

## Verification

```bash
show clock
show ntp status
show ntp associations
show ntp servers
```

## Important Information

* NTP uses UDP port `123`.
* Lower stratum is preferred.
* NTP is used to keep device clocks synchronized.
* `show ntp status` can be used to check synchronization status and stratum.

