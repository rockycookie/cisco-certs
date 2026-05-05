# OSPF

## Open questions
- [ ] any non-backbone area must connect to the backbone area?
    - yes, to avoid routing loops
- [ ] how to forward routes between areas?
    - inputs from any area
        1. ABR receives type 1 LSA (type 2 LSA to decide the mask)
        2. creates type 3 LSA and advertise it to other areas
    - inputs from backbone area (0) only
        1. ABR receives type 3 LSA
        2. re-creagtes new type 3 LSA
        3. sets itself as the advertising router
        4. with additional cost metric
- [ ] OSPF route selection
    - intra-area routes are always preferred over inter-area routes
    - when tie, both routes get installed into the RIB
        - ECMP (Equal-Cost Multipathing)
        - max 4 routes by default
    - for intra-area or inter-area route alone, look for the lowest path metric installed in the OSPF RIB
- [ ] Does summarization lose information? what are lost?
    - yes
    - it is normally designed to work
    - shorter mask, some route might not exist
    - metrics would become one, default to the lowest one's
        - dynamically recalculated when adding/deleting type 1 LSAs
