# Integrity
- Message Integrity Check (MIC) is a security tool that can protect against data tampering

## WEP

## TKIP
- Temporal Key Integrity Protocol (TKIP)
- MIC 
    - it adds a hash value to each frame as a message integrity check to prevent tampering
- TKIP sequence counter
    - record of frames sent by a unique MAC address, to prevent frames from being replayed as an attack

## CBC-MAC used as MIC
- Cipher Block Chaining Message Authentication Code (CBC-MAC)
- from CCMP
- might not be supported by legacy devices

## GMAC used as MIC
- Galois Message Authentication Code (GMAC)
- from GCMP
