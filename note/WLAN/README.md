# Wireless LAN

1.0 Network Fundamentals
    1.1 Explain the role and function of network components
        1.1.d Access Points
    1.11 Describe wireless principles
        1.11.a Nonoverlapping Wi-Fi channels
        1.11.b SSID
        1.11.c RF (Radio Frequency)
        1.11.d Encryption
2.0 Network Access
    2.6 Compare Cisco Wireless Architectures and AP modes
    2.7 Describe physical infrastructure connections of WLAN components (AP, WLC, access/trunk ports, and LAG)
    2.8 Describe AP and WLC management access connections (Telnet, SSH, HTTP, HTTPS, console, and TACACS+/RADIUS)
    2.9 Configure the components of a wireless LAN access for client connectivity using GUI only, such as WLAN creation, security settings, QoS profiles, and advanced WLAN settings
5.0 Security Fundamentals
    5.9 Describe wireless security protocols (WPA, WPA2, and WPA3)
    5.10 Configure WLAN using WPA2 PSK using the GUI

## 802.11 std
See [802.11 std](./802.11-std.md)

## Other network topologies
- repeater
- WGB (workgroup bridge)
    - For devices can only use ethernet cable, but need wireless connection
- outdoor bridge
    - An AP can be configured to act as a bridge to form a single wireless link from one LAN to another over a long distance
    - commonly used for connectivity between buildings or between cities
    - A point-to-multipoint bridged link allows a central site to be bridged to several other sites.
- mesh network
    - In a mesh topology, wireless traffic is bridged from AP to AP, in a daisy-chain fashion, using another wireless channel.
    - e.g. many APs chained eventually conntected to one switch via one cable

## Radio Frequency
- Band
    - 2.4GHz
        - many overlapping channels
            - only 3 nonoverlapping channels are available
        - reach further
        - better penetration (walls)
    - 5GHz
        - no overlapping channel
            - many more than 3
        - less interference
