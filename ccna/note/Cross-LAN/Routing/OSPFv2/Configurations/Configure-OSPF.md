# Enable OSPF for an interface

## Option 1

- generic network range
    ```
    R1(config)# router ospf 9
    R1(config-router)# router-id 1.1.1.1
    R1(config-router)# network 10.1.1.1 0.0.0.0 area 0
    ```
- interface network fall within the range
    ```
    R1(config)# interface S0/0
    R1(config-if)# ip address 10.1.1.1 255.255.255.0
    ```

## Option 2

- no generic network range
    ```
    R1(config)# router ospf 9
    R1(config-router)# router-id 1.1.1.1
    R1(config-router)# no network 10.1.1.1 0.0.0.0 area 0
    ```
- per-interface config
    ```
    R1(config-router)# interface g0/0.1
    R1(config-subif)# ip ospf 1 area 0
    R1(config-subif)# interface g0/0.2
    R1(config-subif)# ip ospf 1 area 0
    R1(config-subif)# interface g0/0/0
    R1(config-if)# ip ospf 1 area 0
    ```
