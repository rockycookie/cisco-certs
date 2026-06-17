# First Hop Redunadnt Protocol

- "First Hop" --> the default gateway

## HSRP (Hot Standby Router Protocol)
- Notes:
    - for 3-tier architecture, where to do the HSRP config depneds on where is the "First Hop" (it differs between using L2 vs L3 switches)
- commands:
    - `preempt`: Forces this router to immediately take back the Active role if its priority becomes higher than the current Active router
    - `priority 120`: election weight; default is 100
    - `standby 1 authentication md5 key-string MySecretHSRPKey123` MD5 authen

## VRRP (Virtual Router Redundancy Protocol)
- Notes:
    - VRRP has preemption enabled by default
        - to disable `no vrrp 20 preempt`
    - VRRP group number is the same as HSRP, range of the number is the only diff

## Commands
### Topology 1
- Physical Interfaces: GigabitEthernet0/1 on both devices
- Subnet: `10.1.1.0/24`
- Router 1 (Primary): Physical IP `10.1.1.2`
- Router 2 (Secondary): Physical IP `10.1.1.3`
- HSRP Virtual IP (Shared Gateway): `10.1.1.1`
- HSRP Group Number: 1

### Configuration 1
```
! sample on standalone physical interface, can also be done on sub-interface
Router1# configure terminal
Router1(config)# interface GigabitEthernet0/1
Router1(config-if)# description Link to Upstream Firewall/ISP
Router1(config-if)# ip address 10.1.1.2 255.255.255.0
Router1(config-if)# standby 1 ip 10.1.1.1
Router1(config-if)# standby 1 priority 120
Router1(config-if)# standby 1 preempt
Router1(config-if)# no shutdown

Router2# configure terminal
Router2(config)# interface GigabitEthernet0/1
Router2(config-if)# description Link to Upstream Firewall/ISP
Router2(config-if)# ip address 10.1.1.3 255.255.255.0
Router2(config-if)# standby 1 ip 10.1.1.1
Router2(config-if)# standby 1 preempt
Router2(config-if)# no shutdown

!---------------------------------------------!
! sample on sub-interface, can also be done on standalone physical interface

Router1(config)# interface GigabitEthernet0/0.20
Router1(config-subif)# description Default Gateway for VLAN 20
Router1(config-subif)# encapsulation dot1Q 20
Router1(config-subif)# ip address 192.168.20.2 255.255.255.0
Router1(config-subif)# vrrp 1 ip 192.168.20.1
Router1(config-subif)# vrrp 1 priority 120

Router2(config)# interface GigabitEthernet0/0.20
Router2(config-subif)# description Backup Gateway for VLAN 20
Router2(config-subif)# encapsulation dot1Q 20
Router2(config-subif)# ip address 192.168.20.3 255.255.255.0
Router2(config-subif)# vrrp 1 ip 192.168.20.1
```

### Topology 2
- VLAN Interface: VLAN 10
- Subnet: `192.168.10.0/24`
- Router 1 (Primary): Physical IP `192.168.10.2`
- Router 2 (Secondary): Physical IP `192.168.10.3`
- HSRP Virtual IP (Gateway): `192.168.10.1`
- HSRP Group Number: 10

### Configuration 2

```
Switch1# configure terminal
Switch1(config)# interface vlan 10
Switch1(config-if)# ip address 192.168.10.2 255.255.255.0
Switch1(config-if)# standby 10 ip 192.168.10.1
Switch1(config-if)# standby 10 priority 110
Switch1(config-if)# standby 10 preempt
Switch1(config-if)# no shutdown

Switch2# configure terminal
Switch2(config)# interface vlan 10
Switch2(config-if)# ip address 192.168.10.3 255.255.255.0
Switch2(config-if)# standby 10 ip 192.168.10.1
Switch2(config-if)# standby 10 preempt
Switch2(config-if)# no shutdown

!---------------------------------------------!

Switch1(config)# interface vlan 20
Switch1(config-if)# ip address 192.168.20.2 255.255.255.0
Switch1(config-if)# vrrp 20 ip 192.168.20.1
Switch1(config-if)# vrrp 20 priority 120
Switch1(config-if)# no shutdown

Switch2(config)# interface vlan 20
Switch2(config-if)# ip address 192.168.20.3 255.255.255.0
Switch2(config-if)# vrrp 20 ip 192.168.20.1
Switch2(config-if)# no shutdown
```
- You must configure the physical interfaces connecting Switch 1 and Switch 2 as an 802.1Q Trunk line that allows VLAN 20

