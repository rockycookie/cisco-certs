# Commands

## Initialize the BGP routing process
```
router bgp <as-number>
```

## Define BGP router ID
```
bgp router-id <router-id>
```
- when not defined
    1. the highest IP address of any up loopback interfaces
    2. the highest IP address of any active up interfaces
- When the router ID changes, all BGP sessions reset and need to be reestablished

## Define BGP Peer Router
```
neighbor <ip-address> remote-as <as-number>
```
- `<ip-address>`: IP of the Peer's interface in the network that connects the routers
- `<as-number>`: AS number of the neighbor

## Address family
```
address-family afi safi
```

## Activate
```
neighbor <ip-address> activate
```
- `<ip-address>`: Peer's interface IP

## Verification
```
show bgp afi safi summary
```
e.g.
```
R1# show bgp ipv4 unicast summary
BGP router identifier 192.168.1.1, local AS number 65100
BGP table version is 1, main routing table version 1

Neighbor    V   AS      MsgRcvd     MsgSent TblVer InQ OutQ     Up/Down     State/PfxRcd
10.12.1.2   4   65200   8           9       1      0   0        00:05:23    0
```

## Route Advertisement
- BGP network statements identify specific network prefixes to be installed 
    - from routing table
    - into the BGP table --> **Loc-RIB**
- before advertising a Loc-RIB entry to the peer
    1. check NLRI is valid and next-hop address is resolvable in RIB
    2. check outbound neighbor route policies
```
network <network> mask <subnet-mask> [route-map <name>]
```