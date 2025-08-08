# Scheduling

## Methods
### Low Latency Queuing (LLQ)
- always send message from this queue
- scheduler never services the other queues (called queue starvation)

### Class-Based Weighted Fair Queuing (CBWFQ)
- ensure different traffic classes receive guaranteed bandwidth
- Weighted Round-Robin Scheduling

### Weighted Random Early Detection (WRED)
- selectively drop packets before a queue becomes full

## Components of queuing system
- Classifier (QoS marking or others)
- Queues
- Scheduler (which queue item goes to interface to be sent)
