# Rate Limiting

## DHCP
- Use interface subcmd:
    ```
    ip dhcp snooping limit rate <number of messages per second>
    ```
- Error recover, global cmd
    ```
    errdisable recovery cause dhcp-rate-limit
    errdisable recovery interval <seconds>
    ```

## ARP
- Use interface subcmd:
    ```
    ip arp inspection limit rate <number messages per second> [burst interval <seconds>]
    ```
    - burst interval: so that the rate limit can have logic like “x ARP messages over y seconds”
- Error recover, global cmd
    ```
    errdisable recovery cause arp-inspection
    errdisable recovery interval <seconds>
    ```
