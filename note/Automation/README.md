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
