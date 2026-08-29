# ADR-WSF-25 : WSF Integration Architecture

Status: Baseline
Program: World Semantic Foundation
Parent: ADR-WSF-24 ; WSF Software Architecture
Related: ADR-WSF-02, ADR-WSF-12, ADR-WSF-22, ADR-WSF-23, ADR-WSF-24
Decision Type: Foundational Integration Architecture
Implementation: Implemented by the corresponding change request

---

## 1. Decision Statement

The World Semantic Foundation shall establish a **WSF Integration Architecture** that governs how foundational semantic constructs (concepts, relationships, assertions, identities) are exchanged with external semantic systems, enterprise platforms, and downstream consumers.

The governing principle is:

> **Integration bridges semantic systems ; it does not replace semantic authority.**

The WSF Integration Architecture therefore:

- Defines the connector pattern as the canonical integration unit ;
- Establishes read, write, and bidirectional connector categories ;
- Maintains semantic integrity during integration ;
- Supports federated semantic graphs across organisations ;
- Enables ecosystem-wide interoperability ;
- Preserves provenance across integration boundaries.

---

## 2. Why This Decision Is Necessary

The architecture addresses four irreducible requirements:

1. **Semantic interoperability** : external systems must consume WSF semantics without translation loss.
2. **Federated operation** : multiple WSF instances must collaborate across organisational boundaries.
3. **Authoritative direction** : integration must preserve the source-of-truth direction for assertions.
4. **Heterogeneous protocols** : different external systems use different exchange protocols.

Without a governed integration architecture:

- Translation logic fragments across consumer systems ;
- Semantic drift accumulates at integration boundaries ;
- Provenance chains break across systems ;
- Federation becomes brittle and unscalable.

---

## 3. Decision Drivers

The WSF Integration Architecture addresses:

- Multi-protocol exchange (REST, gRPC, Kafka, file-based) ;
- Semantic fidelity across translation ;
- Federated identity resolution ;
- Cross-organisational provenance ;
- Event-driven integration patterns ;
- Bulk and streaming operations ;
- Conflict resolution across federated instances ;
- Security and trust across boundaries ;
- Version compatibility across federated peers ;
- Operational observability.

---

## 4. Connector Pattern

The connector pattern is the canonical integration unit. A connector encapsulates:

- **Source/sink identification** : the external system being integrated ;
- **Protocol binding** : the exchange protocol (REST, gRPC, Kafka) ;
- **Semantic mapping** : how external representations map to WSF canonical forms ;
- **Provenance capture** : attribution for integrated content ;
- **Error handling** : retry, dead-letter, escalation policies.

Connectors are stateless modules that can be deployed, scaled, and updated independently.

---

## 5. Connector Categories

The architecture defines three connector categories:

### Read Connectors

Read connectors ingest external content into WSF:

- Pull external concepts, assertions, and relationships ;
- Translate to WSF canonical forms ;
- Capture provenance (external source, ingestion time, ingestion agent) ;
- Apply validation before persistence.

Examples:

- **OpenDEA connector** : reads OpenDEA semantic assets ;
- **TM Forum connector** : reads TM Forum ontology ;
- **Schema.org connector** : reads Schema.org vocabulary ;
- **SKOS connector** : reads SKOS concept schemes.

### Write Connectors

Write connectors export WSF content to external systems:

- Push concepts, assertions, and relationships ;
- Translate from WSF canonical forms ;
- Generate target-system representations ;
- Preserve semantic identity in target system.

Examples:

- **Knowledge Graph connector** : exports to Neo4j, Amazon Neptune ;
- **Search Index connector** : exports to Elasticsearch, OpenSearch ;
- **Documentation connector** : exports to Markdown portals, static sites ;
- **Data Warehouse connector** : exports to Snowflake, BigQuery.

### Bidirectional Connectors

Bidirectional connectors enable real-time synchronisation:

- Subscribe to WSF change events ;
- Subscribe to external system change events ;
- Maintain semantic consistency across boundaries ;
- Resolve conflicts using governed policies.

Examples:

- **Federated WSF connector** : bidirectional sync with peer WSF instances ;
- **Active ontology connector** : bidirectional sync with active ontology platforms.

---

## 6. Semantic Mapping

Every connector performs semantic mapping between external and WSF representations.

### Mapping Modes

#### 1 : 1 Direct Mapping

External concept maps directly to a single WSF concept. Example: `schema:Person → wsf:Entity`.

#### N : 1 Aggregation

Multiple external concepts aggregate to one WSF concept. Example: `schema:givenName + schema:familyName → wsf:Identity`.

