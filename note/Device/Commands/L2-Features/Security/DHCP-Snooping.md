# DHCP Snooping
DHCP snooping performs the following activities:
- Validates/Filters DHCP messages received from untrusted sources
- Validate requests from untrusted hosts
    - by maintaining the DHCP snooping binding (untrusted host --> leased IP) database

## Enabling
```
switch(config)# [no] feature dhcp
switch(config)# [no] ip dhcp snooping
switch(config)# [no] ip dhcp snooping vlan 100,200,250-252
```

1. Feature enablement: The DHCP snooping feature is disabled by default
    - to begin building and maintaining the database
    - Disabling the DHCP snooping feature removes all DHCP snooping configuration
2. Global enablement: After feature enabled, it is globally disabled by default
    - all ports (except trusted) starts rejecting new DHCP server and validating IP claim

## Trust a Port
```
switch(config-if)# [no] ip dhcp snooping trust
```
