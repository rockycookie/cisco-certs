# IPv6 Terminologies

## Subnet ID: IPv6 prefix
- equivalent to mask in IPv4


## Unicast
### Global unicast
- First Hex Digits: `2` or `3` (originally); all not otherwise reserved (today)

### Unique local unicast
- also named "site-local"
- address format:
    - 8b
        - formal prefix `FC00::/7`
        - most commly used `FD00::/8`
    - 40b: unique 40-bit global ID (Pseudo-Random, unique so that company/network merges get less collision)
    - 16b: subnet
    - 64b: interface ID

### Link local unicast
- First Hex Digits: `FE80`

## Multicast

- First Hex Digits: `FF`
- IP ranges
    - IANA defines the range `FF30::/12` (all IPv6 addresses that begin with FF3) as the range of addresses to be used for some types of multicast applications
    - Additionally, different IPv6 RFCs reserve multicast addresses for specific purposes `FF02::/`
    - Multicasr scopes:
        - Interface-Local: `FF01`
            - Packet remains within the device. Useful for internally sending packets to services running on that same host.
        - Link-Local: `FF02`
            - Solicited-node multicast
                - `FF02::1:FF_ _ : _ _ _ _` with /104, or `FF02:0000:0000:0000:0000:0001:FF_ _: _ _ _ _`
        - Site-Local: `FF05`
        - Organization-Local: `FF08`
        - Global: `FF0E`

| Short name       | Multicast Address | Meaning                                      | IPv4 equivalent |
|------------------|-------------------|----------------------------------------------|-----------------|
| All nodes        | FF02::1           | All interfaces that use IPv6 that in the LAN | 224.0.0.1       |
| All routers      | FF02::2           | all IPv6 router interfaces in the LAN        | 224.0.0.2       |
| All OSPF         | FF02::5           | All OSPF routers                             | 224.0.0.5       |
| All OSPF DR      | FF02::6           | All OSPF-designated routers                  | 224.0.0.6       |
| EIGRPv6 Routers  | FF02::A           | All routers using EIGRP for IPv6 (EIGRPv6)   | 224.0.0.10      |
| DHCP Relay Agent | FF02::1:2         | All routers acting as a DHCPv6 relay agent   | N/A             |


## Prefix assignment structure
1. IANA (Internet Assigned Number Authority)
2. RIRs (Regional Internet Registries): AfriNIC, APNIC, ARIN, LACNIC, RIPE NCC
3. ISPs
4. Companies

## Other IPv6 addresses
- unknown/unspecified: `::`
    - A host can use the unknown address (::) when its own IPv6 address is not yet known or when the host wonders if its own IPv6 address might have problems
- loopback: `::1`
    - to test its own protocol stack
- anycast
    - why
        - multiple routers to use the same IPv6 address
        - route to the nearest router for the anycsat
    - how
        - `Router(config-if)# ipv6 address {address}/{prefix} anycast`
        - the address value can be chosen like any other IPv6 unicast addresses
