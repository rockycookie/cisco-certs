# DNS

## Router Commands

- enable (default enabled)
    ```
    ip domain-lookup
    ```
- configure DNS server address
    ```
    ip name-server 192.168.1.53
    ```
- enabled the router itself to act as DNS
    ```
    ip dns server
    ```
- add hostname-ip mapping to the router itself
    ```
    ip host <hostname> <ip>
    ```
