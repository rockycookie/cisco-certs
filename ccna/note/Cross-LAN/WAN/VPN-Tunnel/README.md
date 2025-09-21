# VPN Tunnel

Two devices near the edge of the Internet create a VPN tunnel to achieve:
- Confidentiality
    - man-in-the-middle
- Authentication
    - sender is not attacker
- Data integrity
    - data not changed
- Anti-replay

These devices:
- add headers to the original packet
- encrypt the original IP packet

## Site-to-Site VPN with IPsec
- IPsec defines how two devices, both of which connect to the Internet, can achieve the main goals of a VPN
- it uses pre-shared keys or certificates

Steps:
1. devices use some related VPN technology like Generic Routing Encapsulation (GRE) to create the concept of a tunnel (a virtual link between the routers)
2. IPsec adds the security features to the data that flows over the tunnel

## Remote Access VPN with TLS
- HTTPS on browsers
- VPN client to secure all packets
