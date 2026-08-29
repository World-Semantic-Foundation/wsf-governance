# ADR-WSF-18 — Concept Identity

Status: Proposed
Program: World Semantic Foundation
Parent: ADR-WSF-17 — Foundational Semantic Architecture
Implements: CR-WSF-17 Rev.1 §31 (Next Implementation ADRs)
Related: ADR-WSF-01, ADR-WSF-02, ADR-WSF-09, ADR-WSF-10, ADR-WSF-11, ADR-WSF-12, ADR-WSF-16
Decision Type: Foundational Semantic Architecture
Implementation: Authorized upon Acceptance (via subsequent CRs)

---

## 1. Decision Statement

The World Semantic Foundation shall establish **Concept Identity** as the foundational mechanism through which semantic meaning persists across representations, contexts, versions, lifecycles, and integration boundaries.

The governing principle is:

> **A semantic concept is identified by its meaning, not by its name, label, representation, or location.**

Concept Identity therefore enables:

- Concepts to be referenced unambiguously across WSF, downstream systems, and integration partners;
- The same identity to survive representation changes (YAML ↔ JSON-LD ↔ RDF ↔ OWL);
- The same identity to survive context changes (universal ↔ enterprise ↔ domain);
- The same identity to be tracked through version evolution;
- Concepts to be distinguished from each other even when labels collide;
- Concepts to be deprecated without losing their historical identity.

---

## 2. Why This Decision Is Necessary

WSF must support a large number of semantic concepts, relationships, specializations, and contexts. The investigation has shown that:

- **The same name does not establish semantic identity** (per INV-R16, ADR-WSF-10);
- **Names collide across domains** (e.g., "Capability" in business, IT, AI);
- **Semantic evolution is governed** (per ADR-WSF-16) and requires stable identity through evolution;
- **Specialization creates new concepts** (per ADR-WSF-04, ADR-WSF-14) that must remain traceable to their parents;
- **Integration with downstream systems** (OpenDEA, Assessment-Models, etc.) requires unambiguous reference.

Without an explicit Concept Identity model, the following problems emerge:

1. **Semantic collision**: Two concepts share a name but mean different things.
2. **Identity loss**: A concept "evolves" and silently becomes a different concept.
3. **Reference ambiguity**: A reference cannot be resolved to a specific concept.
4. **Concealed divergence**: Concepts with the same name drift apart through version changes.
5. **Integration confusion**: Downstream systems refer to concepts using different schemes.

Concept Identity is therefore a foundational requirement.

---

## 3. Decision Drivers

Concept Identity must provide:

- **Persistence**: Identity survives changes in representation.
- **Uniqueness**: Each concept has exactly one identity.
- **Resolvability**: Identity can be resolved to a specific concept.
- **Stability**: Identity is stable through compatible evolution.
- **Traceability**: New identities can be traced to parent identities.
- **Namespace compatibility**: Identity works across multiple namespaces.
- **Machine readability**: Identity is machine-resolvable.
- **Human readability**: Identity is meaningful to humans.
- **Governance**: Identity is governed through the ADR/CR process.

---

## 4. Concept Identity Model

WSF SHALL distinguish:

```
Concept Identity (the stable, persistent identity)
   │
   ├── References (ways to refer to the identity)
   │     ├── URI (canonical machine reference)
   │     ├── IRI (internationalized URI)
   │     ├── Namespaced Identifier (e.g., wsf:Capability)
   │     ├── CURIEs (compact URIs)
   │     └── Human-readable labels (preferred name, aliases)
   │
   ├── Semantic Specification (the meaning)
   │     ├── Definition
   │     ├── Constraints
   │     ├── Relationships
   │     ├── Scope
   │     └── Context applicability
   │
   ├── Status (governance state)
   │     ├── Candidate
   │     ├── Investigating
   │     ├── Proposed
   │     ├── Normative
   │     ├── Deprecated
   │     └── Retired
   │
   └── Version (evolution)
         ├── Semantic Version
         ├── Specification Version
         └── Representation Version
```

These four components are distinct and SHALL NOT be conflated.

---

## 5. Concept Identity Lifecycle

