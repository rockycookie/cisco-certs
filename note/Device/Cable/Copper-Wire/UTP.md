# Unshielded Twisted Pair (UTP) cabling.

An electrical circuit requires a complete loop, so the two nodes, using circuitry on their Ethernet ports, connect the wires in one pair to complete a loop, allowing electricity to flow.

## Encoding scheme
For example, 10BASE-T (10 Mbps) uses an encoding scheme that encodes a binary 0 as a transition from higher voltage to lower voltage during the middle of a 10^-7 second interval.

## Twisting solves physical transmission issue
Twisting the wire pairs together helps cancel out most of the EMI (electromagnetic interference).
EMI between wire pairs in the same cable is called crosstalk.

## Pieces breakdown

### RJ-45 Port on node/machine
- Network interface card (NIC) usually has it

### RJ-45 Connectors on the 2 ends of the cable
- 8 physical locations (pins) that can be inserted

### Cable with wires insight
The 10BASE-T and 100BASE-T standards require two pairs of wires,
while the 1000BASE-T standard requires four pairs

### Other port hardwares
- Gigabit Ethernet Interface Converter (GBIC): The original form factor for a removable transceiver for Gigabit interfaces; larger than SFPs
- Small Form Pluggable (SFP): The replacement for GBICs, used on Gigabit interfaces, with a smaller size, taking less space on the side of the networking card or switch.
- Small Form Pluggable Plus (SFP+): Same size as the SFP, but used on 10-Gbps interfaces. (The Plus refers to the increase in speed compared to SFPs.)
