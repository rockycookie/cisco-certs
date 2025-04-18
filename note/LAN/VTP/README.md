# VLAN Trunking Protocol (VTP)

```
Switch# show vtp status
...
Configuration revision: 62
Number of existing VLANs: 24
VTP Operating Mode: Server
VTP Domain Name: Corporate
...
```
This would compare its revision to other switches' revisions in the same VTP domain. </br>
The switch with higher revision will overwrite others' VLAN database.

## To disable VTP

In general, to avoid VTP overwriting VLAN databases by mistake/attack:
```
vtp mode transparent
```

Some switches has `vtp mode off` now