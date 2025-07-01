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
![[Pasted image 20250701140456.png]]