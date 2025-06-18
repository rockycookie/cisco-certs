# First Hop Redundancy Protocols

## HSRP (Hot Standby Router Protocol)
- Cisco proprietary
- RFC 2281
- Need manual config for preempt (higher-priority router re-gain master after failover-then-reboot)
- 3-sec Hello timer

## VRRP (Virtual Router Redundancy Protocol)
- Open standard similar to HSRP
- RFC 2338
- auto-preempt
- 1-sec Hello timer

## GLBP (Gateway Load Balancing Protocol)
- Cisco proprietory
- Both redundancy and load balancing

## IRDP (ICMP Router Discovery Protocol)
