# Static Routing

## Note:

- `ping` is a round-trip interaction, it needs both outbound route and inbound route to succeed
    - outbound route: `PC->router1->router2` might work by connected route; `router2->router1->PC` needs static/dynamic route (connected route is not sufficient for PC ping router2 to work)
- `Bad mask /30 for address 172.16.0.8` first and last IP addresses in CIDR are reserved
- `no ip domain-lookup` to avoid DNS lookup by typo