```
1. Concept Candidate Identified
       ↓
2. Identity Assigned (provisional)
       ↓
3. Semantic Specification Drafted
       ↓
4. Identity Stabilized (upon Proposed status)
       ↓
5. Identity Normative (upon Accepted ADR)
       ↓
6a. Identity Persists (through compatible evolution)
6b. Identity Replaced (semantic breaking change)
6c. Identity Deprecated (no longer recommended)
6d. Identity Retired (preserved for historical reference)
```

---

## 6. Identity Persistence Through Evolution

Per ADR-WSF-16, semantic identity MUST persist through compatible evolution.

| Evolution Type | Identity Behavior |
|---|---|
| **Clarification** | Identity persists; specification updated |
| **Correction** | Identity may persist if intended meaning restored |
| **Extension** | Identity persists; new semantics added |
| **Constraint change (compatible)** | Identity persists |
| **Constraint change (breaking)** | New identity; old deprecated |
| **Scope change (compatible)** | Identity persists |
| **Scope change (breaking)** | New identity; old deprecated |
| **Meaning change** | New identity; old deprecated/superseded |

---

## 7. Identifier Scheme

WSF SHALL adopt the following identifier scheme (subject to refinement by ADR-WSF-21):

```
wsf:<concept-name>           # For WSF Tier 1/2 concepts
wsf:<domain>:<concept-name>  # For domain concepts
wsf-ex:<example-id>          # For WSF examples
wsf-assertion:<assertion-id> # For WSF assertions
wsf-cap:<capability-id>      # For capabilities
wsf-rel:<relationship-id>    # For relationships
```

Examples:
- `wsf:Entity`
- `wsf:Capability`
- `wsf:Disposition`
- `wsf-rel:possesses`
- `wsf-rel:enables`
- `wsf-cap:OrderFulfillment`
- `wsf-ex:OTCHERE-Inc`

---

## 8. Identity Resolution

Concept Identity SHALL be resolvable through:

1. **Direct lookup**: Identity → Semantic Specification
2. **Reverse lookup**: Name/alias → Identity (with disambiguation)
3. **Cross-namespace lookup**: External identity → WSF identity (via mapping)
4. **Version-aware lookup**: Identity + Version → Specification
5. **Status-aware lookup**: Identity + Status → Specification (when applicable)

---

## 9. Relationship to Identity (the Foundational Concept)

Note the careful distinction:

- **Concept Identity** = the identity assigned to a semantic concept
- **Identity** (the WSF concept) = the broader semantic concept of distinguishability

The WSF concept `Identity` (in `wsf/concepts/identity.md`) describes what it means for any entity to have an identity. **Concept Identity** (this ADR) is the specific application of `Identity` to semantic concepts.

These are related but distinct concerns. This ADR governs Concept Identity; the Identity concept itself is governed separately.

---

## 10. Relationship to Specialization (ADR-WSF-04)

When a concept is specialized:

```
WSF:Capability (parent)
   ↓ specializes
OpenDEA:BusinessCapability (child)
```

The child receives its **own** Concept Identity. The child's identity MUST reference the parent's identity through a `specializes` relationship.

This ensures:
- Each concept has a unique identity;
- Parent-child relationships are traceable;
- Specialization cannot be silent.

---

## 11. Relationship to Versioning (ADR-WSF-16)

Per ADR-WSF-16, semantic versioning records the evolution of a semantic definition. Concept Identity is the constant; the version is the variable.

Example:
```
wsf:Capability
   Version 1.0.0 — initial normative
   Version 1.1.0 — added clarification (identity persists)
   Version 2.0.0 — breaking change (identity persists with v2 mark, v1 deprecated)
```

---

## 12. Relationship to Context (ADR-WSF-14)

Per ADR-WSF-14, context may constrain or specialize meaning but MUST NOT silently redefine it.

Concept Identity supports context through:

- **Identity persists across contexts** (universal meaning is preserved);
- **Context-specific identities are derived** (e.g., `wsf-context:enterprise:Capability`);
- **Context boundaries are explicit** (an identity is bound to its applicable contexts).

---

## 13. Concept Identity Metadata

Every Concept Identity SHALL carry the following metadata:

