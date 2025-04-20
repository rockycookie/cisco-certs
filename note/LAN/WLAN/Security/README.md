# WLAN Security

|                 | Encryption | Authentication                             |
|-----------------|------------|--------------------------------------------|
| WPA Personal    | TKIP       | pre-shared key                             |
| WPA Enterprise  | TKIP       | RADIUS server                              |
| WPA2 Personal   | CCMP (AES) | pre-shared key                             |
| WPA2 Enterprise | CCMP (AES) | RADIUS server                              |
| WPA3 Personal   | CCMP (AES) | Simultaneous Authentication of Equals, SAE |
| WPA3 Enterprise | GCMP-256   | RADIUS server                              |

## Note
- Simultaneous Authentication of Equals (SAE)
    - a password-based authentication and key agreement method
    - it uses a secure key exchange protocol to establish a shared secret between the client and access point
    - Forward Secrecy --> even if an attacker compromises the password later, they cannot decrypt past traffic
    - Mutual Authentication --> ensures both the client and access point are verified
