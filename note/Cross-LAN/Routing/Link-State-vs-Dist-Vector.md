# Linked State vs Distance Vector

|                 | Convergence | Resource utility | Rate by                             | Each router talks to | Example      |
|-----------------|-------------|------------------|-------------------------------------|----------------------|--------------|
| Linked-State    | fast        | high             | hop count / bandwidth / delay       | all routers          | OSPF / IS-IS |
| Distance-Vector | slow        | low              | hop count / bandwidth / delay / ... | immediate neighbours | RIP / EIGRP  |

## Linked State
- route with shortest path
- high demand on resources to run the algorithm
- Hello packets and LSA
    - to build and maintain topological database
- send LSA after convergence only on changes
- require a hierarchical IP adderssing scheme for optimal functionality
    - efficient route aggregation & summarization
- example: OSPF

## Distance Vector
- send entire routing table 
    - to immdediate neighbours only
    - regularly
- rate by number of hops
- convergence slow
- 
- example: RIP
