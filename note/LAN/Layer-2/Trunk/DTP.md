# DTP (Dynamic Trunking Protocol)
- Cisco-proprietary protocol
- dynamically decides if a link should be trunk or not
- DTP uses specific modes to negotiate trunking:
    - Dynamic Auto: The port will become a trunk port if the other side is configured as trunk or dynamic desirable
    - Dynamic Desirable: The port will actively attempt to negotiate a trunk link
    - Trunk: The port is manually configured as a trunk port and will always negotiate as a trunk. 
    - Access: The port is manually configured as an access port and will not participate in trunk negotiation

## To stop DTP
- option 1: `switchport nonegotiate`
- option 2: `switchport mode access`
