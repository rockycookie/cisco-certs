# Unstable Connection

## RF signal problems
- **[Unique]** Clients connect at low data rates only
    - indicating signal strength or quality degrades
- Signal strength decreases significantly a short distance from the AP
    - normal signal propagation should provide more gradual attenuation
- Multiple retransmissions seen in packet captures

## Co-channel interference
when multiple access points operate on the same wireless channel within overlapping coverage areas, causing RF contention and degraded performance

Symptoms:
- **[Unique]** Different client devices experience the same issues in the same location
- Signal strength decreases significantly a short distance from the AP
- Multiple retransmissions seen in packet captures

### What to do for 2.4GHz
- In the 2.4 GHz band, channels must be separated by at least 5 channels to achieve non-overlapping operation.
- North America uses channels 1, 6, and 11
