# OSPFv2

## Enable
```
Router(config)#router ospf 119
Router(config-router)# router-id 119.0.0.0
```

## Advertise which networks
```
Router(config-router)# network 192.168.0.0 0.0.0.255 area 19


Router(config-router)#do sh ip protocol

Routing Protocol is "ospf 119"
  Outgoing update filter list for all interfaces is not set 
  Incoming update filter list for all interfaces is not set 
  Router ID 119.0.0.0
  Number of areas in this router is 1. 1 normal 0 stub 0 nssa
  Maximum path: 4
  Routing for Networks:
    192.168.0.0 0.0.0.255 area 19
  Routing Information Sources:  
    Gateway         Distance      Last Update 
    119.0.0.0            110      00:00:17
  Distance: (default is 110)
```

## Enable an Interface to participate OSPF
```
R0(config-if)#ip ospf 119 area 19

00:44:21: %OSPF-5-ADJCHG: Process 119, Nbr 119.0.0.1 on GigabitEthernet0/1 from LOADING to FULL, Loading Done

R0(config-if)#do sh ip ospf nei
Neighbor ID     Pri   State           Dead Time   Address         Interface
119.0.0.1         1   FULL/DR         00:00:38    172.16.0.2      GigabitEthernet0/1
```

## Per Interface Config

```
Router(config-if)#ip ospf ?
  <1-65535>           Process ID
  authentication      Enable authentication
  authentication-key  Authentication password (key)
  cost                Interface cost
  dead-interval       Interval after which a neighbor is declared dead
  hello-interval      Time between HELLO packets
  message-digest-key  Message digest authentication password (key)
  network             Network type (point-to-point or not)
  priority            Router priority
```
