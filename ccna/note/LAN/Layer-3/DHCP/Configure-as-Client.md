# Configure Switch/Router As DHCP Client

```
# conf t

(config)# int vlan 1


(config-if)# ip address dhcp
(config-if)# no shutdown
```

- Note, router would use physical interface

## Verification

```
# show interfaces vlan 1

Vlan1 is up, line protocol is up
    Hardware is EtherSVI, address is 0019.e86a.6fc0 (bia 0019.e86a.6fc0)
Internet address is 192.168.1.101/24
MTU 1500 bytes, BW 1000000 Kbit, DLY 10 usec,
    reliability 255/255, txload 1/255, rxload 1/255
...
```

and 

```
# show dhcp lease

Temp IP addr: 192.168.1.101 for peer on Interface: Vlan1
Temp sub net mask: 255.255.255.0
    DHCP Lease server: 192.168.1.1, state: 3 Bound
    DHCP transaction id: 1966
    Lease: 86400 secs, Renewal: 43200 secs, Rebind: 75600 secs
Temp default-gateway addr: 192.168.1.1
...
```

## Side-effect on Routers

Default gateway route learned as "static" route

```
R1# show ip route static

...
Gateway of last resort is 192.0.2.1 to network 0.0.0.0
S* 0.0.0.0/0 [254/0] via 192.0.2.1
```
