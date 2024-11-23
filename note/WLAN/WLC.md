# Wireless LAN Controller

- A port is a physical entity that is used for connections on the controller platform
    - Distribution system ports
        - connects to a neighbor switch
    - Service port
        -  "last resort" means of accessing the controller GUI for management purposes

- An interface is a logical entity on the controller
    - Many parameters (IP addr, subnet, gateway, VLAN ID, DHCP, primary/secondary physical port)
    - types:
        - Management interface
        - AP-manager interface
        - Virtual interface
        - Service port interface (optional)
        - Dynamic interface (user-defined)

## Notes
- map { WLAN-SSID to Dynamic-interface }
- map { Dynamic-interface to VLAN }
- All interfaces trunk link to other ethernet devices
- Except Service-port-interface uses access link
