# LISP (Locator ID Separation Protocol)
- RLOC (Routing locator) --> network
- EID (Endpoint ID) --> IP address
- traditionally, the two are one-to-one static mapping entities
- LISP makes the two to 2 separate namespaces
    - so that the mappings are mutable
- why
    - originated in SP netowrks to reduce routing table size
    - overlay networks in datacenters to achieve device mobility

## Components
- ITR (Ingress Tunnel Router)
    - sits between RLOC and EID namespaces
    - de-encapsulate the traffic from the RLOC namespace
    - receive from RLOC namespace
- ETR (Egress Tunnel Router)
    - sits between RLOC and EID namespaces
    - encapsulate traffic for the EID namespace
    - send to RLOC namespace
- xTR (ITR + ETR for the same device)
- Proxy ETR/ITR
    - connecting to the network that does not understand RLOC
- Map Server
    - for ITR/ETR to
        - register their maps
        - query device --> EID namespace
    - writes/reads to/from the Map Resolver
- Map Resolver
    - holds the database of EID namespaces to RLOCs
