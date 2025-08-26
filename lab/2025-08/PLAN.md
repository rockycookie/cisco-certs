# PacketTracer Lab Planning

For the topics without pluralsight tutorials, search it online like `ccna packet tracer cdp`

- https://app.pluralsight.com/library/courses/building-packet-tracer-labs-ccna-study-fundamentals/table-of-contents
- https://app.pluralsight.com/library/courses/ccna-study-building-packet-tracer-labs-network-protocol/table-of-contents

## Topics
### Configure and verify:
- Fundamentals
    - IPv4 addressing and subnetting    ---> [pluralsight: ARP table]
    - IPv6 addressing and prefix
- Access
    - VLANs spanning multiple switches    ---> [pluralsight: 3 switch network]
        - Access ports (data and voice)
        - Default VLAN
        - InterVLAN connectivity    ---> [pluralsight: InterVLAN routing]
    - Trunk    ---> [pluralsight: InterVLAN routing challenge]
        - Trunk ports
        - 802.1Q
        - Native VLAN
    - Layer 2 discovery protocols
        - Cisco Discovery Protocol (CDP)
        - LLDP
    - EtherChannel (LACP)
        - Layer 2    ---> [pluralsight: build etherchannel lab]
        - Layer 3    ---> [pluralsight: convert to L3 etherchannel]
- IP Connectivity
    - IPv4 and IPv6 static routing    ---> [pluralsight: 2/3/4 routers static exercise] [pluralsight: L3 switch static routing]
        - Default route
        - Network route
        - Host route
        - Floating static
    - single area OSPFv2    ---> [pluralsight: Dynamic Routing Lab: OSPF] [pluralsight: OSPF challenge]
        - Neighbor adjacencies
        - Point-to-point
        - Broadcast (DR/BDR selection)
        - Router ID
- IP Services
    - inside source NAT    ---> [pluralsight: build NAT labs]
        - static
        - pools
    - NTP
        - client mode
        - server mode
    - DHCP
        - client
        - relay
    - SSH
- Security
    - device access control using local passwords
    - ACL    ---> [pluralsight: build ACL labs]
    - Layer 2 security features
        - DHCP snooping
        - dynamic ARP inspection
        - port security
    - WLAN within the GUI using WPA2 PSK

### Interpret basic operations of
- Rapid PVST+ Spanning Tree Protocol    ---> [pluralsight: build STP labs] [pluralsight: multi-vlan STP labs]
    - Root port, root bridge (primary/secondary), and other port names
    - Port states (forwarding/blocking)
    - PortFast
    - Root guard, loop guard, BPDU filter, and BPDU guard
