# ADR-WSF-19 — Semantic Relationship Model

Status: Baseline
Program: World Semantic Foundation
Parent: ADR-WSF-18 — Concept Identity
Related: ADR-WSF-01, ADR-WSF-04, ADR-WSF-08, ADR-WSF-09, ADR-WSF-11, ADR-WSF-12, ADR-WSF-14, ADR-WSF-18
Decision Type: Foundational Semantic Architecture
Implementation: Implemented by the corresponding change request

---

## 1. Decision Statement

The World Semantic Foundation shall establish a **Semantic Relationship Model** that distinguishes semantic relationships from structural edges, governs how relationships participate in semantic assertions, and provides a controlled vocabulary of relationship types for foundational use.

The governing principle is:

> **A relationship in WSF carries semantic meaning, not merely structural connection.**

Semantic Relationships therefore:

- Have stable identities (per ADR-WSF-18);
- Have specified domains and ranges (the kinds of entities/concepts they connect);
- Have specified semantics (what they mean, not just how they connect);
- Are governed through the ADR/CR process;
- Participate in semantic assertions in controlled ways.

---

## 2. Why This Decision Is Necessary

The investigation established that relationships in semantic systems often collapse into two failure modes:

1. **Structural-only relationships**: Generic "related-to" edges with no specified meaning.
2. **Loose vocabulary**: Many named relationships with overlapping or ambiguous semantics.

Both failure modes produce a graph where traversal is possible but meaning is unclear. Without a Semantic Relationship Model:

- Assertions cannot be validated;
- Specialization chains cannot be inferred reliably;
- Cross-system integration loses meaning;
- Semantic queries return ambiguous results.

WSF therefore requires a model that distinguishes semantic relationships from structural edges.

---

## 3. Decision Drivers

The Semantic Relationship Model must provide:

- **Semantic identity**: Each relationship type has a stable identity.
- **Domain and range**: Each relationship specifies what it connects.
- **Symmetry/asymmetry**: Relationships know whether they are symmetric.
- **Transitivity (where applicable)**: Some relationships are transitive, others are not.
- **Inverse (where applicable)**: Some relationships have natural inverses.
- **Cardinality constraints**: 1:1, 1:N, N:M where appropriate.
- **Composition semantics**: Whether relationships compose.
- **Context applicability**: Where the relationship may apply.
- **Governance**: Relationships are governed through the ADR/CR process.
- **Composability**: Relationships can be combined in controlled ways.

---

## 4. Semantic Relationship Structure

A Semantic Relationship SHALL carry the following metadata:

```yaml
relationship:
  semantic_id: wsf-rel:<name>          # Stable identity
  preferred_name: Human-readable name
  aliases: [Alternative names]
  status: Candidate | Investigating | Proposed | Normative | Deprecated | Retired
  version: Semantic Version
  definition: Human-readable definition
  domain: What the relationship connects from
  range: What the relationship connects to
  properties:
    symmetric: boolean
    transitive: boolean
    antisymmetric: boolean
    functional: boolean
    inverse: wsf-rel:<name>             # if applicable
  cardinality: 1:1 | 1:N | N:1 | N:M
  constraints:
    - constraint description
  context_applicability: List of contexts
  specialization_of: wsf-rel:<parent>   # if applicable
  created: ISO timestamp
  last_modified: ISO timestamp
  authority: WSF
  provenance:
    source: Where the relationship originated
    asserted_by: Who established it
```

---

## 5. Relationship Categories

WSF SHALL distinguish the following categories of Semantic Relationships:

### 5.1 Structural Relationships

Connect entities to entities.

Examples:
- `wsf-rel:has-part` — entity composition
- `wsf-rel:is-part-of` — entity decomposition
- `wsf-rel:contains` — containment
- `wsf-rel:instantiates` — instance-of (Entity → Concept)

### 5.2 Semantically Significant Relationships

Connect entities/concepts with specific semantic meaning.

Examples:
- `wsf-rel:possesses` — Entity possesses Capability/Property
- `wsf-rel:has-capability` — Entity has Capability
- `wsf-rel:assumes-role` — Entity assumes Role
- `wsf-rel:realizes` — Activity realizes Outcome
- `wsf-rel:enables` — X enables Y
- `wsf-rel:produces` — Activity produces Outcome
- `wsf-rel:governs` — Authority governs Artifact
- `wsf-rel:specializes` — Concept specializes Concept
- `wsf-rel:asserts` — Subject asserts Assertion