```yaml
concept_identity:
  semantic_id: wsf:<concept-name>           # The stable identity
  type: Concept | Relationship | Assertion | Context | etc.
  preferred_name: Human-readable name
  aliases: [Alternative names]
  status: Candidate | Investigating | Proposed | Normative | Deprecated | Retired
  version: Semantic Version (per ADR-WSF-16)
  definition: Human-readable definition
  specification_ref: Path to semantic specification
  authority: Who governs this concept
  parent: Parent concept identity (if specialized)
  context_applicability: List of applicable contexts
  created: ISO timestamp
  last_modified: ISO timestamp
  superseded_by: New identity (if deprecated/superseded)
  provenance:
    source: Where the concept originated
    asserted_by: Who established it
    authority: Governance authority
```

---

## 14. Identity Collision Resolution

When two concepts share an identity (collision):

1. **Detection**: The collision is identified through identity resolution.
2. **Investigation**: Determine whether:
   - The concepts are truly identical (merge them);
   - The concepts are semantically distinct (separate them);
   - One is a specialization of the other (formalize hierarchy).
3. **Resolution**: Apply the appropriate fix.
4. **Documentation**: Record the decision in an ADR.

When two concepts share a name but not identity:

1. **Detection**: Reverse lookup reveals the collision.
2. **Resolution**: Either:
   - One concept adopts a different name;
   - Context-specific labels are introduced;
   - The collision is documented and accepted (e.g., `Capability` in different namespaces).

---

## 15. Implementation Implications

Upon Acceptance, subsequent CRs SHALL:

1. **CR-WSF-18.1**: Apply Concept Identity to existing WSF concepts (Entity, Capability).
2. **CR-WSF-18.2**: Establish identity metadata for all existing assets.
3. **CR-WSF-18.3**: Define identifier scheme in detail (with ADR-WSF-21).
4. **CR-WSF-18.4**: Establish identity resolution APIs (with ADR-WSF-24).

---

## 16. Consequences

### Positive

- Concepts can be unambiguously referenced.
- Semantic meaning persists across representations.
- Specialization is traceable.
- Evolution is governed.
- Integration is explicit.
- Naming collisions can be resolved.
- Historical assertions remain interpretable.
- Machine-readable reference is enabled.

### Negative

- Identity management is added governance overhead.
- Identifier scheme must be agreed upon.
- Concept Identity metadata must be maintained.
- Cross-namespace mapping may be required.
- Resolution performance must be considered.

These are accepted consequences.

---

## 17. Rejected Alternatives

### A — Identity by Name

Rejected. Names collide, change, and are not stable.

### B — Identity by Location

Rejected. Locations change (repository moves, renames).

### C — Identity by Version

Rejected. Version is variable; identity must be persistent.

### D — Identity by Representation

Rejected. Representations change; meaning persists.

### E — Identity by Context

Rejected. Concepts may apply across contexts.

### F — Implicit Identity

Rejected. Implicit identity is fragile and creates hidden collisions.

---

## 18. Explicit Non-Decisions

This ADR does NOT decide:

- The exact identifier syntax (governed by ADR-WSF-21);
- The resolution API design (governed by ADR-WSF-24);
- The full metadata schema (governed by ADR-WSF-22);
- The cross-namespace mapping format (governed by subsequent ADRs);
- The URI scheme details (e.g., HTTPS, URN, or custom);
- The persistent identifier service (e.g., w3id.org, custom).

---

## 19. Decision Summary

The decision can be reduced to one sentence:

> **Concept Identity is the persistent, meaning-based identifier for every semantic concept, surviving representation, context, version, and lifecycle changes.**

This is the foundation upon which all subsequent semantic infrastructure can reliably reference, version, specialize, and integrate WSF concepts.

---

## 20. Required Follow-On ADRs

The natural next steps are:

```
ADR-WSF-18 Concept Identity (this ADR)
       │
       ▼
ADR-WSF-19 Semantic Relationship Model
       │
       ▼
ADR-WSF-20 Concept Definition Model
       │
       ▼
ADR-WSF-21 Namespace and Reference Model
       │
       ▼
ADR-WSF-22 Assertion and Provenance Model
```

---

*Per CR-WSF-17 Rev.1 §33: "CR-WSF-17 Rev. 1 establishes the implementation foundation, not the final WSF ontology. It authorizes construction of the environment in which the authoritative semantic foundation can be developed safely."*

*This ADR (ADR-WSF-18) is part of that constructive process.*
