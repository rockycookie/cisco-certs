# Dynamic ARP Inspection
For all ARP requests/responses on untrusted ports:
- drops packets with invalid IP-to-MAC address binding

## Enable
```
Device(config)# ip arp inspection vlan 1
```

## Trust a Port
By default, all interfaces are untrusted

```
Device(config-if)# [no] ip arp inspection trust
```
