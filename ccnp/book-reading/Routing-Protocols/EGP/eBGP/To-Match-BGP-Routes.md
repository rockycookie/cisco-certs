# Methods to match BGP routes
- to apply policy

## Prefix List

```
ip prefix-list <prefix list NAME> seq <Seq number> permit/deny <Network/Length> [ge Min-Mask] [le Max-Mask]

''' Method 1: Direct injection'''
router bgp <AS number>
    neighbor 10.0.0.2 remote-as 65002
    neighbor 10.0.0.2 distribute-list prefix <prefix list NAME> in/out

''' Method 2: Using a Route-Map '''
route-map <route map NAME> permit 10
    match ip address prefix-list <prefix list NAME>

router bgp <AS number>
    neighbor 10.0.0.2 remote-as 65002
    neighbor 10.0.0.2 route-map <route map NAME> in/out
```

## ACL
While ACLs were historically the primary tool for BGP route filtering, they are difficult to read and manage when handling complex subnet mask matching. Today, network engineers primarily use IP Prefix-Lists for BGP selection.

### Standard ACL
Evaluates only the network prefix (the source IP)

### Extended ACL
Evaluates both the network prefix and the subnet mask length
```
access-list <ACL ID> permit/deny ip <Network ID> <Network Wildcard> <Subnet Mask> <Mask Wildcard>

router bgp <AS number>
    neighbor <Peer IP> distribute-list <ACL ID> in/out
```

## AS_PATH Regex
- BGP Regular Expressions (Regex) are used to match patterns in the AS-Path attribute of a BGP route
- Instead of filtering routes by their IP addresses, Regex allows you to filter/manipulate routes based on the specific Autonomous Systems (AS) they have traveled through

```
ip as-path access-list 10 deny _65999$      // deny route originated from AS 65999
ip as-path access-list 10 permit .*         // allow any

route-map <route map NAME> permit 10
    match as-path 10

router bgp 65001
    neighbor 10.0.0.2 route-map <route map NAME> in/out
```

## Community matching

```
ip community-list 100 permit 333:333
    
route-map COMMUNITY-CHECK deny 10
    description Block Routes with Community 333:333 in it
    match community 100
route-map COMMUNITY-CHECK permit 20
    description Allow routes with either community in it
    set weight 111
    set community 10:23                     // Sample 1
    set community 3:0 3:3 10:10 additive    // Sample 2

router bgp 65100
    address-family ipv4 unicast
    neighbor 10.12.1.2 route-map COMMUNITY-CHECK in
```

## Route Maps
- routing policy on a neighbor-by-neighbor basis

| Prefix-List Action | Route-Map Action | Final Result | Explanation |
|---|---|---|---|
| Permit | Deny | ❌ Dropped | Route matches the prefix-list, so the route-map denies it. |
| Permit | Permit | Allowed | Route matches the prefix-list, so the route-map permits it. |
| Deny | Permit | ➡️ Goes to Next Line | Route is skipped by this line; BGP evaluates the next route-map sequence number. |
| Deny | Deny | ➡️ Goes to Next Line | Route is skipped by this line; BGP evaluates the next route-map sequence number. |
