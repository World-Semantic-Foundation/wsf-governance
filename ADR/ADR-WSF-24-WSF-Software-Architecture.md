# ADR-WSF-24 : WSF Software Architecture

Status: Baseline
Program: World Semantic Foundation
Parent: ADR-WSF-23 ; Semantic Representation Architecture
Related: ADR-WSF-02, ADR-WSF-07, ADR-WSF-12, ADR-WSF-22, ADR-WSF-23
Decision Type: Foundational Software Architecture
Implementation: Implemented by the corresponding change request

---

## 1. Decision Statement

The World Semantic Foundation shall establish a **WSF Software Architecture** that governs how foundational semantic constructs (concepts, relationships, assertions, identities) are encoded into machine-processable representations.

The governing principle is:

> **The Semantic Engine persists meaning ; it does not interpret it.**

The WSF Software Architecture therefore:

- Defines the Semantic Engine as the authoritative runtime ;
- Establishes Store, Services, and API as the three architectural layers ;
- Specifies the interface contracts between layers ;
- Separates the persistence layer from the query/validation layer ;
- Enables multiple client interfaces (CLI, REST, gRPC, GraphQL) ;
- Supports both embedded and distributed deployments ;
- Maintains semantic integrity across all runtime operations.

---

## 2. Why This Decision Is Necessary

The architecture addresses four irreducible requirements:

1. **Authoritative persistence** : semantic state must have a single source of truth.
2. **Queryable semantics** : consumers require performant access to concepts, assertions, relationships.
3. **Validation at runtime** : the engine MUST validate representations per ADR-WSF-23.
4. **Deployment flexibility** : the engine MUST run embedded (single process), distributed (multi-node), and cloud-native.

Without a governed software architecture:

- Multiple persistence implementations create semantic drift ;
- Query languages diverge from canonical semantics ;
- Validation logic fragments across consumer systems ;
- Deployment constraints limit adoption.

---

## 3. Decision Drivers

The WSF Software Architecture addresses:

- Single source of truth for semantic state ;
- High-performance query and validation ;
- Pluggable storage backends (relational, graph, document) ;
- Multi-language client support ;
- Embedded and distributed deployment modes ;
- Observability and operational telemetry ;
- Security and access control ;
- Backups and disaster recovery ;
- Horizontal scaling for high-throughput use cases ;
- Versioning and migration support.

---

## 4. The Three-Layer Software Architecture

### Layer 1 : Store Layer

The Store Layer provides authoritative persistence for the semantic graph.

Responsibilities:

- Persist concepts, relationships, assertions, identities ;
- Maintain indexes for high-performance lookup ;
- Enforce uniqueness on `semantic_id` ;
- Provide transactional consistency ;
- Support snapshot and restore ;
- Emit change events for downstream consumers.

### Layer 2 : Services Layer

The Services Layer implements the semantic operations on top of the Store.

Responsibilities:

- Concept CRUD operations ;
- Relationship traversal and graph queries ;
- Assertion submission, validation, and retrieval ;
- Identity resolution and namespace operations ;
- Validation against SHACL/ShEx shapes ;
- Inference over asserted relationships ;
- Audit trail generation.

### Layer 3 : API Layer

The API Layer exposes the Services Layer to external consumers.

Responsibilities:

- REST API for HTTP-based consumers ;
- gRPC API for high-performance consumers ;
- GraphQL API for flexible querying ;
- CLI for batch and scripting use ;
- WebSocket/SSE for real-time subscriptions.

---

## 5. Store Layer Architecture

### Storage Backend Options

The Store Layer supports three pluggable backend families:

#### Relational Backend (PostgreSQL)

- Mature operational tooling ;
- Strong transactional guarantees ;
- JSON column support for flexible attributes ;
- Native graph extensions (Apache AGE, pgRouting) for graph operations.

#### Graph Backend (Neo4j, Memgraph)

- Native graph storage ;
- High-performance traversal ;
- Cypher query language ;
- Trade-off: weaker ACID guarantees.

#### Document Backend (MongoDB, CosmosDB)

- Flexible schema for evolving concept types ;
- Horizontal scaling ;
- Trade-off: requires manual graph index management.

The choice of backend is deployment-specific. The Store Layer interface is identical across backends.

### Schema Design

The canonical schema includes tables/collections for:

- **concepts** : all concept definitions ;
- **relationships** : typed relationships between concepts ;
- **assertions** : assertions about the world ;
- **identities** : identifier mappings and namespaces ;
- **provenance** : audit trail entries ;
- **evidence** : evidence file references ;
- **versions** : concept version history.

### Indexes

Mandatory indexes:

- `concepts.semantic_id` (unique) ;
- `relationships.subject_id, type, object_id` (composite) ;
- `assertions.subject_id, relationship, object_id` (composite) ;
- `assertions.asserted_at, asserted_by` (for temporal queries) ;
- `provenance.assertion_id` (for audit lookups).

