# NAT (Network Address Translation)

Note:

- When configured, the output interface would ARP-claim the IP addresses in the POOL when needed. Below is what the other router sees, `27.0.0.2` and `27.0.0.3` share the same MAC of the NAT-router
    ```
    isp-router#sh ip arp 
    Protocol  Address          Age (min)  Hardware Addr   Type   Interface
    ...
    Internet  27.0.0.1                -   0001.4281.AC01  ARPA   GigabitEthernet0/0
    Internet  27.0.0.2                2   0090.2B85.5B02  ARPA   GigabitEthernet0/0
    Internet  27.0.0.3                2   0090.2B85.5B02  ARPA   GigabitEthernet0/0
    ```

## Configure in/out interface
```
isp-router(config)#int g0/0
isp-router(config-if)#ip nat inside

isp-router(config-if)#int g0/1
isp-router(config-if)#ip nat outside
```

## Static 1-to-1 IP mapping
```
isp-router(config)#ip nat inside source static 192.168.0.10 17.0.0.1
```

## Pool some-to-some IP mapping
```
local-router(config)# ip access-list extended ACCESS
local-router(config-ext-nacl)# permit ip 192.168.0.0 0.0.0.255 any
local-router(config-ext-nacl)# deny ip any any

local-router(config)# ip nat pool ACCESS-POOL 27.0.0.3 27.0.0.6 netmask 255.255.255.248

local-router(config)#ip nat inside source list ACCESS pool ACCESS-POOL
```

## Pool some-to-some IP+Port mapping
Same as above but just add key word overload
```
local-router(config)#ip nat inside source list ACCESS pool ACCESS-POOL overload
```
