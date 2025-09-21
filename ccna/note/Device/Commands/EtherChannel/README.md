# EtherChannel
Comprises: a channel group + a port-channel interface
- channel group
    - binds physical ports to the port-channel interface
- port-channel interface

## To bind a phtsical interface
- `Switch(conf-if)# channel-group <etherchannel-id> mode [on|active|passive]`
    - to bind a physical port
    - for L2, create a new channel group if it does not exist

## To configure a port-channel interface
- `Switch(conf)# interface port-channel <etherchannel-id>`
    - `no switchport` to make it L3
    - `switchport ...` to configure L2 operations

## LACP
- to automatically create EtherChannels by exchanging LACP packets
- procedure
    1. learn the identity of LACP partners 
    2. dynamically group similarly configured ports into a single logical link
        - based on hardware, administrative, and port parameter constraints
    3. add the group to the spanning tree as a single device port
- mode active/passive
