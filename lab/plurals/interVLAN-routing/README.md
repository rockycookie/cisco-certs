# Trunking and inter-VLAN routing

## Note
- Switches do **NOT** have to have IP assigned in order to trunk/forward traffic
- Switches need IP to ping others
- Trunking alone only sperates VLANs, we need router or L3 switch to do inter-VLAN routing
- Each VLAN has their own default routing gatway

## CLI Note
- Need to manually `vlan <number>` from terminal config mode (if not having port accessing the VLAN), otherwise the Vlan interface would stay down
- Router (on a stick)
    - switch side uses `switchport trunk allow <VLAN list>`
    - router side
        - `no ip address`
        - subinterface `interface f0/1.<number>`
            - `encapsulation dot1Q <vlan number>`
            - assign IP here
- L3 witch 
    - needs `ip routing` to enable
    - uses `interface vlan <number>` so that we can assign default-router IP for each
