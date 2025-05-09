# Compare Operators

| Compare Operators                                     | Lower Number Wins | Higher Number Wins | Notes                                                                             |
|-------------------------------------------------------|-------------------|--------------------|-----------------------------------------------------------------------------------|
| VLAN Trunking Protocol (VTP) sync whose VLAN database |                   | ✅                  | Switch on VTP operating mode server, with higher VLAN config revesion number wins |
| STP Root Switch Election                              | ✅                 |                    | The lowest priority; if tie, the lowest switch MAC address                        |
| Routing Path Selection by Admin Distance              | ✅                 |                    | Connected:0, Static:1, Internal-EIGRP:90, OSPF:110, UNKOWN:255                    |
| OSPF DR/BDR Election                                  |                   | ✅                  | The highest OSPF interface priority [0, 255], if tie then highest OSPF RID        |
