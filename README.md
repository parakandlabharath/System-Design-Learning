# System Design Learning

A practical study journal for understanding how software systems are structured, scaled, protected, and operated. Examples use familiar applications such as an online game, shopping app, and student portal.

## Roadmap

| Concept | Status |
|---|---|
| Client, server, API and database | Foundation |
| Authentication vs authorization | Covered |
| Vertical vs horizontal scaling | Covered |
| Load balancing | Covered |
| Auto scaling | Covered |
| Caching and invalidation | Covered |
| Database replication and failover | Covered |
| Backup and recovery | Covered |
| Database sharding | Covered |
| Availability and reliability | Next |
| Rate limiting and queues | Planned |
| System design case studies | Planned |

## Contents
- docs/core-concepts.md
- docs/data-and-resilience.md
- practice/interview-practice.md

## Conceptual request flow

    User / Client
          |
          v
      API Entry
          |
          v
     Load Balancer
          |
          v
   Application Servers
       |         |
       v         v
     Cache    Database
                  |
                  v
             Read Replicas

Real architectures vary with traffic, consistency, security, cost, and product requirements.

## Study method
For each concept, explain the problem it solves, how it works, its trade-offs, where it fits, and what can fail.
