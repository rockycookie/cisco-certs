# Verify OSPF

## `show ip route`
<details>

```
R4# show ip route

Codes: L - local, C - connected, S - static, R - RIP, M - mobile, B - BGP
D - EIGRP, EX - EIGRP external, O - OSPF, IA - OSPF inter area
N1 - OSPF NSSA external type 1, N2 - OSPF NSSA external type 2
E1 - OSPF external type 1, E2 - OSPF external type 2
! Additional legend lines omitted for brevity
Gateway of last resort is not set

10.0.0.0/8 is variably subnetted, 9 subnets, 2 masks
O 10.1.1.0/24 [110/2] via 10.1.14.1, 00:27:24, GigabitEthernet0/0/0
O 10.1.2.0/24 [110/2] via 10.1.14.1, 00:27:24, GigabitEthernet0/0/0
C 10.1.4.0/24 is directly connected, Vlan4
L 10.1.4.4/32 is directly connected, Vlan4
O 10.1.12.0/24 [110/2] via 10.1.14.1, 00:27:24, GigabitEthernet0/0/0
O 10.1.13.0/24 [110/2] via 10.1.14.1, 00:25:15, GigabitEthernet0/0/0
C 10.1.14.0/24 is directly connected, GigabitEthernet0/0/0
L 10.1.14.4/32 is directly connected, GigabitEthernet0/0/0
O 10.1.23.0/24 [110/3] via 10.1.14.1, 00:27:24, GigabitEthernet0/0/0
```
</details>

## `show ip protocols`

<details>

```
R3# show ip protocols
*** IP Routing is NSF aware ***
Routing Protocol is "ospf 1"
    Outgoing update filter list for all interfaces is not set
    Incoming update filter list for all interfaces is not set
    Router ID 3.3.3.3
    Number of areas in this router is 1. 1 normal 0 stub 0 nssa
    Maximum path: 4
! configured by router ospf command
Routing for Networks:
    10.1.13.3 0.0.0.0 area 0
    10.1.23.3 0.0.0.0 area 0
! configured by sub-interface command
Routing on Interfaces Configured Explicitly (Area 0):
    GigabitEthernet0/2/0
    GigabitEthernet0/1/0
    GigabitEthernet0/0/0
    GigabitEthernet0/0.2
    GigabitEthernet0/0.1
Routing Information Sources:
    Gateway     Distance    Last Update
    1.1.1.1     110         02:05:26
    4.4.4.4     110         02:05:26
    2.2.2.2     110         01:51:16
Distance: (default is 110)
```
</details>

## `show ip ospf interface brief`
<details>

```
R1# show ip ospf interface brief
Interface   PID Area    IP Address/Mask     Cost    State   Nbrs F/C
Gi0/0/0     1   0       10.1.12.1/24        1       BDR     1/1
Gi0/1/0     1   0       10.1.13.1/24        1       BDR     1/1
Gi0/2/0     1   0       10.1.14.1/24        1       DR      1/1
Gi0/0.2     1   0       10.1.2.1/24         1       DR      0/0
Gi0/0.1     1   0       10.1.1.1/24         1       DR      0/0
```
</details>

- `State`: Indicates the local router's role on that specific interface within the OSPF network 
    - Designated Router (`DR`), Backup Designated Router (`BDR`), or `DROther`
- `Nbrs F/C`
    - `F` (Full): The number of neighbors currently in the "Full" state, which is the highest level of adjacency in OSPF
    - `C` (Count): The total number of OSPF neighbors connected to that interface
