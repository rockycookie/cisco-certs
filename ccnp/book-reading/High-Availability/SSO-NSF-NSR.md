

| Features | **SSO** (Stateful Switchover) | **NSF** (Non-Stop Forwarding) | **NSR** (Non-Stop Routing) |
|---|---|---|---|
| **Scope of Operation** | Hardware / OS Layer (Chassis RPs) | Data Plane Layer (Forwarding tables) | Control Plane Layer (Routing engines) |
| **Primary Job** | Keeps the standby hardware alive and ready. | Keeps traffic moving using frozen FIB tables. | Keeps routing protocol sessions alive. |
| **What happens on crash** | Standby processor takes control instantly. | Traffic flows while the routing table is rebuilt. | Traffic flows and routing table never resets. |
| **Neighbor Impact** | Neighbors lose sync at the protocol level. | Neighbors actively assist in the recovery. | Neighbors notice absolutely nothing. |

## Terminologies
- CEF/FIB (Forwarding Information Base)
    - a pre-computed cache of the network topology
    - Data Plane (Hardware/ASICs)
        - stored directly in the router's data plane hardware (like TCAM, ASICs or line cards)
    - Forwards packets instantly
    - Flat, binary tree structure (Trie)
    - Next-Hop Info always fully resolved to an egress port
- RIB (Routing Information Base)
    - Control Plane (Software/CPU, stored on main RAM)
    - Learns paths and builds topology
    - Complex list of networks and protocols
    - Next-Hop Info can be unresolved (requires recursion)
