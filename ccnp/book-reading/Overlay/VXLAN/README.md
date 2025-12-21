# VXLAN
- Wide area Ethernet switch
- has a distributed control plane
    - which device --> which tunnel endpoint
    - just like ARP table for regular switch, which MAC address --> which port
- 2 types of control plane
    - Multicast control plane
        - each VTEP joins the same multicast address
        - all VTEP MAC updates are sent to a multicast rendezvous point
        - the rendezvous point then send them out to each VTEP
    - Multi-protocol BGP
        - each VTEP puts its info in an MP-BGP update
        - and send the updates to a BGP router reflector
        - the reflector then reflects the routes to all other VTEPS
        - effectively carry L2 info just like L3 IP route in BGP
- VXLAN tunneling
    - MAC in UDP

## PIM (Protocol Independent Multicast)
- BUM traffic
    - Broadcast, Unknown Unicast, Multicast
