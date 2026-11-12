# Core System Design Concepts

## What is system design?
System design defines components, responsibilities, data flow, interfaces, and operational behavior needed to meet product requirements.

Start with:
- Functional requirements: what the system must do.
- Non-functional requirements: performance, availability, security, scalability, reliability, and cost.
- Constraints: users, traffic, data size, latency, budget, and technology.

## Client, server, API and database
- Client: application used by a customer, such as a browser or mobile app.
- Server: receives requests and runs application logic.
- API: agreed interface through which components communicate.
- Database: stores data for later retrieval and updates.

Example: a game client sends a score to an API. The server validates the player and score before storing the result.

## Authentication vs authorization
- Authentication verifies who a user or service is.
- Authorization determines what that identity is allowed to do.
Example: login verifies a player; checking whether that player can access an admin-only control is authorization.

## Vertical scaling
Increase resources of one server, such as CPU, RAM, or storage.
Advantages: simple to reason about and may require fewer application changes.
Trade-offs: hardware limits, upgrade cost, and a larger single failure point.

## Horizontal scaling
Add more server instances and distribute work.
Advantages: can increase capacity and improve fault tolerance when designed correctly.
Trade-offs: needs traffic distribution, health checks, and attention to shared state and data consistency.

## Load balancing
A load balancer distributes incoming requests across available application instances. Health checks can prevent traffic from going to unhealthy instances.
It does not create servers. Auto scaling can add or remove instances; load balancing distributes requests among them.

## Auto scaling
Automatically adjusts the number of running instances based on signals such as CPU utilization, request count, or queue depth. Policies need sensible thresholds, cooldowns, and capacity limits.

## High availability
High availability aims to keep a service usable despite component failures. Techniques include multiple instances, health checks, redundancy, failover, and deployment across failure zones.
More instances alone do not guarantee high availability: shared databases, networks, and configuration can still be single points of failure.
