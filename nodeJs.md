# Node JS

  -  Node.js is lightweight, event-driven, non-blocking, easy to scale horizontally, has fast I/O handling, and works well with API-driven architectures


-- Worker Threads, thread pool, clustering, gRPC, API versioning, distributed caching, Circuit breakers , Saga pattern, idempotency and schema/versioning


| Concept                 | When to Use                                |
| ----------------------- | ------------------------------------------ |
| **Worker Threads**      | CPU-heavy tasks                            |
| **Thread Pool**         | Node async operations automatically use it |
| **Clustering**          | Scale Node app across CPU cores            |
| **gRPC**                | Fast internal communication                |
| **API Versioning**      | Evolving public APIs safely                |
| **Distributed Caching** | Reduce DB load, boost performance          |
| **Circuit Breakers**    | Protect against slow/failing services      |
| **Saga Pattern**        | Multi-service business transactions        |
| **Idempotency**         | Payments, retries, event reprocessing      |
| **Schema Versioning**   | Evolving APIs & events                     |


## Worker Threads

  - Worker Threads allow Node.js to run CPU-intensive tasks in parallel without blocking the event loop.

  ### Use Cases

  - Crypto hashing
  - Image/PDF processing
  - Large JSON parsing
  - ML inference

## Thread Pool

- Node.js uses an internal libuv thread pool (default: 4 threads) for native async operations.

  ### Use Cases

  - File I/O
  - Crypto (pbkdf2, bcrypt)
  - Network I/O
  - Database queries
  - HTTP requests
  - DNS lookups
  - Increase pool size: `export UV_THREADPOOL_SIZE=64`

## Clustering
  - Allows Node.js to utilize multiple CPU cores by spawning multiple processes.
  - Clustering increases throughput for high-traffic microservices

## gRPC
  - gRPC is a high-performance, open-source universal RPC framework.
  - gRPC is language-neutral, platform-neutral, and based on HTTP/2.
  - gRPC is a modern, high-performance, open-source universal RPC framework.
  - gRPC is language-neutral, platform-neutral, and based on HTTP/2.

## API Versioning
  - URL Versioning (/api/v1/users, /api/v2/users)
  - Header Versioning (X-API-Version: 1.0.0)
  - Query Param Versioning (/users?version=2)

## Distributed Caching
  - Cache shared across microservices, usually **Redis / Memcached**
  - Used to reduce DB load & speed up responses

## Circuit Breakers
  - Prevent cascading failures in distributed systems
  - Implement fallbacks for failed services
  - Example: Hystrix, Resilience4j

## Saga Pattern
  - Pattern for managing distributed transactions across microservices without ACID.
  - Example: Order processing with payment, inventory, and shipping

## Idempotency
  - Ensures operations are repeatable without side effects
  - Example: Payment processing, event reprocessing

## Schema Versioning
  - Evolving APIs & events without breaking existing clients
  - Example: JSON Schema, Protocol Buffers

## Load Balancing
  - Distribute traffic evenly across microservices
  - Example: Round-robin, least connections, IP hash

## Service Discovery
  - Automatically find & connect to available services
  - Example: Consul, Eureka, Kubernetes

## Containerization
  - Package & run apps in isolated containers
  - Example: Docker, Kubernetes

## Microservices
  - Break monolithic apps into smaller, independent services
  - Example: Order service, inventory service, payment service

## Event Sourcing
  - Record changes to app state as a sequence of events
  - Example: Order placed, payment processed, inventory updated

## Event-driven Architecture
  - Use events to trigger actions in other services
  - Example: Order placed -> Payment processed -> Inventory updated

## Event
  - Record changes to app state as a sequence of events
  - Example: Order placed, payment processed, inventory updated

## Event-driven Architecture
  - Use events to trigger actions in other services
  - Example: Order placed -> Payment processed -> Inventory updated



# MongoDB 