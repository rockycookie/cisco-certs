# OSPF Cost Calculation

| Interface           | Default Bandwidth (Mbps) | Default Reference Bandwidth (Mbps)   | Formula (Mbps) | Default OSPF Cost   |
|---------------------|--------------------------|--------------------------------------|----------------|---------------------|
| OSPF mode cmd:      |                          | auto-cost reference-bandwidth ${num} |                |                     |
| Interface mode cmd: | bandwidth ${num}         |                                      |                | ip ospf cost ${num} |
| Serial              | 1.544                    | 100                                  | 100 / 1.544    | 64                  |
| Ethernet            | 10                       | 100                                  | 100 / 10       | 10                  |
| Fast Ethernet       | 100                      | 100                                  | 100 / 100      | 1                   |
| Gigabit Ethernet    | 1,000                    | 100                                  | 100 / 1,000    | 1                   |
| 10 Gigabit Ethernet | 10,000                   | 100                                  | 100 / 10,000   | 1                   |
| 100 Gigbit Ethernet | 100,000                  | 100                                  | 100 / 100,000  | 1                   |
