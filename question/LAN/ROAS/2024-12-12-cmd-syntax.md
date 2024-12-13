### The diagram shows the correct details for a new ROAS configuration on router R1. Another co-worker, tasked with creating the configuration, asks you to review their proposed config (see exhibit.) Which options are true of the potential configuration of R1?
```
  interface GigabitEthernet0/0
   encapsulation dot1q 1
   ip address 10.10.10.1 255.255.255.0
   no shutdown
  !
  interface GigabitEthernet0/0.100
   encapsulation dot1q 20
   ip address 20.20.20.1 255.255.255.0
  !
  interface GigabitEthernet0/0.200
   encapsulation dot1q 40 
   ip address 30.30.30.1 255.255.255.0
  ! 
  interface GigabitEthernet0/0.300
   encapsulation dot1q 30 native
   ip address 40.40.40.1 255.255.255.0
```

- [ ] It will work fine, as expected.
- [ ] The mismatch of VLAN IDs and subinterface numbers will prevent the trunk from working.
- [ ] The interfaces handling the VLAN 20 and 40 traffic have their assignment commands reversed.
- [x] The interfaces handling the VLAN 30 and 40 traffic have their assignment commands reversed.
- [x] The physical interface has a command that is invalid.
- [ ] The VLAN assignment commands are all using the wrong syntax.


