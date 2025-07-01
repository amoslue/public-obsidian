## Steps of system design
### 1. Understand the problem and establish design scope
- ask clarify questions
- functional/non-functional requirement
- QPS estumation
### 2. High-level design
- API
- Database
### 3. Low-level design (dive into each component)
### 4. Summary
- bottlenecks
- single point of failure
- replicas of the data if lost
- monitoring/alaert
- auto-fix/ticket


## Microservice main point
#### Technical Explanation

At a high level, microservices work by:

1. Service Independence: Each service runs as its own process and can be deployed independently
2. API Communication: Services communicate with each other through well-defined APIs, typically REST or gRPC
3. Database Isolation: Each service typically manages its own database, preventing direct database coupling
4. Independent Scaling: Services can be scaled independently based on their specific load requirements

In an interview, you should also be able to explain:

- Service Discovery: How services find and communicate with each other
- Data Consistency: How to maintain data consistency across services
- Fault Isolation: How failures in one service are contained and don't cascade to others

### Common non-functional requirement
- Performance: How fast does the system need to respond to user actions or process requests? This often includes defining acceptable latency thresholds for key operations like loading a user’s feed or posting a tweet.
- Availability: How consistently should the system be accessible to users? This could mean ensuring near 100% uptime through redundancy, failover mechanisms, and proactive monitoring.
- Scalability: Can the system handle increasing numbers of users, data, or traffic without a degradation in performance? Scalability can be both vertical (upgrading resources on a single server) and horizontal (adding more servers or instances). For large-scale systems, horizontal scalability is often preferred.
- Reliability: How well does the system handle failures? This includes designing for fault tolerance so that the system can recover from crashes or unexpected errors without losing functionality or data.
- Consistency: How accurately does the system reflect the same data across all users and operations? In systems with distributed databases, maintaining strong consistency can be challenging but critical for certain operations.
- Durability: How safely is data stored? This involves ensuring that data, once written, isn’t lost due to hardware failures, power outages, or other disruptions.
- Security: How well does the system protect against unauthorized access or attacks? This includes safeguarding sensitive user data and preventing exploits such as SQL injection or distributed denial-of-service (DDoS) attacks.
