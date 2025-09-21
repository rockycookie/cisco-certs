# NTP
- using port 123

## Network Time Protocol
- stratum level
    - a number to show the accuracy of their reference clock data
    - 1 to 15, default 8
    - the lower, the more accurate
    - each client adds 1 to the stratum value learned from its server

### Show
```
Switch# show ntp ?
  associations  NTP associations
  status        NTP status

Switch# show ntp associations
! This output is taken from router R1, acting in client/server mode
    address     ref clock   st  when    poll    reach   delay   offset  disp
*~172.16.2.2    172.16.3.3  3   50      64      377     1.223   0.090   4.469
    * sys.peer, # selected, + candidate, - outlyer, x falseticker, ~ configured
```

### NTP Server Mode
```
Switch(config)# ntp master {stratum-level}
```
- The device acts only as an NTP server, never client
- The device gets its time information from the internal clock on itself
- stratum level
    - 0: most accurate
    - 7: default
    - 15: least accurate, 15 hops away from the source of truth

### NTP Client/Server Mode
```
Switch(config)# ntp server {address | hostname}
```
- acts as both a server and a client
    - First, it acts as an NTP client, to synchronize time with a server. Once synchronized, the device can then act as an NTP server, to supply time to other NTP clients
