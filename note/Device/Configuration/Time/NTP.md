# Device Time
- using port 123

## Configure Manually
```
R1# configure terminal
R1(config)# clock timezone AnyName -5
R1(config)# clock summer-time EDT recurring
```

## Network Time Protocol
- stratum level
    - a number to show the accuracy of their reference clock data
    - 1 to 15, default 8
    - the lower, the more accurate
    - each client adds 1 to the stratum value learned from its server

### Show
```
R1# show ntp associations
! This output is taken from router R1, acting in client/server mode
    address     ref clock   st  when    poll    reach   delay   offset  disp
*~172.16.2.2    172.16.3.3  3   50      64      377     1.223   0.090   4.469
    * sys.peer, # selected, + candidate, - outlyer, x falseticker, ~ configured
```

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
