# Voice VLAN
- The voice VLAN feature enables access ports to carry IP voice traffic from an IP phone
- The (Cisco 7960) IP phone sends voice traffic with Layer 3 IP precedence and Layer 2 class of service (CoS) values (both are vlaue 5)

## Command
```
// Create VLANs
Switch(config)# vlan 10
Switch(config-vlan)# name Data_VLAN
Switch(config-vlan)# exit

Switch(config)# vlan 20
Switch(config-vlan)# name Voice_VLAN
Switch(config-vlan)# exit

// Configure the interface
Switch(config-if)# switchport mode access

// for regular data traffic
Switch(config-if)# switchport access vlan 10

// for the IP phone's voice traffic
Switch(config-if)# switchport voice vlan 20
```
