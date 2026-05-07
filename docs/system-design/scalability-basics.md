# Scalability Basics

## Key Concepts

### Vertical vs Horizontal Scaling

| Type | What | Pros | Cons |
|---|---|---|---|
| Vertical | Bigger machine (more CPU/RAM) | Simple, no code change | Hardware limit, single point of failure |
| Horizontal | More machines | No limit, fault tolerant | Complex, need load balancer |

### CAP Theorem
> You can only guarantee **2 out of 3**: Consistency, Availability, Partition tolerance

| Pick | Sacrifice | Example |
|---|---|---|
| CP | Availability | MongoDB, HBase |
| AP | Consistency | Cassandra, DynamoDB |
| CA | Partition tolerance | Traditional RDBMS (not distributed) |

### Load Balancing
- **Round Robin** — simple, equal distribution
- **Least Connections** — route to least busy server
- **IP Hash** — same client → same server (sticky sessions)
- **Weighted** — powerful servers get more traffic

### Caching
- **Where:** Client → CDN → Load Balancer → App → DB
- **Strategies:**
  - **Cache-Aside** — app checks cache first, fetches DB on miss
  - **Write-Through** — write to cache + DB simultaneously
  - **Write-Behind** — write to cache, async flush to DB
- **Eviction:** LRU (most common), LFU, TTL

### Database

| SQL | NoSQL |
|---|---|
| Structured, ACID | Flexible schema, eventual consistency |
| Joins, complex queries | Horizontal scaling |
| PostgreSQL, MySQL | MongoDB, Cassandra, Redis |

- **Sharding** — split data across DBs by key (user_id % N)
- **Replication** — master-slave for read scaling
- **Indexing** — B-Tree (range), Hash (exact), speeds reads at write cost

### Message Queues
- Decouple producers and consumers
- Handle traffic spikes (buffer)
- Tools: Kafka, RabbitMQ, SQS

## Estimation Cheat Sheet

| Unit | Value |
|---|---|
| 1 day | ~86,400 seconds ≈ 10⁵ |
| 1 million requests/day | ~12 req/sec |
| 1 char | 1 byte (ASCII), 2 bytes (Unicode) |
| 1 image | ~200 KB |
| 1 MB | 10⁶ bytes |
| 1 GB | 10⁹ bytes |
| 1 TB | 10¹² bytes |

## My Notes
<!-- Add your own observations, mistakes, and learnings below -->
