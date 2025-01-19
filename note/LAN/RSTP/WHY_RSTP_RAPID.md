# Why RSTP Rapid

## Terminologies

#### Alternate Port
- which becomes the root port if the root port ever fails
- to be an alternate port, both the RP and the alternate port must receive Hellos that identify the same root switch.

#### Backup Port
- local switch becomes designated port
- used mostly for hub LAN segments, not used much now


## Main idea
- RSTP adds a mechanism by which a switch can replace its root port, without any waiting to reach a forwarding state (in some conditions).
- RSTP adds a new mechanism to replace a designated port, without any waiting to reach a forwarding state (in some conditions).
- RSTP lowers waiting times for cases in which RSTP must wait for a timer.


RSTP defining MaxAge as 3 times the Hello timer (STP 10 times). 
Additionally, RSTP can send messages to the neighboring switch to inquire whether a problem has occurred.

### STP diff
- STP, the root switch creates a Hello with all other switches, updating and forwarding the Hello
- RSTP, each switch independently generates its own Hellos.
