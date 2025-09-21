# Network Address Translation

## Background

### Functions That Extended the Life of IPv4
| Feature          | RFC  | Benefits                                                  |
|------------------|------|-----------------------------------------------------------|
| Private Networks | 1918 | Enable NAT                                                |
| NAT              | 3022 | Enable approximately 65,000 TCP/UDP sessions supported by |
| CIDR             | 4632 | a single public IPv4 address                              |

### Private Address Space
| IP range                      | Networks                    | Class | Number of Networks |
|-------------------------------|-----------------------------|-------|--------------------|
| 10.0.0.0 - 10.255.255.255     | 10.0.0.0                    | A     | 1                  |
| 172.16.0.0 - 172.31.255.255   | 172.16.0.0 - 172.31.0.0     | B     | 16                 |
| 192.168.0.0 - 192.168.255.255 | 192.168.0.0 - 192.168.255.0 | C     | 256                |

## NAT
- `global` vs `local` -- public vs private IPs
- `inside` vs `outside` -- enterprise inbound vs outbound

### Common
1. `config t` && `int {interface num}`
2. `ip nat [inside | outside]`
    - After creating the static/dynamic/PAT NAT entries, the router needs to know which interfaces are “inside” and which are “outside.”

### Static NAT
1. `config t` && `int {interface num}`
2. `ip nat inside source static {inside-local} {inside-global}`

### Dynamic NAT
1. Configure ACL that matches the NAT-requiring inbound traffic
2. `config t`
3. `ip nat pool {pool-name} {first-address} {last-address} netmask {subnet-mask}`
    - the pool of public registered IP addresses
4. `ip nat inside source list {acl-number} pool {pool-name}`

### PAT
1. Configure ACL that matches the NAT-requiring inbound traffic
2. `config t`
3. `ip nat inside source list {acl-number} interface {type/number} overload`
    - to the interface whose (single) IP address will be used for translations

## Verification
### Dynamic NAT Verification
```
NAT# show ip nat translations
Pro     Inside global   Inside local    Outside local   Outside global
---     200.1.1.1       10.1.1.1        ---             ---

NAT# show ip nat statistics
Total active translations: 1 (0 static, 1 dynamic; 0 extended)
Peak translations: 11, occurred 00:04:32 ago
Outside interfaces:
    Serial0/0/0
Inside interfaces:
    GigabitEthernet0/0
Hits: 69 Misses: 1
Expired translations: 0
Dynamic mappings:
-- Inside Source
access-list 1 pool fred refcount 1
[eml fred: netmask 255.255.255.252
    start 200.1.1.1 end 200.1.1.2
    type generic, total addresses 2, allocated 1 (50%), misses 0
```

### PAT Verification
```
NAT# show ip nat translations
Pro     Inside global       Inside local    Outside local   Outside global
tcp     200.1.1.249:49712   10.1.1.1:49712  170.1.1.1:23    170.1.1.1:23
tcp     200.1.1.249:49713   10.1.1.2:49713  170.1.1.1:23    170.1.1.1:23
tcp     200.1.1.249:49913   10.1.1.2:49913  170.1.1.1:23    170.1.1.1:23

NAT# show ip nat statistics
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
