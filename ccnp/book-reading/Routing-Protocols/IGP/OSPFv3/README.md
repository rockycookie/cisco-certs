# OSPFv3
- not backward compatible with OSPFv2
- OSPFv3 runs directly over IPv6
    - it can also run over IPv4
- packet format
    - the number of fields in the packet header has been reduced
        - Neighbor authentication removed --> now relies on IPsec extension headers in the IPv6 packet
    - address family independent
        - IP prefix is no longer present in the OSPF packet headers
        - support both the IPv4 and IPv6 address families
