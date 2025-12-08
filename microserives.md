# Micro Services

  - A microservice is an independently deployable, loosely coupled service that owns a single business capability.
  - **Benefits:** scalability, independent deployments, fault isolation, technology freedom, smaller codebases.
  - **Trade-offs:** complexity, distributed systems issues, observability, latency.

## Microservices communication
  - **Synchronous:** REST, gRPC, GraphQL.
  - **Asynchronous:** Kafka, RabbitMQ, SQS/SNS, Redis Streams.
  - Node.Js microservices can be communicated through 
      - REST using axios, fetch, or Node’s http module
      - gRPC using protobuf
      - Event-based messaging via Kafka/RabbitMQ (retries, timeouts, circuit breakers, correlation IDs.)

  1. Two high-level approaches
    - **Synchronous:** REST, gRPC, GraphQL.
    - **Asynchronous:** Kafka, RabbitMQ, SQS/SNS, Redis Streams.
  2. Protocols & formats
    - **HTTP/REST + JSON** — ubiquitous, human-readable, easy to debug.
    - **gRPC + Protobuf** — binary, faster, strongly typed; great for high-throughput internal RPC.
    - **Message brokers** — Kafka, RabbitMQ, Pulsar for streaming / pub-sub.
    - **GraphQL** — for aggregating several services into one query endpoint (API gateway).
    - **Formats** - JSON (simple), Protobuf/Avro (compact, schema evolution).

## Design a REST API in a microservices architecture
  - proper resource modelling
  - versioning (v1, v2)
  - idempotency
  - pagination
  - error-handling standard (problem+json)
  - rate-limiting & throttling
  - observability

## service discovery
  - Microservices are dynamic (scaling, restarting), so they cannot rely on static URLs.
  - Service discovery (Consul, Eureka, Kubernetes DNS) helps services find each other dynamically.

## Handle API gateway pattern in Node.js
  - Use Nginx, Kong, Express Gateway, or custom Node.js gateway with:
      - Authentication
      - Routing
      - Aggregation
      - Rate limiting
      - Caching
      - Logging
      - Circuit breaking

## Secure microservices in Node.js
  - mTLS between services
  - OAuth2 / JWT
  - RBAC/ABAC
  - Input validation
  - Avoid secrets in code (use Vault, KMS)
  - Rate-limiting + API gateway protections

## Circuit breaker in Node.js
  - Prevents calling unhealthy services repeatedly.
  - Libraries: opossum, cockatiel.
  - Set thresholds: failure %, timeout, half-open test calls.

## Handle scalability in Node.js microservices
  - Horizontal scaling using Kubernetes or Docker
  - Node.js cluster mode
  - Stateless services
  - Asynchronous message-driven workloads

## gRPC - Remote Procedure Calls 
  - binary, faster, streaming support, contract-first.
  - Used for internal microservice communication.
  - faster than JSON/REST
  - strongly typed
  - contract-first

## implement message queues in Node.js
  - Kafka / RabbitMQ (event-driven microservices architecture)
  - **Message Queue (RabbitMQ):** work distribution, messages removed after consumed.
  - **Stream (Kafka):** immutable log, consumers replay messages.