### 5.3 Temporal Relationships

Connect events, states, and intervals in time.

Examples:
- `wsf-rel:before` — Event A before Event B
- `wsf-rel:after` — Event A after Event B
- `wsf-rel:during` — Event during Interval
- `wsf-rel:holds-during` — State holds during Interval

### 5.4 Causal Relationships

Connect causes and effects.

Examples:
- `wsf-rel:causes` — X causes Y
- `wsf-rel:enables` — X enables Y (cognitively)
- `wsf-rel:prevents` — X prevents Y
- `wsf-rel:triggers` — X triggers Y
- `wsf-rel:contributes-to` — X contributes to Y

### 5.5 Normative Relationships

Connect normative semantic elements.

Examples:
- `wsf-rel:obligates` — Agreement obligates Party
- `wsf-rel:authorizes` — Authority authorizes Action
- `wsf-rel:permits` — Permit allows Action
- `wsf-rel:prohibits` — Prohibition disallows Action

### 5.6 Provenance Relationships

Connect semantic artifacts to their origins.

Examples:
- `wsf-rel:asserted-by` — Assertion asserted by Agent
- `wsf-rel:derived-from` — Assertion derived from Source
- `wsf-rel:supported-by` — Assertion supported by Evidence

### 5.7 Identity Relationships

Connect identities.

Examples:
- `wsf-rel:same-as` — X is identical to Y
- `wsf-rel:specializes` — Concept specializes Concept
- `wsf-rel:supersedes` — X supersedes Y

---

## 6. Relationship Pattern in Semantic Assertions

Per ADR-WSF-12, semantic assertions follow:

```
Subject ──Relationship──► Object
```

