# Controller-Based Wireless Network (RFC 5415)

- Split-MAC architecture/mode
    - WLC handles the **control plane** (non-real-time tasks)
        - Association / Di-association
        - authentication (802.1x/EAP)
        - security policies (Classifying)
        - roaming
        - traffic management
    - LAP (Lightweight Access Point) handles the **data plane**
        - transmitting and receiving data
        - also called **real-time tasks**
            - Probe Response
            - Packet buffering
            - Fragmentation
            - Queuing
- Loacl-MAC mode
    - AP handles MAC address authentication and authorization directly
    - failover method when WLC is overloaded and temporarily unavailable

## How it works
1. LAPs power on, discover and associate with the controller
2. LAP and controller authenticate each other
    - using pre-installed certs
3. Make CAPWAP tunnels
    - Control and Provisioning of Wireless Access Points (CAPWAP) protocol
    - to carry management and data traffic
4. Controller pushes config to LAPs
5. Controller handles
    - traffic forwarding
    - traffic routing
    - security functions
    - forward between wired network and LAPs

## CAPWAP Tunnel
- using UDP ports 
    - 5246 for control
    - 5247 for data
- Security: can utilize DTLS (Datagram Transport Layer Security) for encryption
- Trasmission: very similar to Lightweight Access Point Protocol
