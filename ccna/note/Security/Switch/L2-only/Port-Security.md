# Switch Port Security
- Port security identifies devices based on the source MAC address of Ethernet frames
- When a frame with a new source MAC address arrives, pushing the number of MAC addresses past the allowed maximum, a port security violation occurs

## Configuration
1. `switchport mode {access | trunk}`
2. `switchport port-security` to enable port security on the interface
3. `switchport port-security maximum <number>` to override the default maximum number (1) of allowed MAC addresses associated with the interface
4. `switchport port-security violation {protect | restrict | shutdown}`
    |                                                                                       | protect | restrict | shutdown |
    |---------------------------------------------------------------------------------------|---------|----------|----------|
    | Discards offending traffic                                                            | ✅       | ✅        | ✅        |
    | Sends log and SNMP messages                                                           |         | ✅        | ✅        |
    | Disables the interface by putting it in an err-disabled state, discarding all traffic |         |          | ✅        |
5. `switchport port-security mac-address <mac-address>` to predefine any allowed source MAC addresses for this interface
6. `switchport port-security mac-address sticky` to “sticky learn” dynamically learned MAC addresses