#### 1 : N Decomposition

One external concept decomposes to multiple WSF concepts. Example: `external:Address → wsf:Space + wsf:Context`.

#### 0 : 1 New Concept

External concept requires a new WSF concept not yet defined. Connector flags the gap for governance review.

### Mapping Validation

Every mapping MUST be:

- Documented in `wsf-connectors/<connector>/mappings.yaml` ;
- Reviewed and approved through the CR process ;
- Tested with bidirectional round-trip cases ;
- Versioned with the connector release.

---

## 7. Federation Architecture

The WSF Integration Architecture supports federation across multiple WSF instances.

### Federation Topology

#### Hub-and-Spoke

One central hub, multiple spoke instances. Hub acts as authoritative indexer.

#### Peer-to-Peer

Multiple peer instances exchange content bidirectionally. No central authority.

#### Hierarchical

Multiple tiers of WSF instances with defined authority flow.

### Federation Protocol

Federation uses:

- **Discovery** : instances register with a federation directory ;
- **Handshake** : peers negotiate shared semantics and namespaces ;
- **Sync** : peers exchange concepts, assertions, and provenance ;
- **Conflict resolution** : governed policies resolve cross-instance conflicts ;
- **Trust establishment** : cryptographic signatures verify peer authenticity.

### Cross-Instance Identity

Federated identity resolution:

- Each instance owns a namespace ;
- Cross-instance references use federated identifiers ;
- Namespace registries resolve identifiers to instances ;
- Trust chains verify identifier provenance.

---

## 8. Event-Driven Integration

The architecture supports event-driven patterns for real-time integration.

### Event Sources

- WSF state changes (concept created, assertion submitted) ;
- External system changes (via Change Data Capture) ;
- Scheduled events (daily syncs, cleanup) ;
- User-initiated events (manual sync requests).

### Event Bus

- Apache Kafka for high-throughput ;
- NATS for lightweight pub/sub ;
- AWS EventBridge / Azure Event Grid for cloud-native ;
- Redis Streams for embedded use.

### Event Schema

Events use CloudEvents specification:

- `id` : unique event identifier ;
- `source` : event source URI ;
- `type` : event type (e.g., `wsf.concept.created`) ;
- `time` : event timestamp ;
- `datacontenttype` : payload content type ;
- `data` : event payload (JSON-LD).

---

## 9. Exchange Protocols

The architecture supports multiple exchange protocols:

### REST over HTTPS

Synchronous request-response for low-latency needs.

### gRPC

Bidirectional streaming for high-throughput needs.

### Kafka

Fire-and-forget events for decoupled systems.

### File-Based

Batch exchanges via shared storage (S3, NFS).

### WebSocket

Real-time subscriptions for collaborative use.

The choice of protocol is per-integration, governed by operational requirements.

---

## 10. Bulk Operations

For large-scale integration, the architecture supports bulk operations:

### Bulk Import

- File-based ingestion (`.wsf-archive`, `.wsfs` formats) ;
- Streaming import for very large graphs ;
- Checkpoint-and-resume for fault tolerance ;
- Progress reporting.

### Bulk Export

- Subgraph selection ;
- Format conversion (canonical → target) ;
- Compression for transfer efficiency ;
- Checksum verification.

---

## 11. Security and Trust

Integration security:

### Mutual TLS

Service-to-service authentication via mutual TLS.

### OAuth 2.0 + OIDC

User-level authentication for interactive integrations.

### API Keys

Embedded client authentication with scoped keys.

### Cryptographic Signing

Assertion-level Ed25519 signatures for cross-boundary trust.

### Access Control

Per-connector access policies:

- Read-only access ;
- Read-write access ;
- Approval-required for write ;
- Audit-required for sensitive operations.

---

## 12. Observability

Integration observability:

### Connector Metrics

- Messages processed per second ;
- Error rates by error type ;
- Latency p50, p95, p99 ;
- Queue depth for buffered messages.

### Connector Logs

- Structured JSON logs per message ;
- Correlation IDs for tracing ;
- Error context with payload samples ;
- Audit trail entries.

### Connector Traces

- Distributed tracing across connector and WSF ;
- Span annotations for semantic operations ;
- Sampling for high-throughput paths.

### Dashboards

Pre-built dashboards for:

- Connector health overview ;
- Integration throughput trends ;
- Error rate analysis ;
- Federation status.

---

## 13. Versioning and Compatibility

Integration versioning:

### Connector Versioning

- Major versions for breaking protocol changes ;
- Minor versions for additive changes ;
- Patch versions for non-semantic fixes.

