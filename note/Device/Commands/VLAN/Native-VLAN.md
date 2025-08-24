## VLAN1
- **Mandatory**: VLAN 1 is a built-in and fundamental part of the switch's operation and cannot be removed
- **Default**: By default, all new ports on a Cisco switch are automatically assigned to VLAN 1

## Native VLAN on a trunk port
- On a trunk port, VLAN 1 is also the default native VLAN, meaning untagged traffic sent over the trunk is assumed to belong to VLAN 1
- On a trunk port, traffic is usually tagged with an 802.1Q tag to identify the VLAN. However, traffic belonging to the native VLAN does not get a tag
- It needs to be explicitly allowed by `switchport trunk allowed vlan add <ID>`
    - Google search AI suggested only needs to allow when having this allowed list

## Configure Native VLAN on a trunk port
```
switchport trunk native vlan <ID>
```
