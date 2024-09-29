# MAC address table and ARP table

|                | OSI Model                                 |
|----------------|-------------------------------------------|
| MAC Addr Table | L2 (MAC addr) to L1 (switch port) mapping |
| ARP Table      | L3 (IP addr) to L2 (MAC addr) mapping     |

## MAC address table
- LAN switch prepares to forward frames by learning MAC addresses by **examining the source MAC address of each frame received by the switch**
- Multiple MAC addresses could be mapped to the same switch port, which usually means that port is connected to another switch (well or maybe opne host with multiple VMs)

## ARP table
- It exists in **any device** that has IP address assigned to it
- Windows/Mac/Linux OS are constantly checking internet connection, thus there is almost always some ARP entry

## Extra note
- I was using PacketTracer version 8.2.1.0118, where the host's IP-MAC mapping was not added to switch's ARP table while switch's MAC address table was updated. The turoial said it ARP table should also be updated~
