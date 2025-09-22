# Forwarding Architectures

## Architectures

### Centralized Forwarding
- with CPU (route processor)
- ingress line card --> switch fabric --> CPU --> switch fabric --> egress line card

### Distributed Forwarding
- avoid CPU
- ingress line card with forwarding engine --> switch fabric --> egress line card
    - no need going to switch fabric if the forwarding result is local line card

## Switching Algorithms
### Process Switching
- also named as Software Switching or Slow Path
- use general-purpose CPU
- fallback of CEF
- packets types for this method:
    - sourced/destined to the router itself
    - with IP options (too complex for hardware to handle)
    - with/require unknown information (e.g. unresolved ARP entries)

### Cisco Express Forwarding (CEF)
- Software CEF
    - Procedures: check FIB, check AIB, create CEF entry
        - if FIB not found, fallback to Slow Path
        - if AIB not found, invoke ARP process
        - with rate limiter and IP TTL applied
    - Forwarding Information Base (FIB)
        - next-hop IP addresses <--> network destination
        - populated from IP routing table
    - Adjacency Table (AIB)
        - directly connected next-hop IP/MAC addresses
        - populated from ARP or other L2 protocol table
- Hardware CEF

## Hardware Components
### TCAM
- TCAM seraching result is ternary (CAM is binary):
    - 0 for true
    - 1 for false
    - X for do not care
- TCAM entry is stored in Value-Mask-Result (VMR) format
    - Value --> field shoud be searched
        - such as, IP addr, protocol fields
    - Mask --> ???
    - Result --> action to do when a value-mask match happens
        - such as, allow/drop, flow to QoS policer
- Parallel hardware processing

### ASICs vs NPU
- ASICs (Application Specific Integrated Circuits)
    - not-programable
- Network Processing Units (NPU)
    - programable
    - easier firmware changing