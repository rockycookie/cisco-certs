# IPv6

## Connected and Local Route
1. The router looks for any configured **unicast addresses** on any
interfaces by looking for the `ipv6 address` command
2. Skip if interface does NOT have a “line status is up, protocol status is up” notice in the output of the `show interfaces` command
3. The router adds both a connected and local route


Note, Routers do not create connected or local IPv6 routes for link-local addresses.

