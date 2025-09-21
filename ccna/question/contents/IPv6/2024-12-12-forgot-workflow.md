### Host A, in one Ethernet VLAN, needs to communicate using IPv6 to host B, which is in another Ethernet VLAN. Which answer best describes the protocol used by host A to learn the layer 2 address of Host B?

- [x] No protocol is used; A does not learn B's MAC address.
- [ ] ARP
- [ ] NDP
- [ ] OSPFv3

### Examine the output of the show ipv6 interface brief command shown in the exhibit. What two address types are shown?
```
R1# show ipv6 interface brief
FastEthernet0/0            [administratively down/down]
    unassigned
GigabitEthernet1/0         [administratively down/down]
    FE80::C800:1FF:FE7E:1C
    FD00:1:1:2:C800:1FF:FE7E:1C
```

- [ ] Multicast
- [ ] Anycast
- [x] Link-local
- [x] Unique local

### Based on the exhibit, which two solicited-node multicast addresses will the router create?
```
R1# show ipv6 interface GigabitEthernet 0/3
GigabitEthernet0/3 is up, line protocol is up
  IPv6 is enabled, link-local address is FE80::AB:ABAB
  No Virtual link-local address(es):
  Global unicast address(es):
    2001:DB8:2211:1::1, subnet is 2001:DB8:2211:1::/64
  Joined group address(es):
    FF02::1
    FF02::2
    FF02::5
  (output omitted)
```

- [ ] FF02::1:FF00:1
- [ ] FF02::1:FFAB:ABAB
- [ ] FF01::1:FFAB:ABAB
- [ ] FF03::1:FF00:1
