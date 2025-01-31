# Router commands

## Enale IPv6
On Cisco routers, IPv4 routing is enabled by default, but IPv6 routing is not enabled by default.
```
(config terminal)# ipv6 unicast-routing
```
- without this, router does not route IPv6 traffic

## Address for interface
```
ipv6 address 2001:DB8:1111:1::1/64
```
or
```
ipv6 address 2001:DB8:1111:1::/64 eui-64
```

## Verify address
```
R1# show ipv6 interface brief
```
<details>
<summary>Output</summary>

```
GigabitEthernet0/0 [up/up]
    FE80::1:AAFF:FE00:1
    2001:DB8:1111:1::1
GigabitEthernet0/1 [administratively down/down]
    unassigned
GigabitEthernet0/0/0 [up/up]
    FE80::32F7:DFF:FE29:8568
    2001:DB8:1111:4::1
GigabitEthernet0/1/0 [administratively down/down]
    unassigned
```
</details>

<br/>

```
R1# show ipv6 interface GigabitEthernet 0/0
```
<details>
<summary>Output</summary>

```
GigabitEthernet0/0 is up, line protocol is up
    IPv6 is enabled, link-local address is FE80::1:AAFF:FE00:1
    No Virtual link-local address(es):
    Global unicast address(es):
        2001:DB8:1111:1::1, subnet is 2001:DB8:1111:1::/64
    Joined group address(es):
        FF02::1
        FF02::2
        FF02::1:FF00:1
    MTU is 1500 bytes
    ICMP error messages limited to one every 100 milliseconds
    ICMP redirects are enabled
    ICMP unreachables are sent
    ND DAD is enabled, number of DAD attempts: 1
    ND reachable time is 30000 milliseconds (using 30000)
    ND advertised reachable time is 0 (unspecified)
    ND advertised retransmit interval is 0 (unspecified)
    ND router advertisements are sent every 200 seconds
    ND router advertisements live for 1800 seconds
    ND advertised default router preference is Medium
    Hosts use stateless autoconfig for addresses.
```
</details>
