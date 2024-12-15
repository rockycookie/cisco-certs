  # OSPFv2

## Concepts

- LSA (Link-State Advertisements)
    - a data structure that contains info about network topology
- LSDB (Link-State Database)
    - collection of all the LSAs known to a router
- Dijkstra Shortest Path First (SPF)
    - algorith applied to LSDB to get shortest path to each node

## Procedure
1. Become neighbors
    1. a router sends multicast OSPF Hello packets to each interface periodically
        - which contains router ID (RID) --> 32bit, IP addr
        - multicast IP address `224.0.0.5` --> a multicast IP address intended for all OSPF-speaking routers
        - array of seen router IDs
    2. when reciving OSPF Hello packets, the router
        - the receiver list the sender as a neighbour with state `Init`
        - checks all OSPF parameters
        - add the source router ID to the seen array
        - send new Hello packet
    3. For a router state change from `Init` to `2-Way`
        - The router needs to receive a Hello packet from the neighbour whose seen array contains the receiver's router ID
    4. when both routers reach `2-Way` state
        - they become neighbours and ready to share their LSDB
2. Elect Designated Router DR per subnet
    - elect if per-interface setting: OSPF network type is `broadcast`
    - backup designated router (BDR)
3. Exchange databases with Designated Router
    1. [exchange **Database Description (DD)** packets] both neighbour routers exhange their known LSAs
    2. [loading] the receiver router checks and ask the sender for details of the receiver-missing LSAs
        - Link-State Request packets for asking for missing routes
        - **Link-State Update (LSU)** packets for sending the required routes
    3. when finished, the neighbours reach `Full` state (adjacency, fully adjacent neighbor)
4. Maintain neighbor-relationship and LSDB
    - Maintain neighbor state by sending Hello messages based on the Hello Interval and listening for Hellos before the Dead Interval expires
    - Flood any changed LSAs to each neighbor
    - Reflood unchanged LSAs as their lifetime expires (default 30 minutes)
5. Calculate (SPF) and add best route
    - considers the costs of the outgoing interfaces (only) in each route

### Become Neighbours
Routers that both
- use OSPF
- sit on the same data link

### OSPF area
- Same subnet same area
- Backbone area (area 0)
- Backbone router: routers connected to the backbone area (includes ABRs)
- Internal router: all interfaces in the same area (not in the backbone area)
- ABR (Area Boarder Router): some interfaces connected to backbone area, some connected to non-backbone area
- All non-backbone area must have ABRs connecting themselves to backbone area
- Intra-area route: route within one area
- Interarea route: route cross areas

### What info needed?
- Type 1
    - Router LSA
    - Describe a router
    - Contents: **RID**, interfaces, IP address/mask, interface states
- Type 2
    - Network LSA
    - Describe a subnet in the same area as thye asker (a network that has a DR )
    - Contents: **DR and BDR** IP addresses, subnet ID, mask
- Type 3
    - Summary LSA
    - Describe a subnet in another area
    - Contents: Subnet ID, mask, RID of **ABR** that advertises the LSA
