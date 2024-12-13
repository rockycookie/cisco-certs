### Which of the following behaviors are applied to a low latency queue in a Cisco router or switch? (Choose two answers.)
- [ ] Shaping
- [x] Policing
- [x] Priority scheduling
- [ ] Round-robin scheduling

Low Latency Queuing (LLQ) applies priority queue scheduling, always taking the next packet from the LLQ if a packet is in that queue. To prevent queue starvation of the other queues, IOS also applies policing to the LLQ. However, applying shaping to an LLQ slows the traffic, which makes no sense with the presence of a policing function already.
