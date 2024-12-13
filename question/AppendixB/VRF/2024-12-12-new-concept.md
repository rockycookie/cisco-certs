### An engineer configures a router that formerly had no VRFs to add two VRFs. The configuration also places some interfaces in one VRF and some in another. How many IP routing tables does the router have now?

- [ ] 1
- [ ] 2
- [x] 3
- [ ] 4

Devices that perform routing - routers and multilayer switches - use virtual routing and forwarding (VRF) instances to create multiple instances of a router within one device. Without VRFs, a router has a single routing table, and the router places all IP routes into one IP routing table. With VRFs, the router creates a routing table for each VRF. Additional configuration can place interfaces into the VRFs so that their connected routes land in the associated per-VRF routing table. The routing protocol configuration can also place routing protocol neighbor relationships into the different VRFs, so routes learned via those neighbors again land in the correct per-VRF routing table.

A router without VRFs has a single IP routing table. Once configured to use VRFs, the router has the original IP routing table (the global routing table) plus one IP routing table per VRF. Interfaces and routing protocol neighbors not placed into a VRF feed their routes into the global routing table.

In this question, with two VRFs, the router has three IP routing tables: one per VRF plus the global routing table.
