# ADR-WSF-23 : Semantic Representation Architecture

Status: Baseline
Program: World Semantic Foundation
Parent: ADR-WSF-22 ; Assertion and Provenance Model
Related: ADR-WSF-02, ADR-WSF-04, ADR-WSF-12, ADR-WSF-19, ADR-WSF-21, ADR-WSF-22
Decision Type: Foundational Semantic Architecture
Implementation: Implemented by the corresponding change request

---

## 1. Decision Statement

The World Semantic Foundation shall establish a **Semantic Representation Architecture** that governs how foundational semantic constructs (concepts, relationships, assertions, identities) are encoded into machine-processable representations.

The governing principle is:

> **Semantic representations serve meaning ; they do not constrain it.**

The Semantic Representation Architecture therefore:

- Establishes representation as a translation layer separate from semantic identity;
- Defines the canonical encoding formats (JSON, JSON-LD, Turtle, RDF/XML, YAML, Protobuf);
- Specifies the formal grounding layer (SHACL, ShEx, OWL profiles) for validation;
- Distinguishes syntactic correctness from semantic validity;
- Provides bidirectional round-trip capability between representations without information loss;
- Supports serialisation, deserialisation, and canonicalisation.

---

## 2. Why This Decision Is Necessary

The architecture must address four irreducible requirements:

1. **Representation neutrality** : WSF concepts must remain stable across representation technologies.
2. **Machine processability** : automated systems require concrete, parseable encodings.
3. **Validation grounding** : representations must be checkable against semantic constraints.
4. **Interoperability** : downstream systems and tools must consume and produce representations without semantic loss.

Without a governed representation architecture, the following risks emerge:

- **Vendor lock-in** : a single representation technology becomes de facto standard.
- **Information loss** : semantics present in one representation disappear in another.
- **Validation gaps** : representations cannot be checked for semantic conformance.
- **Tool fragmentation** : each consumer reimplements translation, with semantic drift.

---

## 3. Decision Drivers

The Semantic Representation Architecture addresses:

- Representation independence from semantic identity;
- Round-trip stability (encode → decode → identical meaning);
- Validation at both syntactic and semantic levels;
- Tool ecosystem support;
- Human readability for editorial workflows;
- Machine efficiency for runtime processing;
- Version compatibility across representation specifications;
- Streaming and incremental processing for large semantic graphs;
- Cryptographic signing for assertions;
- Compression and storage optimisation.

---

## 4. The Representation Stack

The architecture establishes a five-layer representation stack:

### Layer 1 : Semantic Identity Layer

Concept identifiers (`wsf:Concept`, `wsf-rel:hasPart`) anchor all representations.

### Layer 2 : Canonical Encoding Layer

Three canonical encoding formats with explicit mappings:

- **JSON-LD** : primary canonical encoding for programmatic use
- **Turtle** : canonical encoding for RDF-aware tools and semantic web contexts
- **YAML** : canonical encoding for human-authored configuration and editorial use

### Layer 3 : Constraint Grounding Layer

Formal languages for representing constraints and validation:

- **SHACL** : primary validation language for shape constraints
- **ShEx** : secondary validation language for compact shape expressions
- **OWL 2 RL** : reasoning profile for entailment within constrained performance envelope

### Layer 4 : Distribution Format Layer

Wire formats for transport:

- **Protocol Buffers** : high-performance runtime encoding
- **MessagePack** : compact binary encoding
- **CBOR** : constrained environments encoding

### Layer 5 : Presentation Layer

Human-facing rendering:

- **Markdown** : narrative documentation and editorial content
- **Mermaid / GraphViz** : diagram rendering
- **HTML / SVG** : web presentation

---

## 5. Canonical Encoding Rules

### Rule 1 : Single Meaning, Multiple Encodings

The same concept MAY be encoded in any canonical format. The semantic identity remains stable across all encodings.

### Rule 2 : Canonical JSON-LD Profile

JSON-LD is the primary programmatic encoding. The profile:

- Uses `@context` to declare namespace bindings;
- Embeds `@id` for resource identification;
- Uses `@type` for type assertions;
- Follows JSON-LD 1.1 specification with WSF-defined context document.

### Rule 3 : Canonical Turtle Profile

Turtle serves RDF-aware consumers. The profile:

- Prefixes: `@prefix wsf: <https://world-semantic-foundation.org/ns/>`
- Prefixes: `@prefix wsf-rel: <https://world-semantic-foundation.org/rel/>`
- Type declarations use `a` shorthand.

