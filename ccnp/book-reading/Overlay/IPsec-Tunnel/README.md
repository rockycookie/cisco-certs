## Procedures

### Phase 1: ISAKMP (Management Tunnel)
```
Router(config)# crypto isakmp policy 10
Router(config-isakmp)# encryption aes
Router(config-isakmp)# hash sha256
Router(config-isakmp)# authentication pre-share
Router(config-isakmp)# group 14

Router(config)# crypto isakmp key YourSecretKey address 203.0.113.2
```
1. Both sides use DH `group 14` to get DH shared secret
    - `sha256` used for integrity check
2. Key Derivation Function (KDF): This shared secret is
    - combined with other data (`pre-share` key + nonce)
    - put through a hashing algorithm (like `sha256`)
3. KDF generates:
    1. Authentication Hash
    2. AES Key
3. The routers exchange the authentication hashes to finish the authentication

### Phase 2: IPsec (Data Tunnel)
```
Router(config)# crypto ipsec transform-set MYSET esp-aes esp-sha256-hmac
```

- Even without Perfect Forward Secrecy (PFS), the router generates new/unique keys for Phase 2 (not reusing key from phase 1)
    - Phase 1 keys usually last 24 hours, while Phase 2 keys are often refreshed every hour
    - Phase 1 is a single bidirectional tunnel. Phase 2 actually creates two separate tunnels (one for inbound traffic and one for outbound), each with its own unique AES key
- Some of the phase 1 information is reused to generate phase 2 AES keys
- The difference is where the encryption/hash is applied and what it is protecting
    - `esp-aes` vs `aes`
    - `esp-sha256-hmac` vs `sha256`

### Binding and Activation

```
Router(config)# ip access-list extended VPN-TRAFFIC
Router(config-ext-nacl)# permit ip 10.1.1.0 0.0.0.255 10.2.2.0 0.0.0.255
```

#### Crypto Map
```
Router(config)# crypto map MYMAP 10 ipsec-isakmp
Router(config-crypto-map)# set peer 203.0.113.2
Router(config-crypto-map)# set transform-set MYSET
Router(config-crypto-map)# match address VPN-TRAFFIC
```

#### IPsec Profile
```
Router(config)# crypto ipsec profile MY_PROFILE
Router(config-crypto-profile)# set transform-set MYSET

Router(config)# interface tunnel 0
Router(config-if)# ip address 10.255.255.1 255.255.255.252
Router(config-if)# tunnel source GigabitEthernet0/0
Router(config-if)# tunnel destination 203.0.113.2
Router(config-if)# tunnel mode ipsec ipv4

Router(config-if)# tunnel protection ipsec profile MY_PROFILE
```

- The policy-profile association happens automatically through the Peer IP address
- Morden: If your config starts with `crypto ikev2 profile ...`, then your IPsec profile must include that `set ikev2-profile ...` line to bridge the management side (Phase 1) to the data side (Phase 2)
