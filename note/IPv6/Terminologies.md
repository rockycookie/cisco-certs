# IPv6 Terminologies

## Subnet ID: IPv6 prefix
- equivalent to mask in IPv4

## Global unicast
- First Hex Digits: 2 or 3 (originally); all not otherwise reserved (today)

## Unique local unicast
- 8b: First 2 Hex Digits: FD
- 40b: unique 40-bit global ID (Pseudo-Random, unique so that company/network merges get less collision)
- 16b: subnet
- 64b: interface ID

## Multicast
- First Hex Digits: FF

## Link local 
- First Hex Digits: FE80

## Prefix assignment structure
1. IANA (Internet Assigned Number Authority)
2. RIRs (Regional Internet Registries): AfriNIC, APNIC, ARIN, LACNIC, RIPE NCC
3. ISPs
4. Companies
