# CDP
```
Switch(config)#no cdp run
Switch(config)#do sh cdp nei
% CDP is not enabled

Switch(config)#cdp run
...
Switch(config)#do sh cdp neighbors
Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge
                  S - Switch, H - Host, I - IGMP, r - Repeater, P - Phone
Device ID    Local Intrfce   Holdtme    Capability   Platform    Port ID
Router       Gig 0/1          160            R       C2900       Gig 0/1
Router       Gig 0/1          160            R       C2900       Gig 0/1.10
Router       Gig 0/1          160            R       C2900       Gig 0/1.200
Switch       Fas 0/10         160            S       2960        Fas 0/10
```

- More details, could be done witch device ID like `Switch(config)#do sh cdp entry Router`
    ```
    Switch(config)#do sh cdp entry *

    Device ID: Router
    Entry address(es): 
    Platform: cisco C2900, Capabilities: Router
    Interface: GigabitEthernet0/1, Port ID (outgoing port): GigabitEthernet0/1
    Holdtime: 170

    Version :
    Cisco IOS Software, C2900 Software (C2900-UNIVERSALK9-M), Version 15.1(4)M4, RELEASE SOFTWARE (fc2)
    Technical Support: http://www.cisco.com/techsupport
    Copyright (c) 1986-2012 by Cisco Systems, Inc.
    Compiled Thurs 5-Jan-12 15:41 by pt_team

    advertisement version: 2
    Duplex: full
    ---------------------------

    Device ID: Router
    Entry address(es): 
    IP address : 192.168.10.1
    Platform: cisco C2900, Capabilities: Router
    Interface: GigabitEthernet0/1, Port ID (outgoing port): GigabitEthernet0/1.10
    Holdtime: 170

    Version :
    Cisco IOS Software, C2900 Software (C2900-UNIVERSALK9-M), Version 15.1(4)M4, RELEASE SOFTWARE (fc2)
    Technical Support: http://www.cisco.com/techsupport
    Copyright (c) 1986-2012 by Cisco Systems, Inc.
    Compiled Thurs 5-Jan-12 15:41 by pt_team

    advertisement version: 2
    Duplex: full
    ---------------------------

    Device ID: Router
    Entry address(es): 
    IP address : 192.168.20.1
    Platform: cisco C2900, Capabilities: Router
    Interface: GigabitEthernet0/1, Port ID (outgoing port): GigabitEthernet0/1.200
    Holdtime: 170

    Version :
    Cisco IOS Software, C2900 Software (C2900-UNIVERSALK9-M), Version 15.1(4)M4, RELEASE SOFTWARE (fc2)
    Technical Support: http://www.cisco.com/techsupport
    Copyright (c) 1986-2012 by Cisco Systems, Inc.
    Compiled Thurs 5-Jan-12 15:41 by pt_team

    advertisement version: 2
    Duplex: full
    ---------------------------

    Device ID: Switch
    Entry address(es): 
    Platform: cisco 2960, Capabilities: Switch
    Interface: FastEthernet0/10, Port ID (outgoing port): FastEthernet0/10
    Holdtime: 170

    Version :
    Cisco IOS Software, C2960 Software (C2960-LANBASEK9-M), Version 15.0(2)SE4, RELEASE SOFTWARE (fc1)
    Technical Support: http://www.cisco.com/techsupport
    Copyright (c) 1986-2013 by Cisco Systems, Inc.
    Compiled Wed 26-Jun-13 02:49 by mnguyen

    advertisement version: 2
    Duplex: full
    ```