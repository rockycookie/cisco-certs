# Cabling Topics in CCNA

- 1.3 Compare physical interface and cabling types
    - 1.3.a Single-mode fiber, multimode fiber, copper
    - 1.3.b Connections (Ethernet shared media and point-to-point)
- 1.4 Identify interface and cable issues (collisions, errors, mismatch duplex, and/or speed)


## L1: Ethernet physical layer standards
The IEEE defines Ethernet physical layer standards using `802.3` formally

Informally:
- UTP (with a suffix that includes `T`)
- fiber (with a suffix that includes `X`)

| Name             | IEEE informal | IEEE formal | Speed    | Cable Type | Max Length |
|------------------|---------------|-------------|----------|------------|------------|
| Ethernet         | 10BASE-T      | 802.3       | 10 Mbps  | Copper     | 100 m      |
| Fast Ethernet    | 100BASE-T     | 802.3u      | 100 Mbps | Copper     | 100 m      |
| Gigabit Ethernet | 1000BASE-LX   | 802.3z      | 1 Gbps   | Fiber      | 5 km       |
| Gigabit Ethernet | 1000BASE-T    | 802.3ab     | 1 Gbps   | Copper     | 100 m      |
| 10 Gig Ethernet  | 10GBASE-T     | 802.3an     | 10 Gbps  | Copper     | 100 m      |
|                  | 10GBASE-LX4   |             |          | MM (Fiber) | 300 m      |
|                  | 10GBASE-S     |             |          | MM (Fiber) | 400 m      |
|                  | 10GBASE-LR    |             |          | SM (Fiber) | 10 km      |
|                  | 10GBASE-E     |             |          | SM (Fiber) | 30 km      |

- More info: https://ethernetalliance.org
- Yes, 100 meters is the limit of UTP

### Tradeoffs among different cable types
|                                     | UTP   | Multi-mode Fiber | Single-mode Fiber |
|-------------------------------------|-------|------------------|-------------------|
| Cable Cost                          | Low   | Medium           | High              |
| Switch Port Cost                    | Low   | Medium           | High              |
| Max Distance                        | 100 m | 500 m            | 40 km             |
| Affected by EMI                     | Some  | None             | None              |
| Risk of signal emitted out of cable | Some  | None             | None              |

## L2: All on the same data-link layer protocol - Ethernet!

No matter whether the data flows over a UTP cable or any kind of fiber cable, and no matter the speed, the data-link header and trailer use the same format.
