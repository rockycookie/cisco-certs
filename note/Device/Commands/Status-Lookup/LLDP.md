# Link Layer Discovery Protocol

## Enable
### `[no] lldp run`
- A global configuration command that sets the default mode of LLDP operation for any interface that does not have more specific LLDP subcommands (lldp transmit, lldp receive)
- both transmit and receive

### `[no] lldp transmit`
- Interface subcommand
- transmit LLDP messages or not

### `[no] lldp receive`
- Interface subcommand
- receive LLDP messages or not

### `lldp timer /seconds/`
- LLDP send timer (the frequency at which CDP sends messages)

### `lldp holdtime /seconds/`
- timer to remove LLDP info

## Show

### `show lldp`
```
SW2# show lldp
Global LLDP Information:
Status: ACTIVE
LLDP advertisements are sent every 30 seconds
LLDP hold time advertised is 120 seconds
LLDP interface reinitialisation delay is 2 seconds
```
### `show lldp interface /interface/`
```
SW2# show lldp interface g1/0/2
GigabitEthernet1/0/2:
    Tx: enabled
    Rx: enabled
    Tx state: IDLE
    Rx state: WAIT FOR FRAME
```

### `show lldp neighbors`
```
SW2# show lldp neighbors
Capability codes:
    (R) Router, (B) Bridge, (T) Telephone, (C) DOCSIS Cable Device
    (W) WLAN Access Point, (P) Repeater, (S) Station, (O) Other

Device ID   Local Intf      Hold-time       Capability      Port ID
R1          Gi1/0/2         120             R               Gi0/0/1
SW1         Gi1/0/21        120             B               Gi1/0/24

Total entries displayed: 2
```

### `show lldp entry /hostname/`
```
SW2# show lldp entry R1
Capability codes:
    (R) Router, (B) Bridge, (T) Telephone, (C) DOCSIS Cable Device
    (W) WLAN Access Point, (P) Repeater, (S) Station, (O) Other
------------------------------------------------
Local Intf: Gi1/0/2
Chassis id: 70ea.1a9a.d300
Port id: Gi0/0/1
Port Description: GigabitEthernet0/0/1
System Name: R1

System Description:
Cisco IOS Software [Fuji], ISR Software (ARMV8EB_LINUX_IOSD-UNIVERSALK9_IAS-M),
Version 16.8.1, RELEASE SOFTWARE (fc3)
Technical Support: http://www.cisco.com/techsupport
Copyright (c) 1986-2018 by Cisco Systems, Inc.
Compiled Tue 27-Mar-18 10:56 by mcpre
Time remaining: 100 seconds
System Capabilities: B,R
Enabled Capabilities: R
Management Addresses:
    IP: 10.12.25.5
Auto Negotiation - not supported
Physical media capabilities - not advertised
Media Attachment Unit type - not advertised
Vlan ID: - not advertised

Total entries displayed: 1
```