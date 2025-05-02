# EtherChannel
```
2.4 Configure and verify (Layer 2/Layer 3) EtherChannel (LACP)
```

## Why
- load balance routes instead of STP block

## What

### How it looks
```
# show etherchannel 1 summary

Number of channel-groups in use: 1
Number of aggregators: 1
Group  Port-channel  Protocol    Ports
------+-------------+-----------+-----------------------------------------------
1      Po1(SU)       -           Fa0/14(P) Fa0/15(P)
```

### When adding port to gourp
The new physical interface’s settings must be the same as the existing ports’ settings;
otherwise physical interface remains configured as part of the PortChannel,
but it is not used as part of the channel, often being placed into some nonworking state.
- Speed
- Duplex
- STP interface setting
- Operational access or trunking state (all must be access, or all must be trunks)
    - If an access port, the access VLAN
    - If a trunk port, the allowed VLAN list
    - If a trunk port, the native VLAN

### Load distribution
Goals:
- same-application messages use the same link --> ensure in-the-same-order
- use all the active links in, adjusting to link addition/removal
- balance the traffic across those active links
- be quick

Steps:
1. conf t
2. port-channel load-balance {**src-mac** | **dst-mac** | **src-dst-mac**}

```
SW1# show etherchannel load-balance
EtherChannel Load-Balancing Configuration:
        src-mac
EtherChannel Load-Balancing Addresses Used Per-Protocol:
    Non-IP: Source MAC address
    IPv4: Source MAC address
    IPv6: Source MAC address

SW1# test etherchannel load-balance interface po1 mac 0200.0000.0001 0200.1111.1111
Would select Gi1/0/22 of Po1
SW1# test etherchannel load-balance interface po1 mac 0200.0000.0001 0200.1111.1112
Would select Gi1/0/22 of Po1
SW1# test etherchannel load-balance interface po1 mac 0200.0000.0001 0200.1111.1113
Would select Gi1/0/22 of Po1
```

## How

### Layer 2, manual
1. conf t
2. int {int name}
3. channel-group {num} mode on
    - `num` could be different in different switches

### Layer 2, dynamic LACP
1. conf t
2. int {int name}
3. channel-group {num} mode {**active** | **passive**}
    - `num` could be different in different switches

### Layer 2, dynamic PAgP
1. conf t
2. int {int name}
3. channel-group {num} mode {**desirable** | **auto**}
    - `num` could be different in different switches
