# Why RSTP Rapid

## Why faster
- Shorter timer
    - RSTP defining MaxAge as 3 times the Hello timer (STP 10 times)
- Ask instead of waitting for timeout
    - With STP Listening state, the switches all tell each other (with BPDU messages) that the topology has changed and to **time out any MAC table entries** using the forward delay timer
    - RSTP switches tell each other (using messages) that the topology has changed, which makes
        - direct neighboring switches to **flush their MAC tables** to remove all the potentially loop-causing entries, without a wait
- Quickly repleace RP:
    - When
        - the root port fails
        - or Hellos stop arriving on the root port
    - no wait for timer, ports’ role and state:
        - root port ==> disabled port && forwarding ==> discarding
        - alt port ==> root port && forwarding
- Quickly replace DP:
    - With a backup port, if the current DP fails, the switch can start using the backup port immediately

## Terminologies

#### Alternate Port
- which becomes the root port if the root port ever fails
- to be an alternate port, both the RP and the alternate port must receive Hellos that identify the same root switch.

#### Backup Port
- switch-local backup port becomes designated port
- used mostly for hub LAN segments, not used much now


## Main idea
- RSTP adds a mechanism by which a switch can replace its root port, without any waiting to reach a forwarding state (in some conditions).
- RSTP adds a new mechanism to replace a designated port, without any waiting to reach a forwarding state (in some conditions).
- RSTP lowers waiting times for cases in which RSTP must wait for a timer.

### STP diff
- STP, the root switch creates a Hello, with all other switches updating and forwarding the Hello
- RSTP, each switch independently generates its own Hello
