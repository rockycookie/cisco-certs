# EtherChannel Creation Requirements

- Speed and duplex settings must be identical
- port types
    - access
        - all ports should be in the same VLAN
    - trunk
        - all ports must use the same trunking encapsulation (ISL or 802.1Q)
        - both static, both LACP or both PAgP
- STP
    - While different STP path costs on the member ports do not prevent EtherChannel formation, it's generally recommended to have consistent STP costs for optimal performance
