# VPN

## Tunnel
### IPSec tunnel

## Hub and Spoke
### GRE over IPSec tunnel
- static tunnels between hub and spoke
- adding new branch/spoke NEEDS main-office/hub configuration change

### DMVPN (Dynamic Multipoint VPN, Cisco)
- single mGRE tunnel interface in the main office
- single IPSec profile to manager all spoke routers
- adding new branch/spoke does NOT need main-office/hub configuration change
