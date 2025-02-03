# IPv6 Address Assignment

## Auto assignment
Every IPv6 host interface (and router interface) can create its own link-local address automatically, solving some initialization problems for hosts before they learn a dynamically learned global unicast address.

### Lik-local
Link-local addresses are used for:
- some overhead protocols that stay local to one subnet
- being the next-hop address for IPv6 routes.

#### How
1. Link-local address should always start with `FE80::/64`
2. The second half of the link-local address, in practice, can be formed
    - using EUI-64 rules (IOS default)
    - be randomly generated (Microsoft OS)
    - be manually configured
        - `ipv6 address {address} link-local` where address must be within range

<br/>

## Static assignment

### 128b IP assignment

### 64b IP assignment: EUI-64
(extended unique identifier) <br/>
The IPv6 address is {64-bit subnet prefix} appending {64-bit interface ID}

#### Subnet prefix
Configured

#### To get interface ID
1. Split 48-bit MAC address in 2 halves
2. Insert FFFE (16-bit) in between, so that total it is 64obit
3. Invert the 7th bit of the interface ID

Note, for interfaces that do not have a MAC address, like serial interfaces, the router uses the MAC of the lowest-numbered router interface that does have a MAC.

<br/>

## Dynamic assignment

### stateful DHCP
```
(config-if)# ipv6 address dhcp
```
- Dynamic learning on the address and prefix length using DHCP

### SLAAC
(Stateless Address Auto Configuration) <br/>

```
(config-if)# ipv6 address autoconfig
```

- Dynamic learning of the prefix and prefix length
- Calculate the interface ID using EUI-64 rules
