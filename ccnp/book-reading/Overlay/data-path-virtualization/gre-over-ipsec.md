# GRE over IPsec

## Configuration Steps

### Configure GRE

### using IPsec profile
1. Configure an ISAKMP policy for IKE SA
    - `crypto isakmp policy <priority>`
        - `encryption {des | 3des | aes | aes 192 | aes 256}`
        - `hash { sha | sha256 | sha384 | md5 }`
        - `authentication {rsa-sig | rsa-encr | pre-share}`
        - `group {1 | 2 | 5 | 14 | 15 | 16 | 19 | 20 | 24}`
2. Configure PSK
    - `crypto isakmp key <keystring> address <peer-address> [mask]`
3. Create a transform set and enter transform set configuration mode
    - `crypto ipsec transform-set <transform-set-name> transform1 [transform2 [transform3]`
        - `mode [tunnel | transport]`
            - To avoid double encapsulation (from GRE and IPsec), you should choose transport mode
4. Create an IPsec profile and enter IPsec profile configuration mode
    - `crypto ipsec profile <ipsec-profile-name>`
        - `set transform-set transform-set-name [transform-set-name2...transform-set-name6]`
            - highest priority set first
5. Apply the IPsec profile to a tunnel interface
    - `tunnel protection ipsec profile <ipsec-profile-name>`

### using crtpyo map
1. Configure a crypto ACL to classify VPN traffic
2. Configure an ISAKMP policy for IKE SA
3. Configure PSK
4. Create a transform set and enter transform set configuration mode
5. Configure a crypto map and enter crypto map configuration mode
6. Apply a crypto map to the outside physical interface
