# How to Scale

- IP addressing schemes
- area segmentation
- addres/route summarization
- hardware capabilities

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

