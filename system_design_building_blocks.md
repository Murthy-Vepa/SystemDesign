# Top 15 System Design Building Blocks - Detailed Guide

## 1. Load Balancer
**Purpose**: Distributes traffic across servers

**Detailed Explanation**:
- Acts as a reverse proxy that distributes incoming client requests across multiple backend servers
- Prevents any single server from becoming overwhelmed with requests
- Types include Layer 4 (transport layer) and Layer 7 (application layer) load balancers
- Algorithms: Round Robin, Least Connections, Weighted Round Robin, IP Hash
- Provides high availability by routing traffic away from failed servers
- Can perform health checks to monitor server status

**Use Cases**:
- Web applications with high traffic
- Microservices architectures
- Database clusters
- API endpoints

## 2. API Gateway
**Purpose**: Provides entry point for all client requests

**Detailed Explanation**:
- Single point of entry for all client requests to backend services
- Handles cross-cutting concerns like authentication, logging, rate limiting
- Routes requests to appropriate microservices
- Can perform request/response transformation
- Provides protocol translation (HTTP to gRPC, etc.)
- Implements security policies and API versioning

**Key Features**:
- Request routing and composition
- Authentication and authorization
- Rate limiting and throttling
- Request/response transformation
- Monitoring and analytics
- Caching

## 3. DNS (Domain Name System)
**Purpose**: Resolves domain names to IPs

**Detailed Explanation**:
- Translates human-readable domain names to IP addresses
- Hierarchical distributed naming system
- Types of DNS records: A, AAAA, CNAME, MX, TXT, NS
- DNS resolution process involves recursive and iterative queries
- Can be used for load distribution and failover
- TTL (Time To Live) controls caching duration

**DNS Resolution Process**:
1. Browser cache check
2. OS cache check
3. Router cache check
4. ISP DNS server query
5. Root nameserver query
6. TLD nameserver query
7. Authoritative nameserver query

## 4. Cache
**Purpose**: Reduces latency and load on database

**Detailed Explanation**:
- Temporary storage layer that stores frequently accessed data
- Significantly improves application performance
- Types: Client-side, CDN, Web server, Database, Application cache
- Cache strategies: Cache-aside, Write-through, Write-behind, Refresh-ahead
- Cache eviction policies: LRU, LFU, FIFO, Random
- Distributed caching solutions: Redis, Memcached, Hazelcast

**Cache Patterns**:
- **Cache-Aside**: Application manages cache directly
- **Write-Through**: Write to cache and database simultaneously
- **Write-Behind**: Write to cache first, database later
- **Refresh-Ahead**: Proactively refresh cache before expiration

## 5. CDN (Content Delivery Network)
**Purpose**: Delivers static content closer to users

**Detailed Explanation**:
- Geographically distributed network of proxy servers
- Caches static content (images, CSS, JavaScript, videos) closer to users
- Reduces latency by serving content from nearest edge location
- Offloads traffic from origin servers
- Provides DDoS protection and improved security
- Popular CDNs: CloudFlare, AWS CloudFront, Azure CDN

**Benefits**:
- Faster content delivery
- Reduced bandwidth costs
- Improved availability and redundancy
- Enhanced security features
- Better user experience globally

## 6. Database
**Purpose**: Stores and retrieves data efficiently

**Detailed Explanation**:
- Persistent storage system for application data
- Types: Relational (SQL) and Non-relational (NoSQL)
- ACID properties for relational databases: Atomicity, Consistency, Isolation, Durability
- NoSQL types: Document, Key-Value, Column-family, Graph
- Database optimization: Indexing, query optimization, connection pooling
- Backup and recovery strategies

**Database Types**:
- **SQL**: MySQL, PostgreSQL, Oracle, SQL Server
- **NoSQL Document**: MongoDB, CouchDB
- **Key-Value**: Redis, DynamoDB
- **Column-family**: Cassandra, HBase
- **Graph**: Neo4j, Amazon Neptune

## 7. APIs (Application Programming Interfaces)
**Purpose**: Enables communication between clients and servers

**Detailed Explanation**:
- Set of protocols and tools for building software applications
- Defines how different software components should interact
- Types: REST, GraphQL, gRPC, SOAP
- RESTful principles: Stateless, cacheable, uniform interface
- API design best practices: versioning, documentation, error handling
- Authentication methods: API keys, OAuth, JWT

**API Design Principles**:
- Consistency in naming conventions
- Proper HTTP status codes
- Clear error messages
- Comprehensive documentation
- Rate limiting and throttling
- Security considerations

## 8. Microservices
**Purpose**: Breaks monolith into independent services

**Detailed Explanation**:
- Architectural approach that structures application as collection of loosely coupled services
- Each service is independently deployable and scalable
- Services communicate via well-defined APIs
- Enables technology diversity and team autonomy
- Requires sophisticated deployment and monitoring
- Challenges: Distributed system complexity, data consistency

**Microservices Patterns**:
- Service discovery
- Circuit breaker
- API gateway
- Database per service
- Saga pattern for distributed transactions
- Event sourcing and CQRS

## 9. Rate Limiter
**Purpose**: Controls request flow from clients

