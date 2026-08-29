# ADR-WSF-21 — Namespace and Reference Model

Status: Baseline
Program: World Semantic Foundation
Parent: ADR-WSF-20 — Concept Definition Model
Related: ADR-WSF-01, ADR-WSF-18, ADR-WSF-19, ADR-WSF-20, ADR-WSF-23
Decision Type: Foundational Semantic Architecture
Implementation: Implemented by the corresponding change request

---

## 1. Decision Statement

The World Semantic Foundation shall establish a **Namespace and Reference Model** that governs how WSF identifiers are constructed, namespaces are organized, references are resolved, and cross-namespace integration is performed.

The governing principle is:

> **WSF identifiers are persistent, globally unique, resolvable references that encode namespace, concept type, and instance in a controlled scheme.**

The Namespace Model therefore:

- Defines the WSF namespace hierarchy;
- Establishes identifier syntax and conventions;
- Provides namespace management rules;
- Defines reference resolution algorithms;
- Governs cross-namespace integration.

---

## 2. Why This Decision Is Necessary

WSF:

1. **Reference any concept** from anywhere — global resolution required.
2. **Distinguish namespaces** — different authorities, different scopes.
3. **Maintain stability** — identifiers persist across representations.
4. **Support federation** — different organizations contribute concepts.
5. **Resolve references** — given an identifier, find the concept.

Without a Namespace Model:

- Identifiers collide across authorities;
- References cannot be resolved reliably;
- Integration across organizations fails;
- Concepts cannot be unambiguously cited.

---

## 3. Decision Drivers

The Namespace and Reference Model must provide:

- **Global uniqueness**: No two identifiers refer to different things.
- **Local uniqueness**: Within a namespace, no collisions.
- **Persistence**: Identifiers don't change.
- **Resolvability**: Identifiers can be resolved to concepts.
- **Human readability**: Identifiers are meaningful to humans.
- **Machine readability**: Identifiers are processable by machines.
- **Federation**: Multiple authorities can contribute.
- **Versioning**: Identifiers can carry version information.
- **Context applicability**: Identifiers can be context-qualified.

---

## 4. WSF Namespace Hierarchy

WSF SHALL adopt the following namespace hierarchy:

```
wsf:                              # Root WSF namespace
   │
   ├── wsf-concept:               # Tier 1/2/3 concepts
   │     ├── wsf-concept:Entity
   │     ├── wsf-concept:Concept
   │     ├── wsf-concept:Relationship
   │     └── ...
   │
   ├── wsf-rel:                   # Semantic Relationships
   │     ├── wsf-rel:possesses
   │     ├── wsf-rel:specializes
   │     └── ...
   │
   ├── wsf-cap:                   # Capabilities
   │     ├── wsf-cap:OrderFulfillment
   │     └── ...
   │
   ├── wsf-dis:                   # Dispositions
   │     ├── wsf-dis:Capacity
   │     └── ...
   │
   ├── wsf-ctx:                   # Contexts
   │     ├── wsf-ctx:enterprise
   │     └── ...
   │
   ├── wsf-assertion:             # Assertions
   │     ├── wsf-assertion:OTCHERE-OrderFulfillment-001
   │     └── ...
   │
   ├── wsf-ex:                    # Examples
   │     ├── wsf-ex:OTCHERE-Inc
   │     ├── wsf-ex:Kwesi
   │     └── ...
   │
   ├── wsf-id:                    # Identity references
   │     └── ...
   │
   ├── wsf-time:                  # Time references
   │     └── ...
   │
   └── wsf-space:                 # Space references
         └── ...
```

Each sub-namespace is governed by its own rules but follows common conventions.

---

## 5. Identifier Syntax

WSF identifiers SHALL follow this syntax:

```
[scheme:][namespace:]local-name[#version]
```

Components:
- **scheme**: Optional URI scheme (default: `https://wsf.world-semantic-foundation.org/`)
- **namespace**: Sub-namespace (e.g., `concept`, `rel`, `cap`)
- **local-name**: Human-readable name within namespace
- **version**: Optional semantic version

Examples:
- `wsf-concept:Capability` — Tier 1 concept
- `wsf-concept:BusinessCapability` — Tier 2 specialized concept
- `wsf-rel:possesses` — Relationship
- `wsf-cap:OTCHERE-OrderFulfillment` — Specific capability
- `wsf-ex:OTCHERE-Inc` — Example entity
- `wsf-assertion:OTCHERE-OrderFulfillment-001` — Specific assertion
- `wsf-concept:Capability@1.0.0` — Specific version (optional)

---

## 6. CURIEs (Compact URIs)

For human convenience, WSF SHALL support CURIEs:

```yaml
prefixes:
  wsf-concept: "https://wsf.world-semantic-foundation.org/concept/"
  wsf-rel: "https://wsf.world-semantic-foundation.org/rel/"
  wsf-cap: "https://wsf.world-semantic-foundation.org/cap/"

curi_examples:
  wsf-concept:Capability  →  https://wsf.world-semantic-foundation.org/concept/Capability
  wsf-rel:possesses       →  https://wsf.world-semantic-foundation.org/rel/possesses
```

CURIEs allow concise references while preserving URI compatibility.

---

## 7. Namespace Management

Each namespace is managed by an authority:

| Namespace | Authority | Scope |
|---|---|---|
| `wsf-concept:*` | WSF Core Concepts Authority | All WSF foundational concepts |
| `wsf-rel:*` | WSF Relationship Vocabulary Authority | All WSF relationships |
| `wsf-cap:*` | Capability Authority | All capabilities |
| `wsf-dis:*` | Disposition Authority | All dispositions |
| `wsf-ctx:*` | Context Authority | All contexts |
| `wsf-assertion:*` | Assertion Authority | All assertions |
| `wsf-ex:*` | Examples Authority | All examples |
| `wsf-id:*` | Identity Authority | All identity references |
| `wsf-time:*` | Time Authority | All time references |
| `wsf-space:*` | Space Authority | All space references |