### Transaction Model

- ACID transactions for all state changes ;
- Optimistic concurrency control via version numbers ;
- Read-committed isolation level as default ;
- Serializable isolation available for validation flows.

---

## 6. Services Layer Architecture

### Service Modules

The Services Layer comprises eight service modules:

#### 1. Concept Service

- Create, retrieve, update, delete concepts ;
- Version concept definitions ;
- Specialise and inherit (per ADR-WSF-04) ;
- Retire and deprecate concepts.

#### 2. Relationship Service

- Declare relationship types ;
- Create and remove relationships ;
- Traverse relationship graphs ;
- Query relationship patterns.

#### 3. Assertion Service

- Submit assertions ;
- Validate against shapes ;
- Track lifecycle states ;
- Resolve conflicts.

#### 4. Identity Service

- Resolve identifiers to concepts ;
- Manage namespace registrations ;
- Handle identifier collisions ;
- Maintain canonical naming.

#### 5. Validation Service

- Run SHACL validation ;
- Run ShEx validation ;
- Report validation results ;
- Cache validation outcomes.

#### 6. Inference Service

- Apply OWL 2 RL entailment ;
- Materialise inferred relationships ;
- Expire stale inferences ;
- Provide explanation traces.

#### 7. Query Service

- Execute graph queries (Cypher-like) ;
- Execute semantic queries (SPARQL-like) ;
- Execute full-text searches ;
- Return paginated results.

#### 8. Audit Service

- Record all state changes ;
- Capture attribution metadata ;
- Maintain immutable audit trail ;
- Support audit queries.

### Service Coordination

Services communicate through:

- Synchronous API calls within a single process ;
- Message queues (Kafka, NATS) for distributed deployments ;
- Event bus for state change notifications.

---

## 7. API Layer Architecture

### REST API

REST API conventions:

- Resource-oriented URLs (`/concepts/{id}`, `/assertions/{id}`) ;
- JSON-LD request and response bodies ;
- HTTP status codes for outcome reporting ;
- OAuth 2.0 + OpenID Connect for authentication ;
- RBAC for authorisation.

Endpoints include:

- `GET /concepts/{semantic_id}` : retrieve a concept ;
- `POST /concepts` : create a new concept ;
- `GET /relationships?subject=X&object=Y` : query relationships ;
- `POST /assertions` : submit an assertion ;
- `POST /validate` : run validation on a representation.

### gRPC API

gRPC API for high-throughput consumers:

- Protobuf schemas in `wsf-spec/api/grpc/` ;
- Streaming RPCs for bulk operations ;
- Bidirectional streaming for real-time subscriptions.

### GraphQL API

GraphQL API for flexible querying:

- Schema generated from canonical concept definitions ;
- Single endpoint for composite queries ;
- Subscriptions for change notifications.

### CLI

Command-line interface for batch operations:

- `wsf concept get <semantic_id>` ;
- `wsf assertion submit <file>` ;
- `wsf validate <file>` ;
- `wsf query <expression>`.

### WebSocket / SSE

Real-time subscriptions:

- Concept change notifications ;
- Assertion lifecycle events ;
- Validation result streams.

---

## 8. Deployment Modes

### Embedded Mode

Single-process deployment:

- All three layers in one process ;
- In-memory or file-based storage ;
- For single-user tools, IDE plugins, test suites.

### Distributed Mode

Multi-node deployment:

- Store Layer on dedicated cluster ;
- Services Layer as stateless microservices ;
- API Layer behind load balancer ;
- For production deployments at scale.

### Hybrid Mode

Mixed deployment:

- Read replicas for query distribution ;
- Master node for write coordination ;
- Cache layer for hot concepts ;
- For moderate-scale production deployments.

---

## 9. Observability Architecture

The Semantic Engine emits:

### Metrics (Prometheus-compatible)

- Request rate, error rate, latency ;
- Concept/assertion counts ;
- Validation pass/fail rates ;
- Storage utilisation.

### Logs (Structured, JSON)

- All state changes ;
- Validation events ;
- Error conditions ;
- Audit trail entries.

### Traces (OpenTelemetry)

- Distributed tracing across services ;
- Span annotations for semantic operations ;
- Sampling for high-throughput paths.

### Dashboards

Pre-built Grafana dashboards for:

- System health overview ;
- Concept lifecycle trends ;
- Validation pipeline status ;
- Query performance analysis.

---

## 10. Security Architecture

### Authentication

- OAuth 2.0 with OpenID Connect ;
- Mutual TLS for service-to-service ;
- API key authentication for embedded clients.

### Authorisation

- Role-based access control (RBAC) ;
- Attribute-based access control (ABAC) for fine-grained policies ;
- Multi-tenant isolation in distributed deployments.

### Audit

- All state changes captured immutably ;
- Cryptographic signing per ADR-WSF-22 ;
- Compliance reporting (GDPR, SOC 2).

