# STP

## Show Status
```
Switch#show spanning-tree ?
  active             Report on active interfaces only
  detail             Detailed information
  inconsistentports  Show inconsistent ports
  interface          Spanning Tree interface status and configuration
  summary            Summary of port states
  vlan               VLAN Switch Spanning Trees
  <cr>
```

## Entire Switch (2960) Config
```
Switch(config)#spanning-tree ?
  mode      Spanning tree operating mode
  portfast  Spanning tree portfast options
  vlan      VLAN Switch Spanning Tree

Switch(config)#spanning-tree mode ?
  pvst        Per-Vlan spanning tree mode
  rapid-pvst  Per-Vlan rapid spanning tree mode

Switch(config)#spanning-tree portfast ?
  bpduguard  Enable portfast bpdu guard on this switch
  default    Enable portfast by default on all access ports
Switch(config)#spanning-tree portfast bpduguard ?
  default  Enable bpdu guard by default on all portfast ports
```

## Per Interface Config
```
Switch(config-if)#spanning-tree ?
  bpduguard  Don't accept BPDUs on this interface
  cost       Change an interface's spanning tree port path cost
  guard      Change an interface's spanning tree guard mode
  link-type  Specify a link type for spanning tree protocol use
  portfast   Enable an interface to move directly to forwarding on link up
  vlan       VLAN Switch Spanning Tree

Switch(config-if)#spanning-tree guard ?
  root  Set guard mode to root guard on interface
```
