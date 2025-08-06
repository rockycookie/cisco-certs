# Configure Router as DHCP Server
Out of CCNA exam topic scope

## Method 1
```
Router(config)# ip dhcp database ftp://user:password@172.16.1.1/router-dhcp timeout 80

Router(config)# ip dhcp excluded-address 172.16.1.100 172.16.1.103
```

## Method 2
```
Router(config)# ip dhcp excluded-address 172.16.1.100 172.16.1.103
Router(config)# ip dhcp pool 1
Router(dhcp-config)# network 172.16.0.0 255.255.0.0
Router(dhcp-config)# domain-name cisco.com
Router(dhcp-config)# dns server 172.16.1.103 172.16.2.103
Router(dhcp-config)# default-router 172.16.1.100 172.16.1.101
```
