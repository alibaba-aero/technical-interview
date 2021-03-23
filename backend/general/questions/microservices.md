# Microservices

* What are monolith's downsides and advantages?
* What are microservices downsides and advantages?
* Service Registry & Discovery
    * What's service registry?
    * Tools for service-discovery (Consul, Redis, ...)
    * Where do we need them?
* Load-Balancing
    * What are the application requirements for load-balancing?
    * What's HA?
    * What's replication?
    * What's sharding?
    * What is the difference between Horizontal-Scaling and Vertical-Scaling?
* Distributed Transactions
    * What's SAGA?
    * What's two-phase commit?
* Metrics, Monitoring, Tracing, Logging
    * What's CorrelationId?
    * What's distributed tracing? Why we need that?
    * What are metrics? How to collect them?
    * What's monitoring? How it's related to the metrics?
    * What's centralized logging?
        * What's ELK?
        * How to keep the logs while the logging provider is down?
* Key-Vaults
    * Where to store secret things like passwords, api-keys, ...?
    * What's key-vault?
* Service-Mesh
    * What's service-mesh? Why we need that?
    * What's Side-Car pattern?
* Communication Patterns (Inbox/Outbox, Fan-in/Fan-Out, Pub/Sub, Peer-2-Peer, ...)
    * How microservices can talk to each other?
    * What's gRPC? What's protobuf?
* Message Delivery Semantics (At-Least-Once, At-Most-Once, Exactly-Once) + Retry
    * What's at-least-once in messaging?
    * What's at-most-once in messaging?
    * How to achieve exactly-once delivery in messaging?
    * What should we do when a message not get delivered?
    * What's retry pattern?
