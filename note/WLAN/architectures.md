# Architectures

## Distributed Autonomous APs
- trunck link between access-layer switch and AP

### Standalone Autonomous AP Architecture
- Each AP configured separately
- Each SSID maps to one VLAN
- Same SSID/VLAN for roaming

### Enterprise central Architecture
- AP management platform inside enterprise
- Cisco Prime Infrastructure

### Cloud-based AP Architecture
- AP management platform on cloud outside enterprise
- Cisco Meraki

## Distributed Lightweight APs (Split-MAC Architecture)
- access link between access-layer switch and AP
- WLC (Wireless LAN Controller)
    - Management functions
        - RF, association and roaming management
        - client auth, security, QoS
    - Real-time functions
        - RF, MAC, encryption
- Split-MAC Architecture
    - What
        - normal MAC operations are pulled apart into two distinct locations
        - SSID area blelow AP, nothing between AP and WLC, VLAN above WLC
    - How
        - each AP must boot and bind itself to a WLC
            - CAPWAP tunnel between AP and WLC to carry 802.11-related and client messages
                - Tunnel 1: CAPWAP control messages
                - Tunnel 2: CAPWAP data
                    - Used for packets traveling to and from wireless clients that are associated with the AP
                    - not encrypted by default --> encryption: Datagram Transport Layer Security (DTLS)
            - Every AP and WLC must also authenticate each other with digital certificates (pre-installed)
        - once CAPWAP tunnels are built from a WLC to APs, the WLC can begin offering a variety of additional functions (...)
- Deployments
    - unified or centralized WLC deployment --> core-layer switch (top-most)
        - physical
        - typically supports up to 6,000 APs per WLC
    - cloud-based WLC deployment
        - usually virtual machine
        - typically supports up to 3000 APs per WLC
    - embedded WLC deployment --> access-layer switch (bottom)
        - small campuses or distributed branch locations (small number of APs needed)
        - WLC can be co-located with a stack of switches
        - typically supports up to 200 APs per embedded WLC
    - Mobility Express WLC --> in an AP itself
        - typically supports up to 100 APs per WLC
