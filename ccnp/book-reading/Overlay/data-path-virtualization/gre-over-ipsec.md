# GRE over IPsec

## Configuration Steps

### using IPsec profile
1. Configure an ISAKMP policy for IKE SA
2. Configure PSK
3. Create a transform set and enter transform set configuration mode
4. Create an IPsec profile and enter IPsec profile configuration mode
5. Apply the IPsec profile to a tunnel interface

### using crtpyo map
1. Configure a crypto ACL to classify VPN traffic
2. Configure an ISAKMP policy for IKE SA
3. Configure PSK
4. Create a transform set and enter transform set configuration mode
5. Configure a crypto map and enter crypto map configuration mode
6. Apply a crypto map to the outside physical interface
