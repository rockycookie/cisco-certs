# Network Advertisement
Notes:
- Adj-RIB-Out/In is (2) per BGP session
- BGP only advertises the best path by default to other BGP peers, regardless of the total route number within Loc-RIB

## Outbound workflow

1. Configure `network` command
    ```
    router bgp 65100
    neighbor 10.12.1.2 remote-as 65200
    network 10.12.1.0 mask 255.255.255.0
    network 192.168.1.1 mask 255.255.255.255
    ```
2. the BGP proces searches the RIB routes for an exact network prefix match
3. set PAs based on the match
4. install the route to Loc-RIB
5. each entry in Loc-RIB get checked/filtered by
    1. Validity check
    2. Outbound route policies
6. then the routes are put to Adj-RIB-Out
7. Advertise all routes within Adj-RIB-Out to the peer

## Inbound workflow

1. raw routes received and cached on Adj-RIB-In table
2. those routes are evaluated by the inbound route policy, and the passing routes are written to Loc-RIB
 - after this step, Adj-RIB-In's memory is cleared
3. validity check
4. Install the best-path route into the RIB (and ignore the others)
5. do the outbound workflow
