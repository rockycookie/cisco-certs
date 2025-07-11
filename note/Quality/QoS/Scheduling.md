# Scheduling

## Low Latency Queuing (LLQ)
- always send message from this queue
- scheduler never services the other queues (called queue starvation)

## Class-Based Weighted Fair Queuing (CBWFQ)
- ensure different traffic classes receive guaranteed bandwidth

## Weighted Random Early Detection (WRED)
- selectively drop packets before a queue becomes full
