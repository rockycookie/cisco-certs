# High-Level Data Link Control
- HDLC has less work to do than Ethernet because of the simple point-to-point topology of a
leased line.

## Fields
- Flag
    - Lists a recognizable bit pattern so that the receiving nodes realize that a new frame is arriving
- Address
- Control
    - mostly not in use
- Type
    - Identifies the type of Layer 3 packet encapsulated inside the frame
- FCS
    - Identifies a field used by the error detection process
