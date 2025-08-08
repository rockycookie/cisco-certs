
# Memory Storages
- MAC address table ---> ternary content-addressable memory (TCAM)
- IOS resides ---> flash
- startup-configuration ---> NVRAM
- running-configuration, logs, and so on ---> DRAM (lost after reboot)


## SDM (Switch Database Manager)

### `sdm prefer { default | dual-ipv4-and-ipv6 default | lanbase-routing | qos }` 
It's used on Cisco Catalyst switches to manage the memory usage of the TCAM
```
configure terminal

sdm prefer { default | dual-ipv4-and-ipv6 default | lanbase-routing | qos } 

end

reload
```


- LAN Base routing template
    - allows the switch to route between VLANs and Supports static routing on SVIs
- Default template
- Dual IPv4 and IPv6 template
- QoS

### `show sdm prefer`
```
Switch# show sdm prefer

The current template is "lanbase-routing" template.
The selected template optimizes the resources in
the switch to support this level of features for
8 routed interfaces and 255 VLANs.
 
number of unicast mac addresses: 4K
number of IPv4 IGMP groups + multicast routes: 0.25K
number of IPv4 unicast routes: 0.75K
number of directly-connected IPv4 hosts: 0.75K
number of indirect IPv4 routes: 1K
number of IPv4 policy based routing aces: 0
number of IPv4/MAC qos aces: 0.125k
number of IPv4/MAC security aces: 0.375k 
```

