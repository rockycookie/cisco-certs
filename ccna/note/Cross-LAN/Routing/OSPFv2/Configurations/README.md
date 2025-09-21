# Configuration Examples

Note taking from the OSPF section of
- https://www.cisco.com/c/en/us/tech/ip/ip-routing/tech-configuration-examples-list.html

## Quick notes
- Network Type POINT_TO_POINT by default on serial interfaces
    - encapsulation
        - HDLC by default
        - `encapsulation ppp`
    - verification
        - `show ip ospf neighbor` --> State `FULL/ -`
        - `show ip ospf interface serial 0` --> `Network Type POINT_TO_POINT`
