# RSTP

## Concepts
### Bridge ID (BID)
- 8-byte value unique to each switch
- 2-byte priority field and a 6-byte system ID
- the system ID is based on a universal (burned-in) MAC address in each switch
- lowest numeric BID --> root switch
    1. priority matters most
    2. system ID (MAC)

### BDPU (Bridge Protocol Data Unit)
- switches use it to exchange information with each other

#### Hello BDPU
- Root bridge ID
- Sender’s bridge ID
- Sender’s root cost
- Timer values on the root switch
    - Hello timer, MaxAge timer, and forward delay timer

<br/>

## How it works

### Terminologies

#### STP Cost
- simply an integer value assigned to each interface, per VLAN

#### RP Selection
- Sum of the costs of all the switch ports the frame would exit if it flowed over that path
    - ignore the costs of inbound-to-reach-root ports
    - calculated by adding Hello BDPU inbound port cost to the BDPU's root cost attribute
- Tiebreaker
    1. the lowest neighbor bridge ID
    2. the lowest neighbor port priority
    3. the lowest neighbor internal port number

#### DP Selection
- the lower-root-cost port (designated port, DP) in forwarding state
- Tiebreaker
    1. the lowest switch bridge ID
    2. the lowest switch port priority
    3. the lowest switch internal port number

#### Engineer config: BID
- set switch priority 
- default: 32768 ==  b1000,0000,0000,0000

#### Engineer config: Port cost
- default values, per port, per VLAN:
    - Ethernet type (Mbps): 10, 100, 1k, 10k, 100k, 1m
    - IEEE cost sicne 2004: 2m, 200k, 20k, 2k, 200, 20
- STP depends on the operating speed instead of the max speed

### Steps
1. STP/RSTP elects a root switch
    - all working ports (designated port, DP) in forwarding state
    - root switch per VLAN
    - steps:
        1. All switches claim to be the root by sending Hello BPDUs
        2. When receive Hello with lower BID, change to forward the superior Hello
2. Each nonroot switch finds the port with the least **root cost**
    - the port (root port, RP) in forwarding state
    - steps:
        1. Switches add their local interface STP/RSTP cost to the root cost listed in each received Hello BPDU
        2. Tiebreaker - neighbour switch's attribute
3. nonroot switches compare their root cost to the other-end switches over links (LAN segments)
    - the lower-root-cost port (designated port, DP) in forwarding state
    - tiebreaker - switch's own attribute
4. block all other working ports
    - Failed interfaces (for example, interfaces with no cable installed) or administratively shutdown interfaces are instead placed into an **disabled state**
