### With a pair of Cisco routers, how does the receiver of an HDLC frame know what has been encapsulated within that frame?

- [ ] HDLC only encapsulates IPv4
- [ ] Based on the FCS field
- [ ] From the IP address (IPv4, IPv6, and so on)
- [x] The Type field in the header
- [ ] Based on the Flag field

Explain:
- In the HDLC header, the Type field indicates the type of Layer 3 packet encapsulated within the HDLC Layer 2 frame.
HDLC can encapsulate many different types of protocols, not just IPv4. 
- The FCS field is used for error detection.
- The Flag field is similar to an Ethernet preamble, which is a specific bit pattern that allows a receiving device to realize that a new frame is arriving.
- The IP address is in the L3 header, not in the HDLC header. 
