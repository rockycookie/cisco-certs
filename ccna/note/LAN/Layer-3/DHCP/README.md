# DHCP (Dynamic Host Configuration Protocol)

## DORA
It involves four key steps:
- DISCOVER
- OFFER
- REQUEST
    - also used for renew
- ACKNOWLEDGE

## Other states
- RELEASE
    - sent when a client voluntarily relinquishes its IP address lease before expiration, typically when shutting down gracefully
- DECLINE
    - sent when a client rejects a server's IP address offer, usually due to address conflicts detected through ARP checking
- INFORM is used by clients that have statically configured IP addresses but need additional configuration parameters from a DHCP server
