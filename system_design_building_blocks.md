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

**Cloud Services**:
- **AWS**: Application Load Balancer (ALB), Network Load Balancer (NLB), Classic Load Balancer, Gateway Load Balancer
- **Azure**: Azure Load Balancer, Application Gateway, Azure Front Door, Traffic Manager
- **GCP**: Cloud Load Balancing, HTTP(S) Load Balancer, Network Load Balancer, Internal Load Balancer
- **OCI**: Load Balancer, Network Load Balancer, Flexible Load Balancer

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

**Cloud Services**:
- **AWS**: Amazon API Gateway, AWS Application Load Balancer (for basic routing)
- **Azure**: Azure API Management, Azure Application Gateway, Azure Front Door
- **GCP**: Cloud Endpoints, API Gateway, Cloud Load Balancing
- **OCI**: API Gateway, Load Balancer (with routing rules)

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

**Cloud Services**:
- **AWS**: Amazon Route 53, AWS Global Accelerator
- **Azure**: Azure DNS, Azure Traffic Manager, Azure Private DNS
- **GCP**: Cloud DNS, Cloud CDN (DNS integration)
- **OCI**: DNS Zone Management, Traffic Management, Health Checks

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

**Cloud Services**:
- **AWS**: Amazon ElastiCache (Redis/Memcached), DynamoDB Accelerator (DAX), CloudFront (edge caching)
- **Azure**: Azure Cache for Redis, Azure CDN, Azure Front Door (caching)
- **GCP**: Cloud Memorystore (Redis/Memcached), Cloud CDN, Cloud Storage (caching)
- **OCI**: OCI Cache with Redis, Content Delivery Network

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

**Cloud Services**:
- **AWS**: Amazon CloudFront, AWS Global Accelerator
- **Azure**: Azure CDN (Microsoft/Verizon/Akamai), Azure Front Door
- **GCP**: Cloud CDN, Media CDN, Cloud Load Balancing (global)
- **OCI**: Content Delivery Network (CDN)

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

**Cloud Services**:
- **AWS**: Amazon RDS, Amazon DynamoDB, Amazon DocumentDB, Amazon Neptune, Amazon Redshift, Amazon Aurora
- **Azure**: Azure SQL Database, Cosmos DB, Azure Database for MySQL/PostgreSQL, Azure Synapse Analytics
- **GCP**: Cloud SQL, Cloud Firestore, Cloud Bigtable, Cloud Spanner, BigQuery
- **OCI**: Autonomous Database, MySQL Database Service, NoSQL Database, Database Migration Service

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

**Cloud Services**:
- **AWS**: AWS Lambda (serverless APIs), Amazon API Gateway, AWS App Runner, Elastic Beanstalk
- **Azure**: Azure Functions, Azure API Management, Azure App Service, Azure Container Apps
- **GCP**: Cloud Functions, Cloud Run, App Engine, Compute Engine
- **OCI**: Oracle Functions, API Gateway, Container Engine, Compute Service

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

**Cloud Services**:
- **AWS**: Amazon ECS, Amazon EKS, AWS Lambda, AWS Fargate, Amazon Service Mesh (App Mesh)
- **Azure**: Azure Kubernetes Service (AKS), Azure Container Instances, Azure Service Fabric, Azure Functions
- **GCP**: Google Kubernetes Engine (GKE), Cloud Run, Cloud Functions, Anthos Service Mesh
- **OCI**: Container Engine for Kubernetes (OKE), Container Instances, Oracle Functions

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

**Cloud Services**:
- **AWS**: AWS WAF, API Gateway throttling, AWS Shield, Application Load Balancer rate limiting
- **Azure**: Azure Front Door rate limiting, API Management policies, Azure DDoS Protection
- **GCP**: Cloud Armor, API Gateway quotas, Load Balancer rate limiting
- **OCI**: Web Application Firewall (WAF), API Gateway rate limiting, DDoS Protection

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

**Cloud Services**:
- **AWS**: Amazon S3, S3 Glacier, S3 Intelligent-Tiering, S3 One Zone-IA
- **Azure**: Azure Blob Storage, Azure Data Lake Storage, Azure Files
- **GCP**: Cloud Storage, Cloud Storage Nearline/Coldline/Archive
- **OCI**: Object Storage, Archive Storage, Data Transfer Service

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

**Cloud Services**:
- **AWS**: Amazon SQS, Amazon SNS, Amazon MQ, Amazon Kinesis, Amazon EventBridge
- **Azure**: Azure Service Bus, Azure Event Grid, Azure Event Hubs, Azure Queue Storage
- **GCP**: Cloud Pub/Sub, Cloud Tasks, Cloud Scheduler
- **OCI**: Queue Service, Streaming Service, Events Service, Notifications Service

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

**Cloud Services**:
- **AWS**: Amazon DynamoDB (auto-sharding), Amazon RDS (manual sharding), Amazon Aurora (sharding support)
- **Azure**: Azure Cosmos DB (automatic partitioning), Azure SQL Database (elastic pools), Sharded databases
- **GCP**: Cloud Spanner (automatic sharding), Cloud Bigtable (automatic sharding), Cloud SQL (manual sharding)
- **OCI**: Autonomous Database (sharding), MySQL Database Service (partitioning), NoSQL Database

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

**Cloud Services**:
- **AWS**: Amazon RDS Multi-AZ, RDS Read Replicas, DynamoDB Global Tables, Aurora Global Database
- **Azure**: Azure SQL Database geo-replication, Cosmos DB multi-region, SQL Managed Instance failover groups
- **GCP**: Cloud SQL read replicas, Cloud Spanner multi-region, Firestore multi-region
- **OCI**: Autonomous Database cross-region replication, MySQL Database Service replicas, Data Guard

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

**Cloud Services**:
- **AWS**: Amazon DynamoDB (built-in), Amazon ElastiCache for Redis (cluster mode), AWS Global Accelerator
- **Azure**: Azure Cosmos DB (automatic partitioning), Azure Cache for Redis (cluster mode)
- **GCP**: Cloud Bigtable (automatic sharding), Cloud Memorystore for Redis (cluster mode)
- **OCI**: NoSQL Database (automatic partitioning), OCI Cache with Redis (clustering)

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

**Cloud Services**:
- **AWS**: CloudWatch, AWS X-Ray, CloudTrail, Systems Manager, AWS Config, Personal Health Dashboard
- **Azure**: Azure Monitor, Application Insights, Log Analytics, Azure Security Center, Azure Sentinel
- **GCP**: Cloud Monitoring (Stackdriver), Cloud Logging, Cloud Trace, Cloud Profiler, Error Reporting
- **OCI**: Monitoring Service, Logging Service, Application Performance Monitoring, Management Agent

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
