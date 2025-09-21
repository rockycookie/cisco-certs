# QoS Marking
## How to mark
- Classification -- the process of matching the fields in a message so that the device can take some QoS action later

### Header-based classification
- Relying on existing QoS makring within the packet
- Stateless Firewall
    - check IP packet headers
- Using ACL
    - Class-Based Marking with access lists is used to apply QoS markings (such as DSCP values) to traffic that has already been classified by other mechanisms
    - It does NOT perform the initial traffic classification or deep packet inspection itself

### Deep packet inspection
- NBAR
    - Differentiate applications 
        - e.g. Amazon entertainment video from Cisco IP camera
    - Deep packet inspection
        - beyond IP and port, check the payload
    - Protocol discovery
    - HTTP header analysis

### Others
- Flow-based classification
- Behavioural classification

## Where to mark
### IP header
- Marking a QoS field in the IP header works well with QoS because the IP header exists for the **entire trip** from the source host to the destination host
- Within 1 byte IPv4 headers - ToS (Type of Service)
    - old 3-bit IPP (IP Precedence)
    - new 6-bit **DSCP (Differentiated Services Code Point)**

### VLAN trunk, Ethernet header
- Within the third byte of the 4-byte 802.1Q header, as a 3-bit field
    - named **CoS (Class of service)** and PCP (Priority Code Point)

### Others
- WiFi: 3-bit TID
- MPLS WAN: 3-bit EXP

## To mark as what

### Expedited Forwarding (EF) DSCP value
- a single DSCP value
- use for packets that need low latency (delay), low jitter, and low loss
- Most often QoS plans use EF to mark voice payload packets

### Assured Forwarding (AF) DSCP values
- a set of 12 DSCP values, AFxy
    - x: queue 1 to 4, the larger the better queue
        - AF4x: Interactive video (for example, videoconferencing)
        - AF3x: Streaming video
        - AF2x: High priority (low latency) data
        - AF1x (=== CS0): Standard data
    - y: drop priority 1 to 3, the larger gets dropped first
- a queuing system with 
    - 4 queues
    - 3 levels of drop priority within each queue

### Class Selector (CS) IPP values
- DCSP values are designed with backward compatibility with CS
