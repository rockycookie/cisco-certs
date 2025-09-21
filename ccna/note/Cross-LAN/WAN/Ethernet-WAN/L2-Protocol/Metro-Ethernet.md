# Metro Ethernet
- Ethernet physical links (usually fiber) to connect customer’s device to SP’s device
- It is a Layer 2 service in that the WAN provider forwards Ethernet frames, like a big switch
- Many customers connect to a Metro Ethernet service with routers/L3-switches, which brings up some Layer 3 issues with IP addressing and routing protocols.
- Ethernet Virtual Circuit (EVC)

## Variations
- Ethernet Line Service
    - Virtual Private Wire Service (VPWS) --- E-Line service --- point-to-point
    - It allows the two customer devices to send Ethernet frames to each other
    - When using routers/L3-switches, each point-to-point link has its own subnet/VLAN
- Ethernet LAN Service
    - Virtual Private LAN Service (VPLS) --- E-LAN service --- full-mesh
        - needs `N*(N – 1) / 2` links
    - When using routers/L3-switches, all links in the same subnet/VLAN
- Ethernet Tree Service
    - E-Tree service --- partial-mesh
    - Hub and Spoke, point-to-multipoint
    - When using routers/L3-switches, all links in the same subnet/VLAN
