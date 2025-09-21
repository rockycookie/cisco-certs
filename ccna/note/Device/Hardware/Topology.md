# Device Topology

## 2-tier Topology
- Also named as "collapsed core"
- it combines distribution and core layer functions

## 3-tier Topology

- **Core (Backbone) Layer**
    - high speed first!
    - connects to every building block
    - Equal-cost multipathing
        - load balancing and fault tolerance
        - routing protocols like OSPF with `maximum-paths 4` configuration
- Between
- **Distribution Layer**
    - L3 routing
    - ACL
        - consumes router resources
    - QoS
        - optimal traffic classification and policy enforcement using commands like `class-map VOICE` and `policy-map QOS_POLICY`
- Between
    - redundant access-to-distribution connections
        - e.g. `channel-group 1 mode active`
- **Access Layer**
    - Redundant hardware
    - PoE

## Stub network
- have only one adjacent router interface
- default route woul be the only entry in the routing table