**Detailed Explanation**:
- Mechanism to control the rate of requests sent or received
- Prevents abuse and ensures fair usage of resources
- Algorithms: Token bucket, Leaky bucket, Fixed window, Sliding window
- Can be implemented at different layers: client, load balancer, API gateway
- Helps prevent DDoS attacks and resource exhaustion
- Returns appropriate HTTP status codes (429 - Too Many Requests)

**Rate Limiting Algorithms**:
- **Token Bucket**: Tokens added at fixed rate, consumed per request
- **Leaky Bucket**: Requests processed at steady rate
- **Fixed Window**: Counter resets at fixed intervals
- **Sliding Window**: More accurate than fixed window

## 10. Object Storage
**Purpose**: Stores large objects like images and files

**Detailed Explanation**:
- Scalable storage architecture for unstructured data
- Data stored as objects with metadata in flat address space
- Highly scalable, durable, and cost-effective
- Accessed via RESTful APIs
- Examples: Amazon S3, Google Cloud Storage, Azure Blob Storage
- Use cases: Backup, content distribution, data archiving, static websites

**Object Storage Features**:
- Unlimited scalability
- High durability (99.999999999% for S3)
- Versioning and lifecycle management
- Access control and encryption
- Event notifications
- Cross-region replication

## 11. Message Queue
**Purpose**: Enables async communication

**Detailed Explanation**:
- Middleware that enables asynchronous communication between services
- Decouples producers and consumers of messages
- Provides reliability through message persistence
- Patterns: Point-to-point, Publish-Subscribe
- Features: Message ordering, delivery guarantees, dead letter queues
- Examples: RabbitMQ, Apache Kafka, Amazon SQS, Apache ActiveMQ

**Messaging Patterns**:
- **Producer-Consumer**: Direct message passing
- **Publish-Subscribe**: One-to-many message distribution
- **Request-Response**: Synchronous-like communication over async transport
- **Message Routing**: Conditional message delivery

## 12. Sharding
**Purpose**: Splits data across databases

**Detailed Explanation**:
- Horizontal partitioning technique that distributes data across multiple databases
- Each shard contains subset of total data
- Improves performance and enables horizontal scaling
- Sharding strategies: Range-based, Hash-based, Directory-based
- Challenges: Cross-shard queries, rebalancing, complexity
- Requires careful planning of shard keys

**Sharding Strategies**:
- **Horizontal Sharding**: Split rows across databases
- **Vertical Sharding**: Split columns/tables across databases
- **Functional Sharding**: Split by feature/service
- **Hash-based**: Use hash function on shard key
- **Range-based**: Split by ranges of shard key values

## 13. Replication
**Purpose**: Improves availability and fault tolerance

**Detailed Explanation**:
- Process of copying data across multiple database servers
- Types: Master-Slave, Master-Master, Cascading replication
- Synchronous vs Asynchronous replication
- Provides high availability and disaster recovery
- Enables read scaling by distributing read queries
- Considerations: Consistency, latency, failover procedures

**Replication Types**:
- **Master-Slave**: One write node, multiple read replicas
- **Master-Master**: Multiple write nodes with conflict resolution
- **Synchronous**: Waits for replica confirmation
- **Asynchronous**: Doesn't wait for replica confirmation

## 14. Consistent Hashing
**Purpose**: Distributes data efficiently

**Detailed Explanation**:
- Distributed hashing scheme that operates independently of number of servers
- Minimizes remapping when servers are added or removed
- Uses hash ring concept with virtual nodes
- Provides good load distribution and fault tolerance
- Used in distributed systems like Amazon DynamoDB, Apache Cassandra
- Solves the rehashing problem in traditional hashing

**Consistent Hashing Benefits**:
- Minimal data movement during scaling
- Even load distribution
- High availability
- Fault tolerance
- Scalability without major disruptions

## 15. Monitoring System
**Purpose**: Tracks health and performance

**Detailed Explanation**:
- Comprehensive system for tracking application and infrastructure metrics
- Collects, processes, and visualizes performance data
- Components: Metrics collection, alerting, dashboards, logging
- Key metrics: Response time, throughput, error rates, resource utilization
- Tools: Prometheus, Grafana, ELK stack, DataDog, New Relic
- Enables proactive issue detection and resolution

**Monitoring Components**:
- **Metrics**: Quantitative measurements over time
- **Logs**: Discrete events with timestamps
- **Traces**: Request flow through distributed systems
- **Dashboards**: Visual representation of system health
- **Alerting**: Automated notifications for anomalies
- **SLOs/SLIs**: Service level objectives and indicators

## Integration and Best Practices

These building blocks work together to create robust, scalable systems:

1. **Start Simple**: Begin with monolithic architecture, evolve to microservices as needed
2. **Design for Failure**: Implement redundancy, circuit breakers, and graceful degradation
3. **Monitor Everything**: Comprehensive monitoring from day one
4. **Security First**: Implement security at every layer
5. **Documentation**: Maintain clear documentation for all components
6. **Testing**: Implement comprehensive testing strategies
7. **Gradual Migration**: When migrating between architectures, do it incrementally

Understanding and properly implementing these building blocks is crucial for designing systems that can handle scale, provide reliability, and deliver excellent user experiences.