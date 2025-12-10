# Stateful Switchover (SSO)

SSO synchronize the
- router configuration
- line card operation
- Layer 2 protocol state information 
from the active RP to the standby RP

<br/>

- NSF (Nonstop Forwarding) 
    - frequently updates the FIB (Layer 3 control plane data) from the active to the standby RP.
    - NFS is part of SSO (can not be configured alone)
- GR (Graceful Restart)
    - deployed with SSO/NSF to protect the Layer 3 forwarding plane during an RP switchover
    - 3 categories
        - SSO/NSF-capable router
            - GR routing protocol extensions + SSO/NSF
        - GR-aware router
            - GR routing protocol extensions
        - GR-unaware router
            - nothing
- NSR (Nonstop Routing)
    - the active RP is responsible for constantly checkpointing all relevant routing control plane information to the standby RP, including routing adjacency and TCP sockets
    - There is no disruption to the routing protocol adjacencies, so the neighboring router does not need to be NSR-aware or GR-aware
    - Downside, it increases the workload on the router due to the constant checkpointing
