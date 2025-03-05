# ACL

## Standard Numbered/Named ACL
- Matching source IP only
- global command (`configure terminal`) which stays in global command
```
access-list {1-99 | 1300-1999} {permit | deny} {(host) IP | IP Wildcard-Mask | any}
```

## Extended Numbered/Named ACL
- Matching all
- global command (`configure terminal`) which stays in global command
```
access-list {100-199 | 2000-2699} {permit | deny} {tcp | udp | ip}  \
{(host) src_IP (src_wildcard) (src_port) | any} \
{(host) dest_IP (dest_wildcard) (dest_port) | any}
```
- port
    - `eq 21`, `lt 21`, `ne 21`, `gt 21`, `20 to 21`
    - `ftp` (eq 21), `telnet` (23), `smtp` (25), `domain` (53)
    - `bootps` (67), `bootpc` (68), `tftp` (69), `www` (80), `pop3` (110), `snmp` (161)

## Named ACL
- global command (`configure terminal`) which enters to ACL subcommand
```
Router(config)# ip access-list {standard | extended} name

Router(config-std-nacl)# {permit | deny} {(host) IP | IP Wildcard-Mask | any}

Router(config-ext-nacl)# {permit | deny} {tcp | udp | ip}  \
{(host) src_IP (src_wildcard) (src_port) | any} \
{(host) dest_IP (dest_wildcard) (dest_port) | any}
```

## Apply ACL to Interface
- Interface subcommand
```
ip access-group number {in | out}
```

### Convention
- Place extended ACLs as close as possible to the source of the packet
    - to discard the packets early
- Place standard ACLs as close as possible to the destination of the packet
    - to avoid unintentionally discarding packets
- Place more specific statements early in the ACL
- Disable an ACL from its interface (using the `no ip access-group` interface subcommand) before making changes to the ACL

## Modify ACL
- Show ACL lines with sequence numbers
    - `show ip access-lists`
- Delete specific line
    - `no sequence-number` from ACL subcommand
- Insert new line
    - `sequence-number {pertmit | deny} ...`
