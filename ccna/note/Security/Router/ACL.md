# Access Control List

## Notes
- ACL needs to be added to VLAN interface for L3 switches; physical interfaces would NOT work!
- `ospf` is also an IP protocol, DONT `deny ip any any` without considering it!
- what happens when router/l3switch handles packet
    1. inbound ACLs filter packets
    2. lookup routing table and make forwarding decisions
    3. outbound ACLs filter packets
- port numbers can only be specified with TCP or UDP protocols in access control lists

## Types
- Standard numbered ACLs (1–99)
- Extended numbered ACLs (100–199)
- Additional ACL numbers (1300–1999 standard, 2000–2699 extended)
- Named ACLs

## Standard numbered IP ACL (filter by source IP only)
1. `conf t`
2.  `access-list {1-99 | 1300-1999} [permit | deny] {source IP} (source-wildcard)`
    - OS refers to each line in an ACL as an Access Control Entry (ACE) --> ACL statement
    - matching-parameters: source IP address or with wildcard mask
3. `int {intferace}`
4. `ip access-group {1-99 | 1300-1999} [in | out]`

## Extended numbered IP ACL
1. `conf t`
2. `access-list {100-199 | 2000-2699} [permit | deny] {protocol} {source_IP + wildcard_mask | 'host' source_IP} {source_port} {dest_IP + wildcard_mask | 'host' + dest_IP} {dest_port}`
    - protocol: ip, tcp, udp, icmp (ping)
    - port
        - operator: `eq`, `lt`, `ne`, `gt`, `range`
    - note:
        - Using ip protocol with port filtering is incorrect syntax
3. `int {intferace}`
4. `ip access-group {100-199 | 2000-2699} [in | out]`

## Standard Named IP ACL
1. `conf t`
2. `ip access-list standard {name}`
    - this will create and move context to the access list
3. `[permit | deny] {source IP} (source-wildcard)`

## Extended Named IP ACL
1. `conf t`
2. `ip access-list extended {name}`
    - this will create and move context to the access list
3. `[permit | deny] {protocol} {source_IP + wildcard_mask | 'host' source_IP} {source_port} {dest_IP + wildcard_mask | 'host' + dest_IP}`
