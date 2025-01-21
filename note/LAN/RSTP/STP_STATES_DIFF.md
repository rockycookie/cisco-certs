# STP vs RSTP diff

## States definition

| Function                                                            | STP State  | RSTP State |
|---------------------------------------------------------------------|------------|------------|
| Port disabled administratively                                      | Disabled   | Discarding |
| Stable state that ignores incoming (and not forwarding) data frames | Blocking   | Discarding |
| Interim state without MAC learning nor forwarding                   | Listening  | n/a        |
| Interim state with MAC learning but no forwarding                   | Learning   | Learning   |
| Stable state that allows both MAC learning and forwarding           | Forwarding | Forwarding |

- With STP Listening state, the switches all tell each other (with BPDU messages) that the topology has changed and to **time out any MAC table entries** using the forward delay timer
- RSTP switches tell each other (using messages) that the topology has changed. Those messages also 
    - direct neighboring switches to **flush their MAC tables** to remove all the potentially loop-causing entries, without a wait
