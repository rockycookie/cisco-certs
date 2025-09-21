# L3 Switch Routing


## Concepts

### Routed Interface -- work the same as a router
- A physical interface
- L3
- Can NOT support L2 features like STP
- The other option
    - by default
    - switched interface
    - L2

### VLAN Interface -- inter-VLAN routing
- also called, switch virtual interface (SVI)
- connects a VLAN to the Layer 3 router engine

## Config
- `switch(config)# ip routing` enables routing, otherwise route table stays empty

### Config a routed interface
```
switch# configure terminal
switch(config)# interface ethernet 2/1
switch(config-if)# no shutdown
switch(config-if)# no switchport
switch(config-if)# ip address 192.0.2.1/8
switch(config-if)# copy running-config startup-config
```
Notes:
- `switch(conifg-if)# no switchport` makes it a L3 routed interface, which also deletes any configuration specific to Layer 2 on this interface

### Config a VLAN interface
```
switch# configure terminal
switch(config)# feature interface-vlan
switch(config)# interface vlan 10
switch(config-if)# no shutdown
switch(config-if)# ip address 192.0.2.1/8
switch(config-if)# copy running-config startup-config
```
Notes:
- VLAN interface number is mapped to the VLAN number
- `feature interface-vlan` enables VLAN interface mode
- VLAN number limit [1, 4094]

### Verification
```
Router# show ip route

Router# show ip interface brief

Router# show protocols
```

## Ref
- https://www.cisco.com/c/en/us/td/docs/switches/datacenter/nexus5000/sw/interfaces/521_N11/b_5k_Interfaces_Config_Guide_Release_521N11/b_5k_Interfaces_Config_Guide_Release_521N11_chapter_011.pdf
