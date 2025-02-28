# Compare Operators

| Compare Operators               | Lower Number Wins | Higher Number Wins | Notes                                                                      |
|---------------------------------|-------------------|--------------------|----------------------------------------------------------------------------|
| STP Root Switch Election        | ✅                 |                    | The lowest priority; if tie, the lowest switch MAC address                 |
| Routing Protocol Admin Distance | ✅                 |                    | Connected:0, Static:1, Internal-EIGRP:90, OSPF:110, UNKOWN:255             |
| Routing Path Selection          | ✅                 |                    |                                                                            |
| OSPF DR/BDR Election            |                   | ✅                  | The highest OSPF interface priority [0, 255], if tie then highest OSPF RID |
