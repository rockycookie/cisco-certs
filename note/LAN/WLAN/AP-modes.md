# AP Modes

## Autonomous Mode
### Method of configuration
- WLSE (Wireless LAN Solution Engine)
    - centralized coordination of autonomous APs
- CLI
- Web interface

## Lightweight Mode (LAP)

- Local Mode
    - default
    - provide 1+ BSSs on a single channel
    - it sepnds 60ms on every 180ms to
        - stop working
        - scan other channels for admin works
- Monitor
    - no traffic; can't serve clients
    - scan other channels for admin works for each 60ms
- FlexConnect
    - switch between SSID and VLAN with conditions
- REAP (Remote Edge AP)
    - allows AP sit on the other end of WAN link communicate with WLC

### Notes
- Admin works includes:
    - measure
        - level of noise
        - inference
    - discover rougue devices
    - find IDS (Intrusion Detection System) events

### Method of configuration
- WLC (Wireless LAN Controller)
    - physical device
- WCS (Wireless Control System)
    - software
