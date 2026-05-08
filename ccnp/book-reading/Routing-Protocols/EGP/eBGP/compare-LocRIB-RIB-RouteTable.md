# Compare the 3

## Loc-RIB (Local RIB - BGP Table)
- Entry Format:
    - Status code
        - `*` (Valid): The route is usable
        - `>` (Best): This path won the BGP selection process
        - `r` (RIB-failure): Won in BGP but lost to another protocol (AD) in the Global RIB
        - `i`: Manually Injected into the table
            - this means the route was added via the network command or via a manual aggregate
            - this is called `IGP` by Cisco which is a "legacy lie" to nowadays Interior Gateway Protocol
    - Network Prefix and Mask: The destination (e.g., `10.1.1.0/24`)
    - Next Hop: The IP address where traffic should be sent (must be reachable for the route to be valid)
    - PAs (Path Attriubtes)
        - Weight: Cisco-proprietary local priority
        - Local Preference: Priority within the AS
        - `AS_Path`: The list of Autonomous Systems the route has traveled through
            - left --> right: most-recently-reached --> origin
        - Origin: How the route entered BGP (IGP, EGP, or Incomplete)
        - MED (Multi-Exit Discriminator): Used to influence neighbors on which entry point to use
        - Community: Tags used for filtering or grouping routes
    - Metric: Often displays the MED or the internal IGP cost to reach the next hop
- Scope:
    - Contains all route candidates it received from its BGP peers
        - the best path is marked and copied to global RIB
    - integration with the other 2
        - Loc-RIB to Global RIB
        - Global RIB to Routing Table
- Verify:
    - `show ip bgp [prefix]`

## RIB (Routing Information Base)
- Scope:
    - Contains all active routes learned from 
        - routing protocols (OSPF, EIGRP, BGP)
        - static routes
        - directly connected interfaces
    - AD (Administrative Distance Check)
        - is applied here to decide the winners, which are copied to the Routing Table
- Verify:
    - `show rib`

## Routing Table
- Scope:
    - The subset of the RIB consisting of the **best routes** installed into the forwarding plane
    - Used for actual packet forwarding
- Verify
    - `show ip route` --> final active table