The Relationship element MUST:
- Be drawn from the governed vocabulary (this ADR);
- Have specified domain (must match Subject's type);
- Have specified range (must match Object's type);
- Carry semantic identity (per ADR-WSF-18);
- Be contextually appropriate.

This pattern is foundational to WSF semantic assertions.

---

## 7. Relationship Properties

### 7.1 Symmetry

A relationship is symmetric if X-R-Y implies Y-R-X.

Example: `same-as` is symmetric.

### 7.2 Transitivity

A relationship is transitive if X-R-Y and Y-R-Z implies X-R-Z.

Example: `is-part-of` may be transitive in some contexts; `same-as` is transitive.

### 7.3 Antisymmetry

A relationship is antisymmetric if X-R-Y and Y-R-X implies X=Y.

Example: `is-parent-of` is antisymmetric.

### 7.4 Functionality

A relationship is functional if each X has at most one Y such that X-R-Y.

Example: `has-biological-mother` is functional.

### 7.5 Inverse

Some relationships have natural inverses.

Example: `contains` is inverse of `is-contained-in`.

---

## 8. Relationship Composition

Semantic Relationships MAY compose to form more complex relationships:

```
A -possesses→ B
B -has-part→ C
   ↓
A -possesses (transitively)→ C
```

Composition rules SHALL be specified per relationship. Some relationships compose; others do not.

---

## 9. Relationship Specialization

Semantic Relationships MAY be specialized:

```
wsf-rel:enables (parent)
   ↓ specializes
wsf-rel:enables-architecturally
wsf-rel:enables-operationally
```

Specialization follows the same rules as Concept specialization (per ADR-WSF-04).

---

## 10. Context-Dependent Relationships

A relationship MAY apply only in specific contexts:

```
wsf-rel:governs
   applies-in:
     - enterprise-context
     - regulatory-context
   not-applicable-in:
     - informal-context
```

This is governed by Context applicability metadata.

---

## 11. Relationships vs Properties (Critical Distinction)

| Aspect | Relationship | Property |
|---|---|---|
| **Connects** | Two entities/concepts | One entity to a value |
| **Example** | `OTCHERE possesses Capability` | `OTCHERE has Name = "OTCHERE Inc"` |
| **Identity** | Has its own semantic identity | Is a characteristic of the entity |
| **Range** | Entity/Concept (usually) | Value (often literal) |
| **Governance** | Governed vocabulary | Governed schema |

Both are needed. The distinction matters for ontology engineering.

---

## 12. Initial Foundational Relationship Set

Per the investigation, the following relationships form the initial foundational set:

**Structural:**
- `wsf-rel:has-part`
- `wsf-rel:is-part-of`
- `wsf-rel:contains`
- `wsf-rel:instantiates`

**Semantically Significant:**
- `wsf-rel:possesses`
- `wsf-rel:has-capability`
- `wsf-rel:assumes-role`
- `wsf-rel:realizes`
- `wsf-rel:produces`
- `wsf-rel:enables`
- `wsf-rel:specializes`
- `wsf-rel:governs`
- `wsf-rel:asserts`

**Temporal:**
- `wsf-rel:before`
- `wsf-rel:after`
- `wsf-rel:during`
- `wsf-rel:holds-during`

**Causal:**
- `wsf-rel:causes`
- `wsf-rel:triggers`
- `wsf-rel:contributes-to`

**Normative:**
- `wsf-rel:obligates`
- `wsf-rel:authorizes`
- `wsf-rel:permits`
- `wsf-rel:prohibits`

**Provenance:**
- `wsf-rel:asserted-by`
- `wsf-rel:derived-from`
- `wsf-rel:supported-by`

**Identity:**
- `wsf-rel:same-as`
- `wsf-rel:supersedes`

This initial set SHALL be refined through subsequent ADRs.

---

## 13. Relationship Validation

Relationships SHALL be validated through:

1. **Domain validation**: Subject type matches relationship domain.
2. **Range validation**: Object type matches relationship range.
3. **Cardinality validation**: Cardinality constraints satisfied.
4. **Symmetry/Transitivity validation**: Mathematical properties hold.
5. **Context validation**: Relationship applies in the asserted context.
6. **Identity validation**: Relationship identity is known.

---

## 14. Implementation Implications

Upon Acceptance, subsequent CRs SHALL:

1. **CR-WSF-19.1**: Establish the initial relationship set with full metadata.
2. **CR-WSF-19.2**: Define relationship validation algorithms.
3. **CR-WSF-19.3**: Establish relationship composition rules.
4. **CR-WSF-19.4**: Define relationship specialization patterns.

---

## 15. Consequences

### Positive

- Relationships carry explicit semantics.
- Assertions can be validated.
- Specialization chains are traceable.
- Cross-system integration preserves meaning.
- Mathematical properties (symmetry, transitivity) are explicit.
- Relationship composition is controlled.
- Domain and range constraints prevent nonsense connections.

### Negative

- Relationship vocabulary is limited (controlled).
- Adding new relationships requires governance.
- Validation overhead.
- Cardinality constraints may be restrictive in some cases.

These are accepted consequences.

---

## 16. Rejected Alternatives

### A — Generic "Related-To"

Rejected. Loses all semantic information.

### B — Uncontrolled Vocabulary

Rejected. Leads to ambiguity and overlap.

### C — Property-Only Model

Rejected. Cannot express relationships between entities.

### D — Untyped Edges

Rejected. Loses domain/range constraints.

### E — Implicit Relationships

Rejected. Cannot be validated or reasoned over.

---

## 17. Explicit Non-Decisions

This ADR does NOT decide:

- The complete relationship vocabulary (initial set defined; full set grows through subsequent CRs).
- The exact validation algorithms (subsequent CRs).
- The composition rules for each relationship (subsequent CRs).
- The serialization format for relationships (governed by ADR-WSF-23).
- The query language semantics (governed by ADR-WSF-24).

---

## 18. Decision Summary

The decision can be reduced to one sentence:

> **Semantic Relationships in WSF are governed vocabulary items with stable identities, specified domains and ranges, explicit mathematical properties, and controlled semantics — not generic edges.**

This is the foundation for assertion validation, semantic query, and cross-system integration.

---

## 19. Required Follow-On ADRs

The natural next steps are:

```
ADR-WSF-19 Semantic Relationship Model (this ADR)
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

*This ADR establishes the model for Semantic Relationships in WSF. Implementation proceeds through subsequent CRs.*
