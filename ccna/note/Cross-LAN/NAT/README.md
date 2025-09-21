# Network Address Translation
```
4.1 Configure and verify inside source NAT using static and pools
```

- `local (private) address` to `global (public) address`
- mapping itself is global config
- per-interface need to attach mapping with inside/outside config

## Static NAT
```
ip nat inside source static <inside-local> <inside-global>
```

- Smaple
    ```
    R1# show running-config
    interface GigabitEthernet0/0
        ip address 10.1.1.3 255.255.255.0
        ip nat inside
    interface Serial0/0/0
        ip address 200.1.1.251 255.255.255.0
        ip nat outside
    ip nat inside source static 10.1.1.2 200.1.1.2
    ip nat inside source static 10.1.1.1 200.1.1.1

    R1# show ip nat translation
    Pro Inside global Inside local Outside local Outside global
    ...

    R1# show ip nat statistics
    Total active translations: 2 (2 static, 0 dynamic; 0 extended)
    Outside interfaces:
        Serial0/0/0
    Inside interfaces:
        GigabitEthernet0/0
    Hits: 100 Misses: 0
    ...
    ```

## Dynamic NAT with public address pool
- it uses ACL to identify which inside local (private) IP addresses need to have their addresses translated
- it defines a pool of registered public IP addresses to allocate

```
ip nat pool <name> <first-address> <last-address> netmask <subnet-mask>

ip nat inside source list <acl-number> pool <pool-name>
```

- Smaple
    ```
    R1# show running-config
    interface GigabitEthernet0/0
        ip address 10.1.1.3 255.255.255.0
        ip nat inside
    interface Serial0/0/0
        ip address 200.1.1.251 255.255.255.0
        ip nat outside
    ip nat pool mypool 200.1.1.1 200.1.1.2 netmask 255.255.255.252
    ip nat inside source list 1 pool mypool
    access-list 1 permit 10.1.1.2
    access-list 1 permit 10.1.1.1
    ```
- Note
    - pool creation would fail if address range is not within the same subnet described by netmask

## Dynamic NAT with public interface port number overload (PAT, Port Addr Translation)

```
ip nat inside source list <acl-number> interface <type/number> overload
```

- Smaple
    ```
    R1# show running-config
    interface GigabitEthernet0/0
        ip address 10.1.1.3 255.255.255.0
        ip nat inside
    interface Serial0/0/0
        ip address 200.1.1.249 255.255.255.252
        ip nat outside
    ip nat inside source list 1 interface Serial0/0/0 overload
    access-list 1 permit 10.1.1.2
    access-list 1 permit 10.1.1.1

    R1# show ip nat translations
    Pro Inside global Inside local Outside local Outside global
    tcp 200.1.1.249:49712 10.1.1.1:49712 170.1.1.1:23 170.1.1.1:23
    tcp 200.1.1.249:49713 10.1.1.2:49713 170.1.1.1:23 170.1.1.1:23
    tcp 200.1.1.249:49913 10.1.1.2:49913 170.1.1.1:23 170.1.1.1:23

    R1# show ip nat statistics
    Total active translations: 3 (0 static, 3 dynamic; 3 extended)
    Peak translations: 12, occurred 00:01:11 ago
    Outside interfaces:
        Serial0/0/0
    Inside interfaces:
        GigabitEthernet0/0
    Hits: 103 Misses: 3
    Expired translations: 0
    Dynamic mappings:
    -- Inside Source
    access-list 1 interface Serial0/0/0 refcount 3
    ```
