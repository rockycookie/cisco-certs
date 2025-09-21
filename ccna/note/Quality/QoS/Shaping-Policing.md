# Shaping and Policing
Shapers and policers monitor the **traffic rate** (the bits per second that move through the shaper or policer) versus a configured shaping rate or policing rate <br/>

Does this next packet push the measured rate past the configured shaping rate or policing rate?
- If no,
    - do nothing
- If yes,
    - if shaping, delay the message by queuing it
    - if policing, either discard the message or mark it differently

## Policing
- policing makes sense only in certain cases, and as a general tool, it can be best used at the edge between two networks (ISP to their customers)
- key features
    - make sure traffic rate equal or below configured
    - allow for bursting after a period of inactivity
    - it is enabled on an interface, in either direction, but **typically at ingress**

## Shaping
- make sure traffic rate equal or below configured
- allow for bursting after a period of inactivity
- enabled on an interface for **egress** (outgoing packets)
