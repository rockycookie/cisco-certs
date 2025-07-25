# OSPF Neighbor States
When OSPF adjacency is formed, a router goes through several state changes before it becomes fully adjacent with its neighbor. Those states are defined in the OSPF RFC 2328 , section 10.1.

## States
1. Down
2. Attempt
    - a Hello packet has been sent to the neighbor, but receive no packet yet
3. Init
    - a Hello packet has recently been seen from the neighbor
4. 2-Way
    - communication between the two routers is bidirectional
        - assured by Hello protocol
    - The (Backup) Designated Router is selected in state 2-Way or greater
5. ExStart
    - first step in creating an adjacency
    - to decide which router is the master, and to decide upon the initial DD sequence number
    - Neighbor conversations in this state or greater are called adjacencies
6. Exchange
    - send Database Description packets to descirbe router's entire link state database
    - each packet has a DD sequence number, and is explicitly acknowledged
7. Loading
    - send Link State Request packets asking for LSAs
8. Full
    - fully adjacent
    - adjacencies will now appear in router-LSAs and network-LSAs
