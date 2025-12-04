# Traffic & Entry

## DNS Resolution (DNS)
- Translates human-readable domain names into IP addresses.
- Enables clients to locate servers by name rather than numeric addresses.
- Uses caching at multiple levels (browser, OS, ISP) to reduce lookup latency.
- Common types: A, AAAA, CNAME, MX, TXT, NS records.

## Content Delivery Network (CDN)
- Distributes content across geographically distributed servers.
- Reduces latency and load on origin servers.
- Improves redundancy and availability.

### Example: Digital Ocean CDN
- Edge caching of static assets.
- Integration with DigitalOcean Spaces (object storage).
- Automatic SSL via Let's Encrypt.
- Purge and versioning support.

## API Routing
- Directs incoming API traffic to appropriate backend services.
- Can apply rate limiting, authentication, and monitoring.
- Often integrated with load balancers or gateways (e.g., NGINX, Kong, Traefik).

---

# Load Balancer

## Core Functions
- **Health Checking:** Continuously monitors service instances, removing unhealthy nodes.
- **SSL Termination:** Decrypts HTTPS traffic at the load balancer to reduce backend overhead.
- **Session Persistence:** Ensures user sessions are directed to the same backend (sticky sessions).
- **Algorithms:**
  - Round Robin — evenly distributes requests.
  - IP Hash — routes clients based on IP for consistent sessions.

## Essential for
- **Horizontal Scalability:** Enables addition/removal of instances without downtime.
- **High Availability:** Routes around failures.
- **Zero-Downtime Deployments:** Gradually shifts traffic during rolling updates.

---

# Firewalls

## Network Firewalls (L3/L4)
- Protect network segments by filtering packets based on:
  - IP addresses
  - Ports
  - Protocols
- Perform **stateful inspection** to track active connections.
- Enforce inbound/outbound traffic policies.

## Application Firewalls (L7)
- Inspect HTTP/HTTPS payloads.
- Defend against web-specific attacks (SQLi, XSS).
- Often integrated with load balancers or API gateways.

---

# Containers

Lightweight, standalone units that package application code with all dependencies.

## Key Differences from Virtual Machines
- Share the host OS kernel.
- Significantly smaller footprint.
- Start in milliseconds.
- Provide process-level isolation rather than full OS virtualization.

## Benefits
- **Consistent Environments:** Identical dev, staging, and prod behavior.
- **Resource Efficiency:** Multiple containers share system resources efficiently.
- **Rapid Scaling:** Containers can be created or destroyed dynamically.

---

# Kubernetes Orchestration

Manages containerized applications at scale.

## Core Capabilities
- **Deployment Management:** Declarative definition of application state.
- **Scaling:** Auto-scaling based on CPU/memory or custom metrics.
- **Networking:** Internal service discovery via DNS; pod-to-pod communication.
- **Lifecycle Management:** Rolling updates, self-healing, restart policies.
- **Storage Integration:** Persistent Volumes and Claims for stateful workloads.

---

# Databases

## Relational Databases
- Use structured schemas with predefined tables and relationships.
- Ensure ACID properties (Atomicity, Consistency, Isolation, Durability).
- Common indexing structure: **B-Tree**.
- Examples: PostgreSQL, MySQL, MariaDB.

## Document Databases
- Store semi-structured data as JSON-like documents.
- Support nested and flexible data structures.
- Query via key paths and JSON operators.
- Examples: MongoDB, CouchDB.

## Key-Value Stores
- Optimized for high-speed retrieval by key.
- Minimal protocol overhead.
- Often memory-based with optional persistence.
- Examples: Redis, Memcached, RocksDB.

---

# MapReduce Algorithms

- Programming model for distributed data processing.
- Splits computation into **Map (filter/sort)** and **Reduce (aggregate)** phases.
- Enables parallel querying and analysis across large datasets.
- Used by systems like Hadoop and Spark for large-scale analytics.

**Benefits:**
- Scalable across many nodes.
- Fault-tolerant via job rescheduling.
- Suitable for batch processing and ETL pipelines.

---

# Graph Databases

- Model data as **nodes (entities)** and **edges (relationships)**.
- Ideal for **relationship-heavy** and **interconnected** data.
- Support complex traversals and queries (shortest path, community detection).
- Examples: Neo4j, ArangoDB, JanusGraph.

**Use Cases:**
- Social networks
- Recommendation systems
- Fraud detection
- Knowledge graphs

---
# Object Storage

Object storage is a system for managing data as discrete **objects** rather than files (file systems) or blocks (block storage). Each object contains the data itself, its metadata, and a unique identifier (UUID).

## Core Characteristics

- **Metadata and UUID**
  - Each object is assigned a unique identifier (UUID or hash).
  - Rich, customizable metadata describes the object (e.g., content type, creation date, tags).
  - Metadata is stored alongside the data, enabling flexible search and classification.

- **Flat Namespace**
  - No traditional folder or directory hierarchy.
  - Objects reside in a single logical namespace, typically grouped by “buckets” or “containers.”
  - Hierarchies can be emulated through naming conventions (e.g., prefixes like `images/2025/`).

- **Massive Scalability**
  - Designed for horizontal scaling across distributed clusters.
  - Handles petabytes to exabytes of data efficiently.
  - Supports parallel access and redundancy across multiple nodes or regions.

- **HTTP APIs**
  - Accessed via RESTful APIs using standard HTTP methods (`GET`, `PUT`, `DELETE`, `HEAD`).
  - Enables easy integration with web applications, automation, and cloud services.
  - Authentication and access control typically via tokens, keys, or signed URLs.

## Benefits

- Infinite scalability and high durability (through replication or erasure coding).
- Cost-effective storage for large unstructured datasets (images, logs, backups, media).
- Simplified management — no partitioning or filesystem limits.
- Global accessibility through standard web protocols.

