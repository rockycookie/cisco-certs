# DHCP

## Enable (enabled by default)
```
Switch(config)# service dhcp
```

## DHCP Packet Forwarding
```
Switch(config-if)# ip helper-address 172.16.1.2
```
Note:
- The IP could be either the DHCP server or the network with the server
