# Dynamic ARP Inspection

Check if the incoming ARP message is an attack, on untrusted ports

## How to configure
1. `ip arp inspection vlan <vlan-list>` global cmd
2. configure DHCP Snooping and/or ARP ACLs for use by DAI
3. `ip arp inspection trust` interface subcmd

## Gratuitous ARP
- It is an ARP reply
- It is sent without having first received an ARP request
- It is sent to an Ethernet destination broadcast address

## The Inspection

- It reuses DHCP Snooping binding table
- It discards:
    -  Messages with an **Ethernet header source MAC address** that is not equal to the ARP origin hardware (MAC) address
    - ARP reply messages with an **Ethernet header destination MAC address** that is not equal to the ARP target hardware (MAC) address
    - Messages with unexpected IP addresses in the two ARP IP address fields

```
SW2(config)# show ip arp inspection interfaces
Interface       Trust State     Rate (pps)  Burst Interval
--------------- -----------     ----------  --------------
Gi1/0/1         Untrusted       15          1
Gi1/0/2         Trusted         8           1
Gi1/0/3         Untrusted       8           4
Gi1/0/4         Untrusted       15          1
! Lines omitted for brevity
```