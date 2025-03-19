# QoS Queuing

## Components of queuing system
- Classifier (QoS marking or others)
- Queues
- Scheduler (which queue item goes to interface to be sent)

## Scheduler scheduling
- Round-Robin Scheduling
    - Weighted Round-Robin Scheduling
    - routers use a popular tool called Class-Based Weighted Fair Queuing (CBWFQ) to guarantee a minimum amount of bandwidth to each class
- Low Latency Queuing
    - RR is not good at low latency (low delay), low jitter, and low loss
    - treat one or more queues as special priority queues. The LLQ scheduler always takes the next message from one of these special priority queues