# WPAs

| Encryption \ MIC | TKIP | CCMP      | GCMP |
|------------------|------|-----------|------|
| TKIP             | WPA  |           |      |
| AES              |      | WPA, WPA2 | WPA3 |

- All WPAs support auth with both Pre-Shared Keys and 802.1x

|                 | Authentication                              |
|-----------------|---------------------------------------------|
| WPA Personal    | pre-shared key                              |
| WPA2 Personal   | pre-shared key                              |
| WPA3 Personal   | Simultaneous Authentication of Equals (SAE) |
| WPA Enterprise  | RADIUS server                               |
| WPA2 Enterprise | RADIUS server                               |
| WPA3 Enterprise | RADIUS server                               |

## Note
- Simultaneous Authentication of Equals (SAE)
    - a password-based authentication and key agreement method
    - it uses a secure key exchange protocol to establish a shared secret between the client and access point
    - Forward Secrecy --> even if an attacker compromises the password later, they cannot decrypt past traffic
    - Mutual Authentication --> ensures both the client and access point are verified