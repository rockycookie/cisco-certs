# IPv6 Static Routing

## Enable
```
Device(config)# ipv6 unicast-routing
```

## Directly Attached Route by IP Assignment
```
Device(config-if)# ipv6 address 2001:DB8:2:1234/64
```

## Directly Attached Static Route
```
Device(config)# ipv6 route 2001:DB8::/32 gigabitethernet1/0/0
```

## Next-Hop Static Route
```
Device(config)# ipv6 route 2001:DB8::/32 2001:DB8:3000::1
```

## Default Static Route
```
Device(config)# ipv6 route ::/0 serial 2/0
```

## Floating Static Route
```
ipv6 route 2001:DB8::/32 gigabitethernet1/0/0 2001:DB8:3000::2 210
```

## Show
```
Router# show ipv6 route

IPv6 Routing Table - 3 entries
Codes: C - Connected, L - Local, S - Static, R - RIP, B - BGP
U - Per-user Static route
I1 - ISIS L1, I2 - ISIS L2, IA - ISIS interarea, IS - ISIS summary
O - OSPF intra, OI - OSPF inter, OE1 - OSPF ext 1, OE2 - OSPF ext 2
ON1 - OSPF NSSA ext 1, ON2 - OSPF NSSA ext 2

S 2001:DB8:1::/48 [1/0]
    via ::, Null0
```
