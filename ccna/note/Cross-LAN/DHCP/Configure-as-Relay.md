# Configure DHCP Relay

## Pre-requisite 
- DHCP clients exist in the subnet
- DHCP server does not exit in the subnet

## Config

```
(config-if)# ip helper-address 172.16.2.11
```

It tells the router to 
- notice local subnet broadcasts (to 255.255.255.255) that use UDP
- change the source and destination IP address
- enabling DHCP servers to sit on a remote subnet

## Verify

```
R1# show ip interface g0/0

GigabitEthernet0/0 is up, line protocol is up
    Internet address is 172.16.1.1/24
    Broadcast address is 255.255.255.255
    Address determined by non-volatile memory
    MTU is 1500 bytes
Helper address is 172.16.2.11
...
```
