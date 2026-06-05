# Control Plane Policing

## Notes
- A massive DDoS attack will still completely exhaust and saturate the physical port, CoPP is designed to protect the router's internal brain (the CPU), not the external pipe

## Order of Operations
1. Ingress Hardware Check: The physical port's hardware (ASIC/TCAM) inspects the packet destination. It realizes the packet is addressed to the router itself (e.g., an OSPF update, an SSH connection, or a Ping).
2. CoPP Evaluation (In Hardware): Before the ASIC forwards that packet up the internal bus to the CPU, it passes it through the CoPP filters
3. The Decision:
    - If the traffic is safe configured rate limit, the hardware forwards it up to the CPU
    - If the rate limit is exceeded, the hardware drops the packet right there on the line card
