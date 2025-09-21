# Dynamic Routing

## Common
- Route by (only consider the later when the previous tied):
    1. Admin distance
    2. Cost
    3. Route by longest matching mask

## RIP
- classfully advertised networks
    - 10.0.0.0 (/8 assumed)
    - 172.16.0.0 (/12 assumed)
    - 192.168.0.0 (/16 assumed)
- `auto-summary` will be enabled by default, which un-optimize routing
    - Expected routing:
        ```
            10.0.0.0/8 is variably subnetted, 4 subnets, 2 masks
        R       10.0.0.0/8 is possibly down, routing via 192.168.1.1, GigabitEthernet2/0 (note this came from auto-summary and will disapper when times out)
        R       10.0.0.0/24 [120/1] via 192.168.2.2, 00:00:12, GigabitEthernet1/0
        R       10.10.0.0/24 [120/1] via 192.168.1.1, 00:00:11, GigabitEthernet2/0
        C       10.20.0.0/24 is directly connected, GigabitEthernet0/0
        ```
    - Auto summarized routing
        ```
            10.0.0.0/8 is variably subnetted, 2 subnets, 2 masks
        R       10.0.0.0/8 [120/1] via 192.168.2.2, 00:00:02, GigabitEthernet1/0
        C       10.20.0.0/24 is directly connected, GigabitEthernet0/0
        ```
- Steps:
    1. `conf t`
    2. `router rip`
    3. `version 2` to allow advertising subnet of larger classful network
        - e.g. `network 10.0.0.0` which would advertise connected networks `10.0.0.0/24`, `10.10.0.0/24` and more
    4. `no auto-summary`
        - see the reasoning above
    3. Add classful networks to advertise
