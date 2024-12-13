### Assume a TCP connection already exists between PC1 and PC2. Which TCP message packet would be the final one to be sent between devices if both approve the connection termination?

- [ ] TCP-FIN
- [x] TCP-ACK
- [ ] TCP-FIN,ACK
- [ ] TCP-SYN, FIN

The normal termination sequence:
1. A segment with an ACK and FIN (terminating host to terminated host)
2. A segment with an ACK (terminated to terminating host)
3. A segment with an ACK and FIN (terminated host to terminating host)
4. A segment with an ACK (terminating host to terminated host)

