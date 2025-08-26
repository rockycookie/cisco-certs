# Designated Router Selection
- DR/BDR is selected per multi-access network segment

## Tie Breaker
1. Highest OSPF priority (default is 1, note that if you configure priority of 0 that router wont enter the election process - used on FR networks.)
2. Highest router-id
3. Highest loopback interface
4. Highest configured physical interface (must be up/up)
