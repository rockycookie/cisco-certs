# Device Time

## Configure Manually
```
R1# configure terminal
R1(config)# clock timezone AnyName -5
R1(config)# clock summer-time EDT recurring
```

## Network Time Protocol

### NTP Server Mode
```
ntp master {stratum-level}
```
- The device acts only as an NTP server, never client
- The device gets its time information from the internal clock on itself

### NTP Client/Server Mode
```
ntp server {address | hostname}
```
- acts as both a server and a client
    - First, it acts as an NTP client, to synchronize time with a server. Once synchronized, the device can then act as an NTP server, to supply time to other NTP clients
