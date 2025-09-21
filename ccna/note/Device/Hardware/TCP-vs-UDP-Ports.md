# Ports allocation

|             | TCP    | UDP      | comment                                                              |
|-------------|--------|----------|----------------------------------------------------------------------|
| HTTP        | 80     |          |                                                                      |
| HTTPS       | 443    |          |                                                                      |
| DNS         | 53     |          |                                                                      |
| SSH, Telnet | 22, 23 |          | SSH uses 22, Telnet uses 23                                          |
| TFTP        |        | 69       |                                                                      |
| NTP         |        | 123      | time synchronization communications between time servers and clients |
| SNMP        |        | 161, 162 | network device agent uses 161, NMS uses 162                          |
| Syslog      |        | 514      | UDP is preferred due to its low overhead                             |
