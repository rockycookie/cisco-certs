# Syslog
4.5 Describe the use of syslog features including facilities and levels

## Facilities
### See logs from console
- By default, IOS shows log messages to console users for all severity levels of messages
- To enable
    - `logging console` global config (default)
- To set log level:
    - `logging console {level-name | level-number}`

### See logs from SSH/Telnet
- To enable
    1. from target device, `logging monitor` global config
    2. from terminal
        - `terminal monitor` to start logging
        - `terminal no monitor` to stop logging
- To set log level:
    - `logging monitor {level-name | level-number}`

### See logs from RAM
- To enable
    - `logging buffered` global config
    - later login users can see old logs by `show logging buffered`
- To set log level:
    - `logging buffered {level-name | level-numbe}`

### See logs from Flash
- To enable 
    - `logging file` global config
    - later login users can see old logs by `show logging file`
- To set log level:
    - `logging file {level-name | level-numbe}`

### See logs from Syslog Server
- RFC 5424: syslog protocol, a device uses UDP to send messages to a syslog server for storage
- To config device to send to the server: 
    - `logging host {address | hostname}`
- To set log level:
    - `logging trap {level-name | level-number}`

## Levels
level-number: level-name
- 0: emergency
- 1: alert
- 2: critical
- 3: error
- 4: warning
- 5: notification
- 6: informational
- 7: debug

## `debug EXEC` command
```
R1# debug ip ospf hello
OSPF hello debugging is on

R1#
*Aug 10 13:38:19.863: OSPF-1 HELLO Gi0/1: Send hello to 224.0.0.5 area 0 from 172.16.1.1
*Aug 10 13:38:21.199: OSPF-1 HELLO Gi0/2: Rcv hello from 2.2.2.2 area 0 172.16.2.2
*Aug 10 13:38:22.843: OSPF-1 HELLO Gi0/2: Send hello to 224.0.0.5 area 0 from 172.16.2.1
```
