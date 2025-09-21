### Which options correctly list the addresses covered by the indicated address class?
- [x] Class B—addresses beginning with 128-191, inclusive
- [x] Class C—addresses beginning with 192–223, inclusive
- [ ] Class B—addresses beginning with 128-192, inclusive
- [ ] Class C—addresses beginning with 172–212, inclusive

<br/>

### A customer support rep at the help desk is working a problem. The problem record mentions address 172.16.1.1 and mask 255.255.254.0. At a lunch-and-learn session yesterday, the rep heard the network engineering team say that they avoided VLSM, and used only a single subnet mask in network 172.16.0.0. Which of the following answers is accurate regarding this implementation of network 172.16.0.0 and its subnetting plan?

- [ ] The network supports up to 256 subnets
- [x] The network supports up to 128 subnets
- [ ] The network supports up to 512 subnets
- [ ] Each subnet supports 126 hosts
- [x] Each subnet supports 254 hosts
- [ ] Each subnet supports 510 hosts

### The figure shows addressing for all the devices in a small lab network. PC1 can ping PC3. Which of the following statements accurately describes the allowed space for IP address growth in this design?
```
PC1: 10.4.4.4/23
R1: 10.4.4.200/23
R1: 192.168.18/30
R2: 192.168.17/30
R3: 172.25.25.25/28
PC3: 172.25.25.26/28
```
- [ ] The subnet that is used on the serial link allows for 4 additional valid IP addresses, but they are wasted, because no other IP addresses are needed beyond the 2 shown for the serial link.
- [x] With 2 IP addresses assigned, R3's LAN subnet allows for 12 additional IP addresses to be assigned.
- [ ] With 2 IP addresses assigned, R3's LAN subnet allows for 28 additional IP addresses to be assigned.
- [x] The R1 LAN subnet supports more than 300 host addresses.
- [ ] The R1 LAN subnet supports more than 600 host addresses.

### Which of the following IP addresses could be assigned to a host?
- [ ] 127.200.102.67/27
- [ ] 63.71.189.192/26
- [x] 207.87.255.133/28
- [ ] 42.16.8.11/30

- For the correct answer, IP address 207.87.255.133 is one of the IP addresses in subnet 207.87.255.128. This subnet has a range of addresses from 207.87.255.129 - 207.87.255.142, with 207.87.255.143 as the subnet broadcast address.
- Any address beginning with 127 is reserved.
- For 63.71.189.192/26, the number is a subnet number, with a range of valid address 63.71.189.- 193 through 63.71.189.254. 
- For 42.16.8.11/30, the number is subnet 42.16.8.8/30’s subnet broadcast address; this subnet has a range of valid IP addresses of 42.16.8.9 and 42.16.8.10
