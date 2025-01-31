# IPv6 Address Assignment

## Static assignment

## Dynamic assignment

### DHCP

### SLAAC
(Stateless Address Auto Configuration) <br/>

### EUI-64
(extended unique identifier) <br/>
The IPv6 address is {64-bit subnet prefix} appending {64-bit interface ID}

#### Subnet prefix
Configured

#### To get interface ID
1. Split 48-bit MAC address in 2 halves
2. Insert FFFE (16-bit) in between, so that total it is 64obit
3. Invert the 7th bit of the interface ID
