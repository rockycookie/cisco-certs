# Classful IPv4

## Class A - large network unicast
### [b0000 0000 to b1000 0000) ---> [0,128) + 127 excluding 0 and 127
- First octet range 1-126
    - 0 and 127 are reserved
- Valid network numbers:
    <details>

    - 1.0.0.0
    - 2.0.0.0
    - ...
    - 126.0.0.0
    </details>
- Total network: 2^7 - 2 = 126
    - 1.0.0.0 to 126.0.0.0 / 8
    - 0(000 0001).0.0.0 to 0(111 1101).0.0.0 / 8
- Hosts per network:
    - 2^24 - 2
- Bits in network part: 8
- Bits in host part: 24
- Default mask: 255.0.0.0

## Class B - medium-sized network unicast
### [b1000 0000 to 1100 0000) ---> [128 - 192) + 61
- First octet range 128-191
- Valid network numbers:
    <details>

    - 128.0.0.0
    - 128.1.0.0
    - ...
    - 128.255.0.0
    - 129.0.0.0
    - 129.1.0.0
    - ...
    - 191.0.0.0
    - ...
    - 191.255.0.0
    </details>
- Total network:
    - (191 - 128 + 1) * 2^8 = 16,384
    - 2^14
        - 128.0.0.0 to 191.0.0.0
        - 10(00 0000).0.0.0 to 10(11 1111).0.0.0 / 16
        - 6 + 8 = 14 bits
- Hosts per network:
    - 2^16 - 2
- Bits in network part: 16
- Bits in host part: 16
- Default mask: 255.255.0.0

## Class C - small network unicast
### [b1100 0000 to b1110 0000) ---> [192, 224) + 31
- First octect range 192 - 223
- Valid network numbers:
    <details>

    - 192.0.0.0
    - 192.0.1.0
    - ...
    - 192.0.255.0
    - 192.1.0.0
    - 192.1.1.0
    - ...
    - 192.1.255.0
    - ...
    - 192.255.255.0
    - 193.0.0.0
    - 193.0.1.0
    - ...
    - 223.255.255.0
    </details>
- Total network:
    - 192.0.0.0 to 223.255.255.0 / 24
    - 110(0 0000).0.0.0 to 110(1 1111).255.255.0 / 24
    - 2^5*2^16 = 2^21 = 2,097,152
- Hosts per network:
    - 2^8 - 2
- Bits in network part: 24
- Bits in host part: 8
- Default mask: 255.255.255.0

## Class D - multicasting
### [b1110 0000 to b1111 0000) ---> [224, 240) + 15

## Class E - research purpose
### [b1111 0000 to b1111 1111] ---> [240, 240] + 15
