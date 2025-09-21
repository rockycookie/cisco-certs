# Company Plan

1. Ask ISP for a block
2. Decide where IPv6 subnets are needed
    - one per VLAN
    - one per point-to-pint WAN connection (serial/Ethernet)
3. Decide subnet IDs
    - Prefix/Subnet ID bits
        - Global Routing Prefix (assigned by ISP)
        - Subnet bits
    - Interface/Host ID bits (usually 64 bits)
4. Assign subnets to internetwork topologies

<br/>

Note: 
- The IPv6 subnet ID, more formally called the subnet router anycast address, is
reserved and should not be used as an IPv6 address for any host.