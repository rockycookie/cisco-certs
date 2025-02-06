#  MPLS (MultiProrocol Label Switching)

- MPLS creates a WAN service that routes IP packets between customer sites
- MPLS VPNs allow the SP to build one large MPLS network, which also creates a private IP-based WAN for each of its customers
- the SP can separate the routes learned from one customer from the routes learned for the next customer; consequently, the SP can support each customer while preventing packets from leaking from one customer to the next

## Note
- MPLS VPNs create a private network by keeping customer data separate, but NOT by encrypting the data.
- While MPLS VPNs provide a Layer 3 service to customers, MPLS itself is sometimes called a Layer 2.5 protocol because it adds the MPLS header between the data-link header (Layer 2) and the IP header (Layer 3).

## Label Switching
- The routers on the edge of the MPLS network add and remove an MPLS header to packets as they enter and exit the MPLS network
- The devices inside the MPLS network then use the label field inside that MPLS header when forwarding data across the MPLS network

## Convention
- Customer edge router learn route with provider edge router using OSPF
- Provide edge router learn route with provider edge router using MP-BGP

## MPLS and QoS
- MPLS VPN supports VoIP with QoS
