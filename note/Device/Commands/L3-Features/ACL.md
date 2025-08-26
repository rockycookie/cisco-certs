# ACL

## Show
```
acl-router# sh ip access-lists

Extended IP access list router-acl
    10 permit tcp any host 192.168.100.100 eq 443
    20 deny ip any any
```

## Creation
```
acl-router(config)# ip access-list standard ?
  <1-99>  Standard IP access-list number
  WORD    Access-list name

acl-router(config)# ip access-list extended ?
  <100-199>  Extended IP access-list number
  WORD        name
```

### Operations on an ACL
```
acl-router(config-ext-nacl)#?
  <1-2147483647>  Sequence Number
  default         Set a command to its defaults
  deny            Specify packets to reject
  exit            Exit from access-list configuration mode
  no              Negate a command or set its defaults
  permit          Specify packets to forward
  remark          Access list entry commen
```

### Standard Numbered/Named ACL
- Matching source IP only
```
acl-router(config-std-nacl)# {permit | deny} {(host) IP | IP Wildcard-Mask | any}
```

### Extended Numbered/Named ACL
- Matching all
- global command (`configure terminal`) which stays in global command
```
acl-router(config-ext-nacl)# {permit | deny} {tcp | udp | ip}  \
{(host) src_IP (src_wildcard) (src_port) | any} \
{(host) dest_IP (dest_wildcard) (dest_port) | any}
```
- port
    - `eq 21`, `lt 21`, `ne 21`, `gt 21`, `20 to 21`
    - `ftp` (eq 21), `telnet` (23), `smtp` (25), `domain` (53)
    - `bootps` (67), `bootpc` (68), `tftp` (69), `www` (80), `pop3` (110), `snmp` (161)

## Apply ACL to Interface
```
acl-router(config-if)# ip access-group <number | name> {in | out}
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
