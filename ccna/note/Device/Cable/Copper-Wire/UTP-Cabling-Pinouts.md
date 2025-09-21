# UTP Cabling Pinouts

## RJ-45 Pinout for 10BASE-T and 100BASE-T
- Send on pins 1,2; receive on 3,6
    - PC NIC
    - Router
    - Wireless access point (Ethernet interface)
- Send on pin 3,6; receive on 1,2
    - Hub
    - Switch

### Samples:
- Host-Hub or Hub-Switch or Host-Switch or Switch-Router:
    - **straight-through cable pinout**
    - 1,2 to 1,2; 3,6 to 3,6
- Host-Host or Swith-Switch or Router-Router:
    - **crossover cable pinout**
    - 1,2 to 3,6; 3,6 to 1,2

## RJ-45 Pinout for 1000BASE-T; new pins are bi-directional
1000BASE-T is different because:
- it requires four wire pairs (instead of 2 pairs)
- it allows both ends to send/receive simultaneously on each wire pair

### straight-through cable pinout
- 1 to 1
- 2 to 2
- 3 to 3
- 4 to 4
- 5 to 5
- 6 to 6
- 7 to 7
- 8 to 8

### crossover cable pinout
- 1 to 3
- 2 to 6
- 3 to 1
- 4 to 4 (bi-directional)
- 5 to 5 (bi-directional)
- 6 to 2
- 7 to 7 (bi-directional)
- 8 to 8 (bi-directional)

## Auto-mdix
Cisco switches have a feature called auto-mdix that notices when the wrong cable is used
and automatically changes its logic to make the link work.
For CCNA exam, this feature does not exist by default.