Namespaces are governed, not free-for-all.

---

## 8. Identifier Assignment Rules

Identifier assignment SHALL follow:

1. **Provisional assignment**: Provisional identifier assigned when concept is candidate.
2. **Stabilization**: Identifier stabilizes when concept is Proposed.
3. **Normative**: Identifier becomes immutable at Normative status.
4. **Deprecated**: Old identifier is preserved (deprecated); new identifier for replacement.
5. **Retired**: Identifier is preserved for historical reference.

Per ADR-WSF-18, identifiers persist through compatible evolution.

---

## 9. Reference Resolution

References SHALL be resolvable:

```
Reference → Resolution Service → Concept/Specification
```

Resolution methods:
1. **Direct lookup**: Known identifier → concept.
2. **CURIE expansion**: CURIE → full URI → concept.
3. **Version-aware lookup**: Identifier + version → specification.
4. **Alias resolution**: Alias → canonical identifier.
5. **Cross-namespace mapping**: External identifier → WSF identifier.

---

## 10. Cross-Namespace Integration

External namespaces MAY integrate with WSF:

```
external-namespace:Concept
   ↓ maps-to
wsf-concept:Concept
```

Mapping is explicit and governed:
- One-to-one: External concept = WSF concept.
- One-to-many: External concept maps to multiple WSF concepts.
- Many-to-one: Multiple external concepts map to one WSF concept.
- Approximation: External concept approximates WSF concept.

Mappings are tracked with provenance.

---

## 11. Federated Namespaces

WSF SHALL support federated namespaces:

```
wsf:                  # WSF root namespace
   │
   ├── partner-org-a:  # Partner organization A
   │     └── partner-org-a:Concept
   │
   ├── partner-org-b:  # Partner organization B
   │     └── partner-org-b:Concept
   │
   └── partner-org-c:  # Partner organization C
         └── partner-org-c:Concept
```

Federated namespaces allow partner organizations to contribute concepts while preserving their authority.

---

## 12. Namespace Versioning

Namespaces SHALL have versions:

```
wsf-concept:Capability          # latest version
wsf-concept:Capability@v1.0.0   # specific version
```

Versioning follows ADR-WSF-16 (Semantic Evolution & Versioning).

---

## 13. Namespace Documentation

Every namespace SHALL have documentation:

```yaml
- namespace:
  prefix: wsf-concept
  uri: https://wsf.world-semantic-foundation.org/concept/
  authority: WSF Core Concepts Authority
  scope: All WSF foundational concepts
  documentation: https://github.com/World-Semantic-Foundation/wsf-governance/blob/main/...
  version: 1.0.0
  status: Normative
```

---

## 14. Reference Patterns in Semantic Assertions

References in assertions SHALL follow the pattern:

```yaml
- assertion:
  subject:
    semantic_id: wsf-ex:OTCHERE-Inc       # Subject reference
  relationship:
    semantic_id: wsf-rel:possesses         # Relationship reference
  object:
    semantic_id: wsf-cap:OTCHERE-OrderFulfillment  # Object reference
  context:
    semantic_id: wsf-ctx:enterprise        # Context reference
```

All four references are WSF identifiers.

---

## 15. Reference Governance

References SHALL be governed:

- **External references**: Approved by namespace authority.
- **Cross-namespace references**: Require explicit mapping.
- **Deprecated references**: Still resolvable but flagged.
- **Unresolvable references**: Flagged for investigation.

---

## 16. Implementation Implications

Upon Acceptance, subsequent CRs SHALL:

1. **CR-WSF-21.1**: Establish the URI scheme and resolution service.
2. **CR-WSF-21.2**: Define CURIE prefix registry.
3. **CR-WSF-21.3**: Establish namespace documentation requirements.
4. **CR-WSF-21.4**: Define cross-namespace mapping format.

---

## 17. Consequences

### Positive

- Identifiers are globally unique.
- References can be resolved.
- Cross-system integration is enabled.
- Federation is supported.
- Versioning is explicit.

### Negative

- Namespace management overhead.
- URI scheme commitment.
- Resolution service required.
- Mapping complexity.

These are accepted consequences.

---

## 18. Rejected Alternatives

### A — Local Identifiers Only

Rejected. Cannot integrate across systems.

### B — UUID Only

Rejected. Not human-readable.

### C — Uncontrolled Namespaces

Rejected. Leads to collisions.

### D — Implicit Namespaces

Rejected. Cannot resolve.

### E — Version in Every Identifier

Rejected. Identifier should be persistent.

---

## 19. Explicit Non-Decisions

This ADR does NOT decide:

- The exact URI scheme details (subsequent CRs).
- The resolution service implementation (governed by ADR-WSF-24).
- The full namespace list (initial set defined; grows through subsequent CRs).
- The federation protocols (subsequent CRs).

---

## 20. Decision Summary

The decision can be reduced to one sentence:

> **WSF identifiers are persistent, globally unique, resolvable references organized in a governed namespace hierarchy that supports versioning, federation, and cross-namespace integration.**

This is the foundation for unambiguous reference and integration.

---

## 21. Required Follow-On ADRs

The natural next steps are:

```
ADR-WSF-21 Namespace and Reference Model (this ADR)
       │
       ▼
ADR-WSF-22 Assertion and Provenance Model
       │
       ▼
ADR-WSF-23 Semantic Representation Architecture
```

---

*This ADR establishes the Namespace and Reference Model for WSF. Implementation proceeds through subsequent CRs.*
