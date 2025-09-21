# Cisco Discovery Protocol

## enable
### `[no] cdp run`
- Global command that enables and disables

### `[no] cdp enable`
- Interface subcommand to enable and disable

### `cdp timer /seconds/`
- CDP send timer (the frequency at which CDP sends messages)

### `cdp holdtime /seconds/`
- timer to remove CFP info

## Show
### `show cdp`
```
SW2# show cdp
Global CDP information:
    Sending CDP packets every 60 seconds
    Sending a holdtime value of 180 seconds
    Sending CDPv2 advertisements is enabled
```

### `show cdp interface /interface/`
```
SW2# show cdp interface GigabitEthernet1/0/2
GigabitEthernet1/0/2 is up, line protocol is up
Encapsulation ARPA
Sending CDP packets every 60 seconds
Holdtime is 180 seconds
```

### `show cdp neighbors`
```
SW2# show cdp neighbors
Capability Codes:   R - Router, T - Trans Bridge, B - Source Route Bridge
                    S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone,
                    D - Remote, C - CVTA, M - Two-port Mac Relay
Device ID   Local Intrfce   Holdtme     Capability  Platform    Port ID
SW1         Gig 1/0/21      155         S I         WS-C2960X   Gig 1/0/24
R1          Gig 1/0/2       131         R S I       C1111-8P    Gig 0/0/1
Total cdp entries displayed : 2
```

### `show cdp neighbors detail`

```
SW2# show cdp neighbors detail
-------------------------
Device ID: SW1
Entry address(es):
    IP address: 1.1.1.1
Platform: cisco WS-C2960XR-24TS-I, Capabilities: Switch IGMP
Interface: GigabitEthernet1/0/21, Port ID (outgoing port): GigabitEthernet1/0/24
Holdtime : 144 sec

Version :
Cisco IOS Software, C2960X Software (C2960X-UNIVERSALK9-M), Version 15.2(6)E2, RELEASE
SOFTWARE (fc4)
Technical Support: http://www.cisco.com/techsupport
Copyright (c) 1986-2018 by Cisco Systems, Inc.
Compiled Thu 13-Sep-18 03:43 by prod_rel_team

advertisement version: 2
Protocol Hello: OUI=0x00000C, Protocol ID=0x0112; payload len=27, value=00000000FFFFFFFF01022501000000000000BCC4938BA180FF0000
VTP Management Domain: 'fred'
Native VLAN: 1
Duplex: full
Management address(es):
    IP address: 1.1.1.1
-------------------------
```