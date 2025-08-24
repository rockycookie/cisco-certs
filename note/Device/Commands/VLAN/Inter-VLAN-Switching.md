## Router on a Stick

### Confiure sub-interface per VLAN
```
Router(config-if)# interface <physical_interface>.<name_number>
Router(config-subif)# encapsulation dot1Q <vlan_id>
Router(config-subif)# ip address <ip_address> <subnet_mask>
```

Note, sub-interface `name_number` does not have to be the VLAN ID
- below work also works
    ```
    192.168.10.0/24 is variably subnetted, 2 subnets, 2 masks
    C       192.168.10.0/24 is directly connected, GigabitEthernet0/1.10
    L       192.168.10.1/32 is directly connected, GigabitEthernet0/1.10
    192.168.20.0/24 is variably subnetted, 2 subnets, 2 masks
    C       192.168.20.0/24 is directly connected, GigabitEthernet0/1.200
    L       192.168.20.1/32 is directly connected, GigabitEthernet0/1.200
    ```

## L3 Switch