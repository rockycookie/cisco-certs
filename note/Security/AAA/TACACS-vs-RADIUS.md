# Application Protocols

- An authenticating device acts as a client talking to a AAA server
- The target where the access is asked for is called Network Access Device (NAD) or Network Access Server (NAS)

## TACACS+
- Terminal Access Controller Access-Control System Plus
- Cisco designed extension to TACACS that is described in RFC 8907
- TCP only, port 49
- modes
    - clear-text mode
    - encryption mode
        - entire packet body encrypted by MD5 (packet header clear-text)
- only for administrator access
- per-command authorization and auditing
- separates authentication, authorization, and accounting into distinct operations

## RADIUS
- normally UDP, ports 1812 and 1813
- encryption on password only
- end-user authentication
- supports session-level accounting, such as connection duration or data usage, but does not track specific user commands
