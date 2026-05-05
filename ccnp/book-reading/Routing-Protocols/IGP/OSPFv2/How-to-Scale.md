# How to Scale (shrinking LSDB)

## Blockers/Challenges
- Larger LSDB consumes more memory
- Larger LSDB makes SPF slower

## Area Segmentation
- An OSPF area is a logical group of router interfaces
    - one interface can belong to only one area
    - same-area routers share the same LSDB for the area
- Area ID is included in the OSPF hello packet
- Backbone area, area 0
    - by default, all routes from different areas are shared to area 0
    - by default, area 0 shares all routes to each area
- LSA type 3: Summary link
    - for route summarization
    - represent networks from other areas
    - ABRs summarize Type 1 LSA into Type 3
    - ABRs do not forward type 1 or type 2 LSAs into other areas
    - A `network number` for an OSPF Type 3 LSA is the destination IP prefix (subnet and mask) advertised by an ABR to propagate inter-area routes
    - An ABR advertises only one type 3 LSA for a prefix

## Route summarization
- summarization occurs between areas on the ABRs
    - normally configured as routes enter the backbone from non-backbone areas
- requires carefully developed IP addressing scheme
- by default, the summarization metric is the lowest from the LSAs
- type 3 LSA gets summarized when crossing ABRs
- type 1 LSA within the same area stays the same
- sample command
    - `area 12 range 172.16.0.0 255.255.0.0 cost 45`

## Route Filtering
- Summarization filtering
    - occurs as routes enter the area on the ABR
    - smaple: `area 12 range 172.16.2.0 255.255.255.0 not-advertise`
- Area filtering
    - filter when type 3 LSA generation occurs
    - sample:
        ```
        ip prefix-list PREFIX-FILTER seq 5 deny 172.16.1.0/24
        ip prefix-list PREFIX-FILTER seq 10 permit 0.0.0.0/0 le 32
        ...
        area 0 filter-list prefix PREFIX-FILTER in
        ```
