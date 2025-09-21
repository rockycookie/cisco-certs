# Designated Port Selection

## Context
- designated ports are selected to prevent network loops
- select one between the two port in a link

## Tie Breaker

### 1. Lowest Root Path Cost
- The root path cost is calculated by adding the individual port costs along the path from a non-root switch to the root bridge

### 2. Lowest Bridge ID (BID)
- The BID is a combination of 
    1. a **switch priority value** (default is 32768)
    2. the switch's MAC address

### 3. Lowest Port ID
- The port ID is a combination of 
    1. a 4-bit **port priority value** (default is 128)
    2. a 12-bit interface ID
