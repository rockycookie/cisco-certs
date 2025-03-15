# Quality of Service

## Classification
- the process of matching the fields in a message to make a choice to take some QoS action

### Using ACL

### Using NBAR
Differentiating applications (like Amazon entertainment video from Cisco IP camera)

## Marking

### IP header
- Marking a QoS field in the IP header works well with QoS because the IP header exists for the **entire trip** from the source host to the destination host
- Within 1 byte IP headers - ToS (Type of Service)
    - old 3-bit IPP
    - new 6-bit DSCP

### VLAN trunk, Ethernet header
- Within third byte of the 4-byte 802.1Q header, as a 3-bit field
    - named CoS (Class of service) and PCP (Priority Code Point)

### Others
- WiFi: 3-bit TID
- MPLS WAN: 3-bit EXP
