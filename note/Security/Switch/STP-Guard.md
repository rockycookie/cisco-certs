# Guarding Technologies for STP
References:
- https://www.cisco.com/en/US/docs/switches/datacenter/nexus5000/sw/configuration/guide/cli_rel_4_1/Cisco_Nexus_5000_Series_Switch_CLI_Software_Configuration_Guide_chapter13.html

## `spanning-tree guard`
- command: `switch(config-if)# spanning-tree guard {loop | root | none}`
- types:
    - root:
        - put a port into root-inconsistent (blocked) state if becoming a root port
    - loop:
        - blocking non-designated ports if BPDU (Bridge Protocol Data Unit) packets are not received

## `bpdufilter` and `bpduguard`
- prevent unauthorized devices from influencing the spanning tree
- commands
    - per-interface: `switch(config-if)# spanning-tree [bpdufilter|bpduguard] [enable|disable]`
    - global: `switch(config)# spanning-tree port type edge [bpdufilter|bpduguard] default`
        - port types:
            - `edge` ports are connected to hosts and can be either an access port or a trunk port
            - `network` ports are connected only to switches or bridges
            - `normal` ports can be connected to any type of device
- types:
    - `bpdufilter`
        - prevent a port from sending or receiving BPDUs
    - `bpduguard`
        - put a port into an error-disabled state once it receives a BPDU
