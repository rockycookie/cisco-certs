# DHCP Snooping
To prevent fake DHCP server and more

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