### Backward Compatibility

- New connector versions support prior protocol versions for N-1, N-2 ;
- Deprecation policies with 6-month notice ;
- Migration guides for breaking changes.

### Federation Version Negotiation

- Peers negotiate highest mutually-supported version ;
- Graceful degradation when version mismatch occurs ;
- Explicit error reporting for unsupported features.

---

## 14. Connector Development Lifecycle

Connectors evolve under governance:

1. **Discovery** : integration need identified ;
2. **Scoping** : connector scope defined in CR ;
3. **Development** : connector implementation per spec ;
4. **Testing** : round-trip and load tests ;
5. **Review** : governance review and approval ;
6. **Deployment** : connector deployed via standard pipeline ;
7. **Monitoring** : operational observability active ;
8. **Maintenance** : updates under version governance.

---

## 15. Connector Catalog

The architecture defines a connector catalog maintained in `wsf-connectors/`:

```
wsf-connectors/
├── catalog.yaml                   # master catalog
├── enterprise/
│   ├── sap/
│   ├── salesforce/
│   └── oracle/
├── semantic/
│   ├── opendea/
│   ├── tmforum/
│   ├── schemaorg/
│   └── skos/
├── knowledge/
│   ├── neo4j/
│   ├── amazon-neptune/
│   └── graphdb/
├── documentation/
│   ├── markdown-portal/
│   ├── static-site/
│   └── confluence/
└── search/
    ├── elasticsearch/
    ├── opensearch/
    └── solr/
```

---

## 16. Implementation Implications

The architecture requires:

- **Connector SDK** : development toolkit for connector authors ;
- **Connector registry** : discoverable catalog of certified connectors ;
- **Test harness** : automated round-trip and load testing ;
- **Deployment templates** : Helm charts, Terraform modules ;
- **Monitoring stack** : Prometheus + Grafana integration ;
- **Documentation portal** : connector authoring guide ;
- **Federation directory** : peer discovery service.

---

## 17. Consequences

### Positive

- Canonical connector pattern ensures consistency ;
- Federated operation enables ecosystem scale ;
- Event-driven integration enables real-time ;
- Versioned compatibility supports long-term maintenance ;
- Strong security and trust boundaries.

### Negative

- Connector development overhead per integration ;
- Federation coordination complexity ;
- Event schema evolution requires cross-system coordination ;
- Multiple protocols increase test surface area.

---

## 18. Rejected Alternatives

### A : Direct Database Integration

Allow external systems direct database access. Rejected because:

- Bypasses semantic validation ;
- Skips audit trail ;
- Prevents semantic integrity.

### B : Single Integration Pattern

Force all integrations through one pattern. Rejected because:

- Limits use case coverage ;
- Forces inappropriate trade-offs ;
- Excludes high-throughput scenarios.

### C : Implicit Federation

Allow federation without governance. Rejected because:

- Causes namespace collisions ;
- Undermines provenance ;
- Limits scalability.

### D : No Versioning

Deploy connector changes without version control. Rejected because:

- Causes silent breakage ;
- Prevents governance of evolution ;
- Complicates migration.

### E : Single Security Model

Apply one security model across all integrations. Rejected because:

- Limits deployment flexibility ;
- Forces inappropriate security overhead ;
- Excludes air-gapped scenarios.

---

## 19. Explicit Non-Decisions

This ADR does NOT decide:

- Specific connector implementations ;
- Cloud provider selection ;
- Specific event bus vendor ;
- Specific OAuth 2.0 grant types ;
- Connector SDK language ;
- Specific monitoring vendor products.

These decisions belong to integration-specific CRs and operational policies.

---

## 20. Decision Summary

The World Semantic Foundation establishes a WSF Integration Architecture that:

- Defines the connector pattern as the canonical integration unit ;
- Distinguishes read, write, and bidirectional connectors ;
- Maintains semantic integrity through governed semantic mappings ;
- Supports federation across organisational boundaries ;
- Enables event-driven integration via standardised schemas ;
- Provides multi-protocol exchange (REST, gRPC, Kafka, file-based, WebSocket) ;
- Embeds security, observability, and version compatibility ;
- Organises connectors into a discoverable catalog.

---

## 21. Required Follow-On ADRs

The implementation of this ADR requires:

- ADR-WSF-26 : WSF Visualization Architecture (defines visual presentation of integrated data)
- ADR-WSF-27 : WSF Digital Twin and Simulation Architecture (defines simulation-specific integration patterns)

---

*Status: Baseline. Parent: ADR-WSF-24.*