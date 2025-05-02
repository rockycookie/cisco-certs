# Layer-3 EtherChannel

|                 | Similarity                       | Diff 1                          | Diff 2                         | Diff 3                    |
|-----------------|----------------------------------|---------------------------------|--------------------------------|---------------------------|
| L2 EtherChannel | treat multiple links as one link | switched port, only do L2 logic | multiple outbound ports (VLAN) | access endpoint hosts     |
| L3 EtherChannel | treat multiple links as one link | routed port, do L3 logic        | single outbound port (IP)      | core/distribution network |


![arch-l2-l3-etherchannel.png](./arch-l2-l3-etherchannel.png)
(Screenshot from ccna-200-301-official-cert-guide-volume1)

## How
- Make routed port instead of switch port: 
    1. `conf t` && `int [range] {int name}` for physical interface
    2. `no switchport`
    3. then we can `ip addr {ip} {mask}`

- Configure L3 EtherChannel
    1. Configure physical interfaces
        1. `conf t` && `int [range] {int name}`
        2. `no switchport`
        3. `no ip addr ...`
        4. `channel-group {num} mode active` (LACP) -- same as L2 ether channel
    2. Configure PortChannel interface
        1. `interface port-channel {num}`
        2. `no switchport`  (might already done by default)
        3. `ip addr {ip} {mask}`
