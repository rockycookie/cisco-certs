# NAT (Network Address Translation)

## Configure in/out interface
```
isp-router(config)#int g0/0
isp-router(config-if)#ip nat inside

isp-router(config-if)#int g0/1
isp-router(config-if)#ip nat outside
```

## Static 1-to-1 IP mapping
```
isp-router(config)#ip nat inside source static 192.168.0.10 17.0.0.1
```

## Pool some-to-some IP mapping