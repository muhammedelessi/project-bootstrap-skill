# Scalability Planning

Scale from measured or credible workload constraints, not from fashion.

## Start with the workload

Characterize read/write ratio, request concurrency, traffic burstiness, dataset size and growth, expensive queries or CPU work, synchronous vs asynchronous requirements, and external dependency limits.

## Optimize the likely bottleneck first

Evaluate in this order when relevant:

1. Correct data model and indexes
2. Avoid unnecessary requests/work
3. Pagination/batching
4. Application and database connection limits
5. Caching for repeated safe reads
6. Background processing for work not required synchronously
7. Horizontal scaling
8. Service decomposition only when independent scale/ownership/deployment warrants it

## Capacity assumptions

For large projects, write down assumptions and the signal that triggers re-evaluation. Avoid fake precision when load tests or production measurements do not exist.

## Backpressure

For queues, uploads, imports, notifications, or expensive jobs define maximum concurrency, queue depth/lag signal, overload behavior, and retry/dead-letter handling when appropriate.

Never assume a queue solves overload if downstream capacity remains unbounded or invisible.