### Rule 4 : Canonical YAML Profile

YAML serves human-authored content. The profile:

- Two-space indentation;
- UTF-8 encoding;
- Explicit keys (no implicit JSON-style shorthand).

---

## 6. Round-Trip Stability

The architecture requires that any canonical encoding can be decoded to the canonical semantic model, and re-encoded to the original encoding without loss.

The properties enforced:

- **Round-trip identity** : `decode(encode(x)) = x` for all canonical encodings.
- **Equivalence preservation** : semantically equivalent representations remain equivalent across all formats.
- **Lossless transformation** : no semantic information discarded during translation.

---

## 7. Validation Architecture

The architecture distinguishes three validation levels:

### Level 1 : Syntactic Validation

- Encoding parses successfully per the format specification.
- JSON-LD context is well-formed.
- Turtle syntax is valid.
- YAML is parseable.

### Level 2 : Structural Validation

- Required fields present per the concept definition (per ADR-WSF-20).
- Type assertions match the declared concept type.
- Identity references resolve to declared concepts.

### Level 3 : Semantic Validation

- Constraint conformance per SHACL/ShEx shapes (per ADR-WSF-22).
- Inheritance correctness per ADR-WSF-04.
- Assertion validity per the Assertion and Provenance Model.
- Cross-reference consistency across the semantic graph.

A representation MAY pass syntactic validation but FAIL structural or semantic validation. Each level is independently checkable.

---

## 8. Information-Carrier vs Non-Carrier Components

The architecture distinguishes:

### Information Carriers

Components that carry semantic meaning and MUST be preserved across all encodings:

- Concept identity (`semantic_id`)
- Relationship types (`wsf-rel:*`)
- Assertion structure
- Identity references
- Temporal markers (per wsf:time vocabulary)
- Spatial markers (per wsf:space vocabulary)
- Evidence references

### Non-Carriers

Components that do not carry semantic meaning and MAY be reformatted:

- Whitespace
- Key ordering in JSON objects
- Comment annotations
- Pretty-print formatting
- File metadata (timestamps, author info)

---

## 9. Streaming and Incremental Processing

For large semantic graphs, the architecture supports:

### Streaming JSON-LD

- Line-delimited JSON-LD (JSON-LD stream);
- Frame-by-frame processing;
- Memory-efficient for graphs >100K nodes.

### Turtle Streaming

- SPARQL-compatible bulk loading;
- Stream-based parsing for incremental validation.

### Batch Processing

- Protobuf batch format for bulk imports/exports;
- Compressed container format (.wsf-archive).

---

## 10. Cryptographic and Integrity Features

The architecture supports:

- **Content addressing** : SHA-256 hash of canonical serialisation as content identifier.
- **Digital signatures** : assertions MAY carry Ed25519 signatures.
- **Provenance chains** : signed audit trails (per ADR-WSF-22).
- **Tamper detection** : hash verification detects any modification.

---

## 11. Version Compatibility

The Semantic Representation Architecture evolves under governance:

- **Major versions** : breaking changes to encoding or shape definitions.
- **Minor versions** : additive changes (new optional fields).
- **Patch versions** : non-semantic fixes (typos, clarifications).

Downstream consumers SHALL declare the WSF Representation Version they support. Representations SHALL declare the version they conform to.

---

## 12. Tool Ecosystem

The architecture enables the following tools:

- **WSF Encoder** : serialises concepts to any canonical format.
- **WSF Decoder** : deserialises representations to concepts.
- **WSF Validator** : runs three-level validation.
- **WSF Transformer** : converts between canonical formats losslessly.
- **WSF Diff** : compares two representations for semantic equivalence.
- **WSF Sign** : produces cryptographic signatures for assertions.
- **WSF Verify** : validates signatures and content hashes.

Tool implementations MAY be provided by multiple vendors; the architecture defines interfaces, not specific implementations.

---

## 13. Distribution and Storage Formats

### Compact Format (`.wsf`)

A zipped bundle containing:

- `manifest.yaml` : bundle metadata;
- `semantic-graph.json` : concept graph;
- `assertions.json` : assertion set;
- `evidence/` : evidence file directory;
- `provenance.json` : provenance chain.

### Streaming Format (`.wsfs`)

Line-delimited JSON-LD for real-time consumption.

### Archive Format (`.wsf-archive`)

Tar + gzip with content-addressed storage.

---

