### Refer to the diagram; you have been tasked to help implement security measures for your company, which is going to place a number of public access computer terminals in its retail locations. Part of this process is securing the Ethernet ports that will be used by these terminals; this will be done by implementing Cisco’s port security feature on SW2 and SW3. Your boss wants to make sure that the ports are forced into a disabled state if another device is plugged into them. In this case, which port security violation mode should be configured on these ports?
- [ ] Protect
- [x] Shutdown
- [ ] Restrict
- [ ] Disable

There are three different port security violation modes: shutdown, restrict, and protect. <br/>
- The shutdown mode will disable a port if a device with an unauthorized MAC address attempts to send traffic.
- The restrict mode will ignore any traffic from unauthorized MAC addresses, log the violation, and send a message to the SNMP manager (if it is configured), but it will NOT disable the port.
- The protect mode will ignore any traffic from unauthorized MAC addresses, but it will not log the violation or send a message to the SNMP manager or disable the port.
