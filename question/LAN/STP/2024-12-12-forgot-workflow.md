### Assuming all default STP settings, which of SW3's ports will become its root port, and what will its root cost be?
- [ ] Fa0/2, 19
- [x] Gi0/1, 8
- [ ] Gi0/1, 4
- [ ] Fa0/2, 8

Using the default port costs, a Gigabit Ethernet port will have a cost of 4 and a Fast Ethernet port will have a cost of 19. SW3 will have two interfaces that can be used to forward traffic to the root switch (SW4): through its Gi0/1 interface via SW1, which results in a total cost of 8, or via its Fa0/2 interface, which results in a total cost of 19. It will select the option with the lowest cost, so it will select its Gi0/1 interface as its root port with a cost of 8.
Summarizing the competing potential root paths and their costs:
- SW3 G0/1 - SW1 G0/3  - 4 + 4 = 8
- SW3 G0/1 - SW1 G0/1 - SW2 G0/2  - 4 + 4 + 4 = 12
- SW3 F0/2  - 19

<br/>

### The exhibit lists output from a switch. Which two statements are true?
```
S2# show spanning-tree vlan 30

VLAN0030
 Spanning tree enabled protocol rstp
 Root ID    Priority    24606
            Address     000c.309e.af81
            This bridge is the root
            Hello Time   2 sec  Max Age 20 sec  Forward Delay 15 sec

 Bridge ID  Priority    24606 (priority 24576 sys-id-ext 30)
            Address     000c.309e.af81
            Hello Time   2 sec  Max Age 20 sec  Forward Delay 15 sec
            Aging Time  300

Interface     Role  Sts    Cost      Prio.Nbr    Type
------------- ----  ---    --------- --------    ----------------------
Fa0/1         Desg  FWD    19        128.1       P2p
Fa0/3         Desg  FWD    19        128.3       P2p
Fa0/4         Desg  FWD    19        128.4       P2p
Fa0/6         Desg  FWD    19        128.6       P2p
```

- [x] All designated ports are in forwarding states.
- [ ] The switch is the root bridge for all the VLANS on this switch.
- [x] The bridge priority is lower than the default value for spanning-tree.
- [ ] There are 30 VLANs on this switch.


