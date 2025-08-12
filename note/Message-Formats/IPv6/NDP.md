# Neighbor Discover Protocol

- The word neighbor refers to the fact that the devices will be on the same
data link—for example, the same VLAN
- NDP neighbor table: the equivalent of the IPv4 ARP cache
- Sample command
    ```
    R3# show ipv6 neighbors

    IPv6 Address         Age   Link-layer Addr    State    Interface
    2001:DB8:1111:5::1   0     0201.a010.0001     REACH    Gi0/0/0
    FE80::1:A0FF:FE10:1  0     0201.a010.0001     REACH    Gi0/0/0
    ```

## Capabilities
- Neighbor MAC Discovery
- Router Discovery
- SLAAC
    - When using Stateless Address Auto Configuration (SLAAC), the host uses NDP messages to learn the subnet (prefix) used on the link plus the prefix length
- Duplicate Address Detection (DAD)
    - Checks before using an IPv6 address

## Neighbor MAC Discovery
- Neighbor Solicitation (NS)
    - asking the host with a particular unicast IPv6 address to send back a reply
    - sent to the solicited-node multicast address associated with the target address
- Neighbor Advertisement (NA)
    - listing that host’s MAC address
- Unsolicited Neighbor Advertisement
    - the message is sent to the all IPv6-hosts local-scope multicast address `FF02::1`

## Router Discovery
- Router Solicitation (RS)
    - `FF02::2`
- Router Advertisement (RA)
    - routers periodically send unsolicited RA messages (even without an incoming RS)
    - `FF02::1`

## Prefix discovery
Stateless Address Auto-Configuration (SLAAC) support

### SLAAC precedure
1. Learn the IPv6 prefix used on the link, from any router, using NDP RS/RA messages
2. Build an address from the prefix plus an interface ID, chosen either by using EUI-64
rules or as a random value
3. Before using the address, first use DAD to make sure that no other host is already
using the same address

## Duplicate Address Detection (DAD)

- Hosts use DAD not only at the end of the SLAAC process, but also any time that a host interface initializes.
    - no matter whether using SLAAC, DHCP, or static address configuration
- NDP NS and NA messages
    - a host sends an NS message for its own IPv6 address
- Hosts do the DAD check for each of their unicast addresses, link-local addresses included,
both when the address is first used and each time the host’s interface comes up.