### Encryption

- TLS 1.3 for transport ;
- AES-256 for at-rest encryption ;
- Field-level encryption for sensitive attributes.

---

## 11. Backup and Recovery

### Backup Strategy

- Continuous incremental backups ;
- Daily full snapshots ;
- Cross-region replication for disaster recovery ;
- Content-addressed backup verification.

### Recovery Objectives

- Recovery Point Objective (RPO) : 1 hour ;
- Recovery Time Objective (RTO) : 4 hours ;
- Automated recovery runbooks ;
- Regular DR testing schedule.

---

## 12. Versioning and Migration

### Version Compatibility

The engine supports multiple major versions concurrently:

- Version negotiation during connection ;
- Backward-compatible APIs for prior versions ;
- Migration paths for breaking changes.

### Migration Tools

- Concept version migrators ;
- Assertion schema migrators ;
- Namespace consolidation tools ;
- Automated migration test suites.

---

## 13. Performance Characteristics

The architecture establishes:

- **Write throughput** : minimum 1K concepts/second, target 10K ;
- **Read throughput** : minimum 10K queries/second, target 100K ;
- **Validation throughput** : minimum 500 assertions/second, target 5K ;
- **Query latency** : <50ms p99 for cached queries, <500ms p99 for cold queries.

These are reference benchmarks; actual performance varies by deployment.

---

## 14. Client SDK Architecture

The architecture defines client SDKs in:

- TypeScript / JavaScript (browser, Node.js) ;
- Python (3.10+) ;
- Java (17+) ;
- Rust (stable) ;
- Go (1.21+).

SDKs share:

- Canonical encoding/decoding logic ;
- Validation client ;
- API client ;
- Local cache for offline operation.

---

## 15. Implementation Implications

The architecture requires:

- **Reference implementation** : open-source Semantic Engine ;
- **Client SDKs** : five language ecosystems ;
- **CLI tool** : command-line interface ;
- **Helm charts** : Kubernetes deployment ;
- **Terraform modules** : cloud provisioning ;
- **Documentation portal** : comprehensive API docs ;
- **Test suite** : end-to-end validation ;
- **Performance benchmarks** : continuous benchmarking.

---

## 16. Consequences

### Positive

- Single source of truth eliminates semantic drift ;
- Pluggable backends support diverse deployment scenarios ;
- Multi-protocol APIs enable ecosystem breadth ;
- Version compatibility supports long-term maintenance ;
- Observability ensures operational reliability.

### Negative

- Multiple service modules increase complexity ;
- Pluggable backends require test coverage across backends ;
- Performance benchmarks require continuous investment ;
- Migration tooling required for version evolution.

---

## 17. Rejected Alternatives

### A : Monolithic Single-Layer Design

Combine Store, Services, and API in one layer. Rejected because:

- Limits deployment flexibility ;
- Couples persistence to interface ;
- Reduces testability.

### B : Direct Database Access

Allow consumers direct database access. Rejected because:

- Bypasses validation ;
- Skips audit trail ;
- Prevents semantic integrity guarantees.

### C : Single API Protocol

Use only REST (or only gRPC). Rejected because:

- Limits consumer ecosystem ;
- Forces performance trade-offs ;
- Excludes real-time use cases.

### D : Cloud-Only Deployment

Require cloud-native deployment. Rejected because:

- Excludes embedded use cases ;
- Limits air-gapped deployments ;
- Forces vendor lock-in.

### E : Implicit Versioning

Version concepts without explicit version declarations. Rejected because:

- Causes silent breakage ;
- Prevents governance of evolution ;
- Complicates migration planning.

---

## 18. Explicit Non-Decisions

This ADR does NOT decide:

- Specific storage backend default (deployment-specific) ;
- Exact OAuth 2.0 grant types ;
- Specific Kubernetes distributions ;
- Cloud provider selection ;
- Specific monitoring vendor products ;
- Particular client SDK implementation details beyond interface contracts.

These decisions belong to deployment-specific CRs and operational policies.

---

## 19. Decision Summary

The World Semantic Foundation establishes a WSF Software Architecture that:

- Defines Store, Services, and API as three architectural layers ;
- Supports pluggable backends (relational, graph, document) ;
- Exposes eight service modules for semantic operations ;
- Provides REST, gRPC, GraphQL, CLI, and streaming APIs ;
- Supports embedded, distributed, and hybrid deployments ;
- Embeds observability, security, and backup capabilities ;
- Maintains version compatibility across major versions ;
- Enables five language ecosystem client SDKs.

---

## 20. Required Follow-On ADRs

The implementation of this ADR requires:

- ADR-WSF-25 : WSF Integration Architecture (defines external system interfaces)
- ADR-WSF-26 : WSF Visualization Architecture (defines presentation rendering)

---

*Status: Baseline. Parent: ADR-WSF-23.*