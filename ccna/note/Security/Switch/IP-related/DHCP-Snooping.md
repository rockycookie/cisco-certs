# DHCP Snooping
To prevent fake DHCP server and maliciously-IP-releasing

## How the switch does it?

1. examine all incoming DHCP messages, jump to step 4 if incoming interface is trusted
2. discard DHCP server messages
3. for DHCP client messages, discard if mismatch
    1. (DISCOVER, REQUEST) Compare MAC address between **Ethernet header** and **DHCP message**
    2. (RELEASE, DECLINE) Compare between (incoming **interface and IP address**) and **DHCP snooping binding table**
4. otherwise, update accordingly the DHCP Snooping binding table

## How to configure the switch:

1. `ip dhcp snooping` global command
2. `ip dhcp snooping vlan <vlan-list>` global command
3. `no ip dhcp snooping information option` global command if the switch is not acting as a L3 DHCP relay agent
4. `ip dhcp snooping trust` interface command
5. rate limmiting
    - `(no) ip dhcp snooping limit rate <number msg/sec>`
6. error recovery, global command
    - `errdisable recovery cause dhcp-rate-limit`
    - `errdisable recovery interval <seconds>`

## DHCP Snooping Binding Database/Table
```
switch(config)# show ip dhcp snooping binding
MacAddress          IpAddress       Lease(sec)  Type            VLAN    Interface
-----------------   -------------   ----------  -------------   ----    --------------------
02:00:11:11:11:11   172.16.2.101    86110       dhcp-snooping   11      GigabitEthernet1/0/3
02:00:22:22:22:22   172.16.2.102    86399       dhcp-snooping   11      GigabitEthernet1/0/4
Total number of bindings: 2
```
