# Compare Operators

| Compare Operators                                     | Lower Number Wins | Higher Number Wins | Notes                                                                       |
|-------------------------------------------------------|-------------------|--------------------|-----------------------------------------------------------------------------|
| STP Root Switch Election                              | ✅                 |                    | The lowest priority wins; if tie, the lowest switch MAC address             |
| STP designated port election                          | ✅                 |                    | The lower cost (if tie then the lower bridge ID) wins                       |
| Routing Path Selection by Admin Distance              | ✅                 |                    | Connected:0, Static:1, Internal-EIGRP:90, OSPF:110, UNKOWN:255              |
| Routing Path Selection by Cost                        | ✅                 |                    |                                                                             |
| OSPF DR/BDR Election                                  |                   | ✅                  | The highest OSPF interface priority [0, 255], if tie then highest OSPF RID  |
| HSRP active router selection                          |                   | ✅                  | The higher priority wins, to own the virtual IP and virtual MAC addr        |
| VLAN Trunking Protocol (VTP) sync whose VLAN database |                   | ✅                  | Higher VLAN config revision number wins, to become the server of the domain |
