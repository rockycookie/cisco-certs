### Which answers correctly describe the function and use of OSPF database description (DD) messages?
- [ ] To exchange lists identifying known LSAs.
- [x] To exchange detailed contents of known LSAs.
- [ ] To exchange counts of known LSAs by type.
- [x] Used after forming a neighbor relationship but before any Link State Update (LSU) messages.
- [ ] Used after forming any neighbor relationships and after any Link State Update (LSU) messages.

### Review the topology diagram. All the Ethernet links have been manually assigned an OSPF cost of 4.  Each end of the serial link that connects R3 and R4 has been set to an OSPF cost of 15. The entire private network has been configured as a single OSPF area.  What is the cost from R1’s routing table to reach the network 10.45.0.0/24?

- [ ] 42
- [ ] 19
- [ ] 34
- [x] 23
- [ ] None of these are correct

### A router configuration uses the default reference bandwidth setting and also uses OSPF cost defaults as calculated by the router. Analyzing the exhibit's output for interface serial 1, which answer lists the approximate interface bandwidth of that interface?
```
HICKORY#show ip ospf interface
  Serial1 is up, line protocol is up
    Internet Address 192.168.2.201/27, Area 0
    Process ID 1, Router ID 192.168.22.1, Network Type NON_BROADCAST, Cost: 64
    Transmit Delay is 1 sec, State BDR, Priority 1
    Designated Router (ID) 10.255.255.1, Interface address 192.168.2.200
    Backup Designated router (ID) 192.168.22.1, Interface address 192.168.2.201
    Timer intervals configured, Hello 30, Dead 120, Wait 120, Retransmit 5
      Hello due in 00:00:09
    Neighbor Count is 1, Adjacent neighbor count is 1
      Adjacent with neighbor 10.255.255.1  (Designated Router)
    Suppress hello for 0 neighbor(s)
```

- [ ] 512 Kbps
- [ ] 1 Mbps
- [x] 1.5 Mbps
- [ ] 2 Mbps

First, note that the output of the show ip ospf interface command lists a cost of 64, and the default setting on the auto-cost reference-bandwidth OSPF configuration command is 100, meaning 100 Mbps. Finally, IOS uses a default OSPF cost calculation of:
reference_bandwidth / interface_bandwidth

Next, the formula needs to use consistent units, so using bits per second:
100,000,000 bps / interface_bandwidth bps = 64

Solving for interface_bandwidth:
interface_bandwidth = 100,000,000 / 64 = 1,562,500. Among the answers, it is closest to 1,500,000 bps = 1500 kbps = 1.5 mbps.

### Given the output from a working OSPF router, as seen in the exhibit, how many neighboring routers exist?
```
HICKORY#show ip ospf neighbor

Neighbor ID    Pri   State         Dead Time   Address         Interface
192.168.22.1    1    FULL/BDR      00:00:35    192.168.22.1    Fast0/0
192.168.22.1    1    FULL/  -      00:00:35    192.168.2.101   Serial1/0
10.255.255.1    10   FULL/DR       00:01:37    192.168.2.200   Serial1/1
```

- [ ] 0
- [ ] 1
- [x] 2
- [ ] 3
- [ ] More than 3