## 14. Performance Characteristics

The architecture establishes:

- **Encoding throughput** : minimum 50K concepts/second on reference hardware.
- **Decoding throughput** : minimum 100K concepts/second.
- **Validation throughput** : minimum 10K assertions/second with full three-level validation.
- **Memory footprint** : <100 bytes per concept in canonical encoding.

These targets are reference benchmarks; actual performance varies by implementation.

---

## 15. Interoperability Boundaries

The architecture maintains:

- **JSON-LD ↔ Turtle** : full bidirectional mapping.
- **JSON-LD ↔ YAML** : full bidirectional mapping for YAML-conformant concepts.
- **JSON-LD ↔ Protobuf** : lossless binary encoding for runtime use.
- **Canonical ↔ Presentation** : presentation formats derive from canonical encodings.

Translation between formats SHALL be governed by ADR-WSF-19 (Semantic Relationship Model) and SHALL NOT alter semantic identity.

---

## 16. Implementation Implications

The architecture requires:

- **Library implementations** : WSF Encoder/Decoder libraries in Java, Python, TypeScript, Rust.
- **CLI tools** : command-line access for batch processing.
- **Web service** : HTTP API for on-demand encoding/decoding.
- **Schema repository** : canonical schemas hosted in wsf-spec/.
- **Test suite** : round-trip test cases covering all canonical formats.
- **Performance benchmarks** : continuous benchmarking per performance characteristics.

---

## 17. Consequences

### Positive

- Semantic identity remains stable across representation technologies.
- Multiple tool ecosystems can interoperate through canonical formats.
- Validation can occur at multiple levels independently.
- Round-trip stability prevents information loss.
- Version compatibility supports ecosystem evolution.
- Cryptographic features enable auditability and trust.

### Negative

- Multiple canonical formats increase test surface area.
- Validation tooling must support multiple validation languages.
- Round-trip guarantees require canonical form definition.
- Performance overhead for canonical-form enforcement.

---

## 18. Rejected Alternatives

### A : JSON-Only

Restrict to JSON encoding only. Rejected because:

- Excludes RDF-aware consumers.
- Limits semantic web interoperability.
- Reduces tool ecosystem flexibility.

### B : Protobuf-Only

Use Protocol Buffers as the only encoding. Rejected because:

- Not human-friendly for editorial workflows.
- Tooling requires schema files for decoding.
- Limits semantic web integration.

### C : Free-Form Translation

Allow each consumer to define its own format translation. Rejected because:

- Causes semantic drift between translations.
- Prevents cross-consumer validation.
- Undermines canonical representation guarantees.

### D : Single Validation Level

Validate only at syntactic level. Rejected because:

- Misses structural defects.
- Allows semantically invalid representations.
- Reduces trust in the semantic layer.

### E : Versioned Compatibility Without Migration Paths

Use semver without explicit migration paths. Rejected because:

- Consumers face breaking changes without guidance.
- Migration complexity is hidden from governance.
- Tooling cannot support multi-version ecosystems.

---

## 19. Explicit Non-Decisions

This ADR does NOT decide:

- Specific Java/Python/TypeScript library implementations;
- Particular crypto signature schemes beyond Ed25519;
- Cloud-hosted vs self-hosted tool deployment;
- Specific SHACL engine implementations;
- Compression algorithm choices;
- Streaming protocol details beyond format compatibility;
- Specific test framework selection.

These decisions belong to follow-on CRs and implementation specifications.

---

## 20. Decision Summary

The World Semantic Foundation establishes a Semantic Representation Architecture that:

- Anchors representations in semantic identity ;
- Provides three canonical encodings (JSON-LD, Turtle, YAML) ;
- Grounds validation in SHACL, ShEx, and OWL profiles ;
- Maintains round-trip stability across all formats ;
- Supports streaming, distribution, and cryptographic features ;
- Evolves under versioned governance ;
- Enables a multi-vendor tool ecosystem through defined interfaces.

---

## 21. Required Follow-On ADRs

The implementation of this ADR requires:

- ADR-WSF-24 : WSF Software Architecture (defines tool implementations)
- ADR-WSF-25 : WSF Integration Architecture (defines external system interfaces)
- ADR-WSF-26 : WSF Visualization Architecture (defines presentation rendering)
- ADR-WSF-27 : WSF Digital Twin and Simulation Architecture (defines simulation-specific representations)

---

*Status: Baseline. Parent: ADR-WSF-22.*