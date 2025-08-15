# IPv6 Static Routing

## Action and Results
1. Assign address `ipv6 address 2001:DB8:1111:4::1/64` to interface `F0/0`
    - routing table adds the connected route `2001:DB8:1111:4::/64`
    - routing table adds the host route `2001:DB8:1111:4::1/128`
    - Router does not create routes based on the link-local addresses anymore
2. Configure static route
    - options
        - `R1(config)# ipv6 route 2001:db8:1111:2::/64 F0/0` (outgoing local interface)
            - usually for serial link
        - `R1(config)# ipv6 route 2001:db8:1111:2::/64 2001:DB8:1111:4::2` (next-hop global unicast or unique-local address)
            - usually for WAN link
        - `R1(config)# ipv6 route 2001:db8:1111:2::/64 FE80::FF:FE00:2` (next-hop link-local address)
            - usually for WAN link
    - routing table adds the static route `2001:DB8:1111:2::/64`

## Default Routes
- without default route, discards packets
- to configure
    - options:
        - `B1(config)# ipv6 route ::/0 S0/0/1`
    - reuslting routing table entries:
        - `S ::/0 [1/0] via Serial0/0/1, directly connected`

## Floating Static Routes
- a static route competes with others
- example, slow-but-cheap static route competes with faster OSPF route
    - `ipv6 route 2001:db8:1111:7::/64 2001:db8:1111:9::3 130`
        - with the `130` admin distance greater than OSPF's `110`
    - the faster OSPF route is prefered, and the slow-but-cheap static route is a fallover

