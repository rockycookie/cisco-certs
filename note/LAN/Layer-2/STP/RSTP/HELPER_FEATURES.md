# Helper Features

## EtherChannel
Reduce the possibility of link/port failures that cuase STP re-convergence

## PortFast
- PortFast allows a switch to immediately transition from blocking to forwarding, bypassing listening and learning states
- The only ports on which you can safely enable PortFast on which you know that no
    - bridges
    - switches
    - or other STP-speaking devices are connected
- risks creating loop
- PortFast is most appropriate for connections to end-user devices

## BDPU Guard

### Security exposures
Attacker's switch connects to the network and claim to be the root
- worse the performance
- inspect the data frames passing through it

User/Attacker's STP-not-supported switch connects to the network
- not able to block ports and cause loops

### BDPU Guard
- it disables a port if any BPDUs are received on the port
- particularly useful on ports that should be used only as an access port and never connected to another switch
- apply together with PortFast, makes PortFast safer from causing-loops
