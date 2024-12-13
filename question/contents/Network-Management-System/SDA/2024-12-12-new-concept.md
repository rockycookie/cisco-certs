### To which types of nodes should an ACI leaf switch connect in a typical single-site design? (Choose two answers.)
- [ ] All of the other leaf switches
- [ ] A subset of the spine switches
- [x] All of the spine switches
- [x] Some of the endpoints
- [ ] None of the endpoints

ACI uses a spine-leaf topology. With a single-site topology, leaf switches must connect to all spine switches, and leaf switches must not connect to other leaf switches. Additionally, a leaf switch connects to some endpoints, with the endpoints being spread across the ports on all the leaf switches. (In some designs, two or more leaf switches connect to the same endpoints for redundancy and more capacity.)

### When planning a greenfield SDA design, what traditional LAN design points should be included?

- [x] The number of switchports needed in each switch
- [x] The required speed of the switchports
- [ ] A security firewall to properly segment traffic
- [ ] The Spanning Tree mode of operation to use

When planning a greenfield SDA design, the traditional LAN design points are
- The number of switchports needed in each switch
- The required speed of the switchports
- The benefits of a switch stack in each location
- The current cable lengths and types already used
- The requirement to support power to endpoint devices
- The current power available in each new switch
- Link capacity for links between switches

For the incorrect options, a security firewall to properly segment traffic is actually something that does not help within the LAN portion of SDA.
Also, note that neither the underlay or overlay requires the use of Spanning Tree, so the STP mode need not be consisered.

### The SDA underlay uses a well-known design called a routed access layer design. What are the features of a routed access layer design?

- [ ] The border node is the default gateway for all endpoint devices.
- [ ] FHRP is required for default gateway redundancy and is deployed on the border node.
- [x] The switch to which an endpoint device physically connects is that device’s default gateway.
- [x] FHRP is no longer needed.

The features of a routed access layer design are
- All switches act as Layer 3 switches.
- All switches use an IGP.
- All links between switches act as Layer 3 routed links, not Layer 2 links spanning VLANs.
- Because no layer 2 links exist between the switches, switches do not need to use Spanning tree.
- Endpoints refer to a default gateway IP address of an interface on the layer 3 switch directly connected to the endpoint device.
- A First Hop Redundancy Protocol (FHRP) is no longer needed.

As for the incorrect answers, the border node is not the default gateway for any of the endpoint devices in the fabric. The edge node the endpoint device is connected to is the default gateway. Because of this, there is no need to run an FHRP anymore.

### What answers describe a productive step when adding SDA to a pre-existing campus network?

- [ ] DNA Center should be used to configure the underlay
- [x] DNA Center should not be used to configure the underlay
- [ ] Device software levels won’t need to be upgraded
- [x] Device software levels must meet the requirements listed on the compatibility list

When deploying SDA into an existing network - called a brownfield deployment - a number of items should be addressed. The most obvious is that there will be production traffic that you won’t want to interrupt or harm during the deployment of SDA. Because of this, DNA Center should not be leveraged to build out the underlay. If you’re in a greenfield situation (building the network with all new equipment) with SDA, you can use DNA Center to automatically build out the underlay.
With a brownfield deployment of SDA, it is critical to make sure that all the devices, new and old, are listed on the SDA compatibility list. In addition, you must make sure your devices are running software levels that are also defined on this compatibility list. Failure to follow the compatibility list can result in future outages or uncertain behavior.
