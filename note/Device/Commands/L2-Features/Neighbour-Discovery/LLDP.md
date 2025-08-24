# LLDP
- Not enabled by default
- `Port ID` is the remote device interface ID

```
Switch#sh lldp neighbors 
% LLDP is not enabled

Switch(config)#lldp run
Switch(config)#do sh lldp run

Switch(config)#do show lldp nei
Capability codes:
    (R) Router, (B) Bridge, (T) Telephone, (C) DOCSIS Cable Device
    (W) WLAN Access Point, (P) Repeater, (S) Station, (O) Other
Device ID           Local Intf     Hold-time  Capability      Port ID

Total entries displayed: 0

// Enaled on Router
Switch(config)#do show lldp nei
Capability codes:
    (R) Router, (B) Bridge, (T) Telephone, (C) DOCSIS Cable Device
    (W) WLAN Access Point, (P) Repeater, (S) Station, (O) Other
Device ID           Local Intf     Hold-time  Capability      Port ID
Router              Gig0/1         120        R               Gig

Total entries displayed: 1

// Enaled on Switch
Switch(config)#do show lldp nei
Capability codes:
    (R) Router, (B) Bridge, (T) Telephone, (C) DOCSIS Cable Device
    (W) WLAN Access Point, (P) Repeater, (S) Station, (O) Other
Device ID           Local Intf     Hold-time  Capability      Port ID
Switch              Fa0/10         120        B               Fa0/5
Router              Gig0/1         120        R               Gig
Switch              Fa0/10         120        B               Fa0/10

Total entries displayed: 2
```
