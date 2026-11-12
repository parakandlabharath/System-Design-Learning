# System Design Interview Practice

Answer in your own words. Focus on the problem solved, how it works, and trade-offs.

## Questions and model answers

### 1. Difference between vertical and horizontal scaling?
Vertical scaling upgrades one machine. Horizontal scaling adds machines or instances and distributes workload.

### 2. Does a load balancer create more servers?
No. It routes traffic across available servers. Auto scaling can provision or remove instances.

### 3. What is a cache hit?
The requested item is found in the cache, avoiding a slower database read.

### 4. Does cache expiration delete permanent data?
No. It removes or invalidates the cached copy. The permanent record remains in its source database unless separately deleted.

### 5. Difference between replication and sharding?
Replication copies data to other nodes. Sharding divides a dataset into partitions stored on different nodes.

### 6. Why can a read replica return old data?
Replication may be asynchronous, so updates take time to reach the replica. This delay is replication lag.

### 7. Is replication a replacement for backups?
No. Deletions and corruption can replicate. Backups provide historical recovery points.

### 8. Difference between RPO and RTO?
RPO describes the acceptable data-loss window. RTO describes the target time to restore service.

### 9. Authentication vs authorization?
Authentication verifies identity; authorization checks permissions.

## Case study: leaderboard service
Imagine an online game with many players checking rankings.

A first-pass design:
1. Game clients call a leaderboard API.
2. A load balancer routes requests to healthy application instances.
3. The application authenticates the player and checks access permissions.
4. Frequently requested leaderboard snapshots may be cached with a freshness policy.
5. Durable player scores are stored in a database.
6. Read replicas may serve read-heavy queries; account for replication lag.
7. Backups and tested recovery procedures protect durable data.

Questions to investigate:
- How many players and requests are expected?
- Must rankings be real-time or can they be delayed?
- How are ties handled?
- Can users read stale rankings?
- How are fraudulent score submissions prevented?
- What are the RPO and RTO targets?

## Progress checklist
- [x] Explain vertical and horizontal scaling.
- [x] Explain load balancing and auto scaling.
- [x] Explain caching, TTL and invalidation.
- [x] Explain replication and failover.
- [x] Explain backup and recovery.
- [x] Explain sharding.
- [ ] Explain availability vs reliability.
- [ ] Design a rate limiter.
- [ ] Design a notification queue.
- [ ] Complete a system design interview walkthrough.
