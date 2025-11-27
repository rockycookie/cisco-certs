# IKE (Internet Key Exchange)
- an auth protocol
    - two endpoints to establish security association (SA)
    - also known as IKE tunnels
    - used to carry control plane and data plane traffic for IPsec
- versions
    - IKEv1
        - some legacy infra uses it
    - IKEv2
        - EAP (certificate-based authentication)
        - anti-DoS
        - needs fewer msg to establish SA
- ISAKMP (Internet Security Association and Key Management Protocol)
    - UDP port 500
- IKE is an implementation of ISAKMP
    - using the Oakley and Skeme key exchange techniques
        - Oakley provides Perfect Forward Secrecy (PFS) for keys, identity protection, and authentication
        - Skeme provides anonymity, repudiability, and quick key refreshment
- For Cisco platforms, IKE == ISAKMP
- procedure in general
    1. DH to generate symmetric keys (different from the PSK)
    2. Authenticate each other
        - for PSK, session-specific hashes of PSK are exchanged
    3. Agree on IPsec parameters (encryption, hash, ...)
    4. Talk with the IPsec parameters

## IKEv1
- two phases of key negotiation
### Phase 1: establish ISAKMP SA, bidirectional
- modes
    - main mode
    - aggressive mode
        - faster
        -  the identities of the two peers trying to establish a AS are exposed to eavesdropping
- subjects
    - initiator
    - responder
- Main mode procedure
    1. MM1
        - initiator sends to the responder, proposals/offers of
            - hash alg: MD5/SHA
            - encryption alg: DES/3DES/AES
            - authentication method: pre-shared key / certificates
            - Diffie-Hellman group
            - lifetime
    2. MM2
        - responder to the initiator with the SA proposal that it matched
    3. MM3
        - initiator starts the DH key exchange
    4. MM4
        - responder sends its own key to the initiator
        - at this point, encryption keys have been shared
    5. MM5
        - initiator starts authentication by sending its IP address
    6. MM6
        - responder sends back a similar packet and authenticates the session
        - at this point, the ISAKMP SA is established
- Aggresive mode procedure
    1. AM1
        - initiator sends all the information contained in MM1, MM3, MM5
    2. AM2
        - responder sends all the information contained in MM2, MM4, MM6
    3. AMS
        - MM5

### Phase 2: establish IPsec SA, unidirectional
- Quick mode procedure
    1. QM1
        - initiator (either peer) can start multiple IPsec SAs in a single exchange message
        - contains phase-1-agreed encryption/integrity alg
    2. QM2
        - responder of matching IPsec parameters
    3. QM3
        - After this message, there should be two unidirectional IPsec SAs

<br/>

## IKEv2

- procedure
    1. IKE_SA_INIT
        1. reqeust
        2. response
    2. IKE_AUTH
        1. request
        2. response
    3. CREATE_CHILD_SA
        - IPsec SA (usually done in IKE_AUTH)
        - not always needed
