# Automation

## Function Separation
### Data Plane
The tasks that a networking device does to send/forward/receive a message.

### Control Plane
Actions that control the data plane, like
- Routing protocols (OSPF, EIGRP, ...)
- ARP, NDP, MAC learning
- STP

### Management Plane
The management plane includes protocols that allow network engineers to manage the devices, like
- TelNet, SSH, SNMP, SysLog

<br/>

## Controller Based Networking === SDN (Software Defined Networking)

### "Controller Core" (North)
- a centralized software application that does some control plane works
- `distributed control plane` vs `centralized control plane`
- it sits anywhere in the network that has IP reachability to the devices in the network

### Network Devices (South)
- each of the network devices still has a data plane
- however, NONE of the network devices has a control plane (e.g. they do not populate their forwarding tables by routing procotols like OSPF)

#### Overlay
- VXLAN tunnels between SDA switches
- to transport traffic from one fabric endpoint to another 

#### Uderlay
- The network of (multilayer) devices and connections
- to support the dynamic discovery of all SDA devices and endpoints
- to support VXLAN
- Cisco
    - All switches act as Layer 3 switches with IS-IS routing protocol
    - SDA edge node acts as the default gateway for the endpoint devices
    - No STP, HSRP needed
    - Use ASIC on each switch for VXLAN --> no performance penalty
    - VXLAN encapsulates the entire data link frame (L2) instead of only encapsulating the IP packet (L3)

#### Fabric
- combination of overlay and underlay
- Fabric edge node: A switch that connects to endpoint devices
    - The first SDA node to receive the frame encapsulates the frame in a new message using a tunneling specification (VXLAN) and forwards the frame into the fabric
    - ingress node
    - the frame is forwared within the fabric based on its VXLAN details
    - The last SDA node removes the VXLAN details and send the original frame to the desitination endpoint
- Fabric border node: A switch that connects to devices outside SDA’s control
- Fabric control node: A switch that performs special control plane functions for the underlay (LISP)

#### Fabric's control plane
- Fabric edge node 
    - creates Endpoint Identifier (EID) per {MAC addr, IP addr, subnet}
- LISP map server
    - stores mapping of node-to-EID
    - the node in the mapping is also called matching Routing Locators (RLOCs)

### Communication bettwen them

- **SBI (Southbound Interface)**
    - it allows the controller to program the data plane forwarding tables of the networking device
    - e.g. OpenFlow, OpFlex, SSH+SNMP+?
- **NBI (Northbound Interface)**
    - it allows controller application to control the controller, using like Java API

### Controller App
- it is a separate prgroam
- it pulls information from the controller core using its (REST) API
- it programs flows into the devices using SBI
- e.g.
    - OpenDaylight Controller
    - Cisco Application Centric Infrastructure (ACI)
    - Cisco APIC Enterprise Module (APIC-EM)
