# Port Security

## Enable per Interface
```
Device(config-if)# switchport port-security
```

## Proction options
- Max num of addresses
```
Router(config-if)# switchport port-security maximum <number_of_addresses>
```
- Static and Sticky
```
Switch(config-if)#switchport port-security mac-address ?
  H.H.H   48 bit mac address
  sticky  Configure dynamic secure addresses as sticky

Switch(config-if)#switchport port-security mac-address sticky ?
  H.H.H  48 bit mac address
  <cr>
```

## Violation Mode
```
Router(config-if)# switchport port-security violation {protect | restrict | shutdown} 
```

## Show
```
Router(config-if)# do show port-security interface 
```
