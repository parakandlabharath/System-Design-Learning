# Data, Caching and Resilience

## Caching
A cache stores data temporarily so repeated reads can be served faster and with less load on the primary data store. A game may cache frequently requested public profiles or leaderboard snapshots.

- Cache hit: requested data is present in the cache.
- Cache miss: data is absent; the application retrieves it from a slower source.
- TTL: how long an entry may remain valid.
- Eviction: removing entries to free cache space.
- Invalidation: marking or removing data that is no longer valid.

A cache is usually a performance layer, not the permanent source of truth. Expiring a cache entry does not delete the original database record.

## Common cache strategies
- Cache-aside: application checks cache; on a miss, reads the database and populates the cache.
- Write-through: application writes through the cache, which updates the backing store as part of the write path.
- Write-behind: cache accepts writes and persists them asynchronously; durability needs careful design.

Cache invalidation and stale data are important challenges.

## Database replication
Replication copies data from one database node to another. In a primary/replica model, writes commonly go to the primary and replicas receive copied changes. Read traffic may be served by replicas.

Replication lag means a replica may temporarily be behind the primary. Applications must account for this when users expect to read their latest write.

## Failover
Failover switches service to a healthy standby or replica when the primary fails. Safe failover requires health detection, promotion rules, connection handling, and protection against split-brain.

Replication is not the same as backup: accidental deletion or corruption can also replicate.

## Backup and recovery
Backups preserve recoverable copies of data.
- RPO (Recovery Point Objective): acceptable amount of data loss measured in time.
- RTO (Recovery Time Objective): target time to restore service.
- Define backup frequency, retention, encryption, access controls, off-site copies, and regular restore tests.

A Git remote can help restore committed and pushed source code. It does not automatically back up uncommitted files, production databases, secrets, uploaded user data, or the runtime environment.

## Database sharding
Sharding partitions a dataset across multiple database nodes. Each shard stores a subset of records, often selected by a shard key such as user ID.

Replication copies data; sharding splits data.

Sharding can increase storage and write capacity, but adds complexity: shard-key selection, hot shards, cross-shard queries, rebalancing, and transactions.

## Quick comparison

| Technique | Main purpose |
|---|---|
| Cache | Faster repeated reads / lower DB load |
| Replication | Copies data for read scale or redundancy |
| Sharding | Splits data across nodes |
| Backup | Recover data after loss or corruption |
| Failover | Switch to a healthy component after failure |
| Load balancing | Distribute incoming requests |
| Auto scaling | Adjust instance count with demand |
