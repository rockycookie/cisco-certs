# WLAN Authentication
- `supplicant`: the device requesting access
- `authenticator`: the switch or access point
- `auth server`
- `inner authentication`: auth happens within TLS channel, could be username/password
- TLS channel is usually buit on top of TCP (less commonly on UDP)

## Open Authntication
- The only requirement is that a client must use an 802.11 authentication request
    - no other credentials are needed
- Authenticating the user’s identity is handled as a true security process through other means
- No encryption

## WEP
- Wired Equivalent Privacy (WEP)
- RC4 cipher algorithm (symmetric WEP key for both encryption and decryption)
    - WEP key is 
        - pre-shared
        - 40 or 104 bits long
- History
    - 2001, a number of weaknesses were discovered
    - 2004, officially deprecated

## 802.1x/EAP
- port-based access control standard
- establish association first, but blocking network data until authn
- sequence
    1. the client uses open authentication to associate with the AP
    2. the actual client auth occurs at an auth server
- Extensible Authentication Protocol (EAP)
    - not a specific protocol itself
    - a method to carry auth data between client and server
    - often within 802.1X framework
        - RADIUS is often used as the backend authentication server for 802.1X
    - it allows protocols below

### LEAP: no cert, dynamic wep
- No TLS channel
- Lightweight EAP (LEAP)
- Cisco proprietary
- client-(RADIUS)server mutual auth by exchanging challenge message (by successful decryption)
- dynamic WEP keys that change frequently
- deprecated

### EAP-FAST: no cert, pac
- TLS channel by PAC instead of cert + inner auth
- EAP Flexible Authentication by Secure Tunneling (EAP-FAST)
- 3-step procedure
    1. auth server (could be RADIUS) generates `Protected Access Credential (PAC)`
        - supplicant can initiate PAC provisioning
    2. client installs the PAC and use it to establish a secure TLS channel to the server
        - allowing client-server mutual auth
        - avoid the need for client-side certificate
            - PAC acts as a pre-shared key that allows EAP-FAST to bypass the need for client certificates in the TLS handshake
    3. further authentication happen within the channel
- fast
    - because faster/more-seamless roaming between access points

### PEAP: server cert
- server-cert TLS channel + inner auth
- phases
    1. Authentication server presents a digital certificate to authenticate itself with the supplicant in the outer authentication
    2. Supplicant is satisfied with the identity of the AS
    3. Build a TLS tunnel to be used for the inner client authentication and encryption key exchange
- server is identified/authenticated by certificate with CA (outter auth)
- client is identified/authenticated by inner auth
    - client has no cert

### EAP-TLS: dual certs
- mutual-cert TLS channel
    - no username/password
    - user might need to login with username/password to get their cert (login to Laptop for example), but that is separate
- the most secure wireless auth method
- each wireless client must obtain and install a certificate
    - Public Key Infrastructure (PKI) could be used to
        - supply certs
        - revoke certs
    - need to use CA as PKI
