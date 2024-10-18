# Access Control List

## Types
- Standard numbered ACLs (1–99)
- Extended numbered ACLs (100–199)
- Additional ACL numbers (1300–1999 standard, 2000–2699 extended)
- Named ACLs

## Standard numbered IP ACL
1. `conf t`
2.  `access-list {1-99 | 1300-1999} [permit | deny] {source IP} (source-wildcard)`
    - OS refers to each line in an ACL as an Access Control Entry (ACE) --> ACL statement
    - matching-parameters: source IP address or with wildcard mask
3. `int {intferace}`
4. `ip access-group {1-99 | 1300-1999} [in | out]`

## Extended numbered IP ACL
1. `conf t`
2. `access-list {100-199 | 2000-2699} [permit | deny] {protocol} {source_IP + wildcard_mask} {source_port} {dest_IP + wildcard_mask} {dest_port}`
    - protocol: ip, tcp, udp, icmp (ping)
    - port
        - operator: `eq`, `lt`, `ne`, `gt`, `range`
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
3. `[permit | deny] {protocol} {source_IP + wildcard_mask} {source_port} {dest_IP + wildcard_mask} {dest_port}`
