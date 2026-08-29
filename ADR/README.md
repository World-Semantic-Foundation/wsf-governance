# Architectural Decision Records (ADRs)

> **The 22 architectural decision records that constitute the WSF architectural foundation.**

Each ADR documents an architectural decision in the World Semantic Foundation. ADRs are immutable historical records once finalized; changes occur through subsequent ADRs.

The full architectural lineage is preserved through the investigation record.

---

## ADR Index

| ADR | Decision | Status |
|---|---|---|
| [ADR-WSF-01](./ADR-WSF-01-WSF-Foundational-Position.md) | WSF Foundational Position | Baseline |
| [ADR-WSF-02](./ADR-WSF-02-Semantic-Layering.md) | Semantic Layering | Baseline |
| [ADR-WSF-03](./ADR-WSF-03-Semantic-Authority.md) | Semantic Authority | Baseline |
| [ADR-WSF-04](./ADR-WSF-04-Semantic-Inheritance.md) | Semantic Inheritance | Baseline |
| [ADR-WSF-05](./ADR-WSF-05-Semantic-Assertion.md) | Semantic Assertion | Baseline |
| [ADR-WSF-06](./ADR-WSF-06-Evidence-Provenance.md) | Evidence & Provenance | Baseline |
| [ADR-WSF-07](./ADR-WSF-07-Capacity-Ability-Capability.md) | Capacity:Ability:Capability | Baseline |
| [ADR-WSF-08](./ADR-WSF-08-Foundational-Concept-Relationships.md) | Foundational Concept Relationships | Baseline |
| [ADR-WSF-09](./ADR-WSF-09-Foundational-Concept-Taxonomy.md) | Foundational Concept Taxonomy | Baseline |
| [ADR-WSF-10](./ADR-WSF-10-Semantic-Identity-Naming.md) | Semantic Identity & Naming | Baseline |
| [ADR-WSF-11](./ADR-WSF-11-Semantic-Concept-Specification.md) | Semantic Concept Specification | Baseline |
| [ADR-WSF-12](./ADR-WSF-12-Semantic-Assertion-Model.md) | Semantic Assertion Model | Baseline |
| [ADR-WSF-13](./ADR-WSF-13-Semantic-Constraints-Validation.md) | Semantic Constraints & Validation | Baseline |
| [ADR-WSF-14](./ADR-WSF-14-Semantic-Context-Boundary.md) | Semantic Context & Boundary | Baseline |
| [ADR-WSF-15](./ADR-WSF-15-Semantic-Authority-Governance.md) | Semantic Authority & Governance | Baseline |
| [ADR-WSF-16](./ADR-WSF-16-Semantic-Evolution-Versioning.md) | Semantic Evolution & Versioning | Baseline |
| [ADR-WSF-17](./ADR-WSF-17-Foundational-Semantic-Architecture.md) | Foundational Semantic Architecture | Final |
| [ADR-WSF-18](./ADR-WSF-18-Concept-Identity.md) | Concept Identity | Baseline |
| [ADR-WSF-19](./ADR-WSF-19-Semantic-Relationship-Model.md) | Semantic Relationship Model | Baseline |
| [ADR-WSF-20](./ADR-WSF-20-Concept-Definition-Model.md) | Concept Definition Model | Baseline |
| [ADR-WSF-21](./ADR-WSF-21-Namespace-Reference-Model.md) | Namespace & Reference Model | Baseline |
| [ADR-WSF-22](./ADR-WSF-22-Assertion-Provenance-Model.md) | Assertion & Provenance Model | Baseline |

---

## Dependency Chain

```
ADR-WSF-01  WSF Foundational Position           (Foundation)
   ↓
ADR-WSF-02  Semantic Layering                  (Layering)
   ↓
ADR-WSF-03  Semantic Authority                 (Authority Boundaries)
   ↓
ADR-WSF-04  Semantic Inheritance               (Specialization)
   ↓
ADR-WSF-05  Semantic Assertion                 (Claims)
   ↓
ADR-WSF-06  Evidence & Provenance              (Support)
   ↓
ADR-WSF-07  Capacity–Ability–Capability        (Disposition)
   ↓
ADR-WSF-08  Foundational Concept Relationships (Grammar)
   ↓
ADR-WSF-09  Foundational Concept Taxonomy      (Classification)
   ↓
ADR-WSF-10  Semantic Identity & Naming         (Identity)
   ↓
ADR-WSF-11  Semantic Concept Specification     (Specification)
   ↓
ADR-WSF-12  Semantic Assertion Model           (Full Assertion)
   ↓
ADR-WSF-13  Semantic Constraints & Validation  (Validity)
   ↓
ADR-WSF-14  Semantic Context & Boundary        (Context)
   ↓
ADR-WSF-15  Semantic Authority & Governance    (Governance)
   ↓
ADR-WSF-16  Semantic Evolution & Versioning    (Evolution)
   ↓
ADR-WSF-17  Foundational Semantic Architecture  (Foundation) ★ FINAL
   ↓
ADR-WSF-18  Concept Identity                    (Identity Foundation)
   ↓
ADR-WSF-19  Semantic Relationship Model         (Relationship Grammar)
   ↓
ADR-WSF-20  Concept Definition Model            (Formal Specification)
   ↓
ADR-WSF-21  Namespace & Reference Model         (Identifier Scheme)
   ↓
ADR-WSF-22  Assertion & Provenance Model        (Assertion Support)
   ↓
ADR-WSF-23  Semantic Representation Architecture (Format Strategy)
   ↓
ADR-WSF-24  WSF Software Architecture           (Engine Design)
   ↓
ADR-WSF-25  WSF Integration Architecture        (Connector Design)
   ↓
ADR-WSF-26  WSF Visualization Architecture      (Visual Asset Design)
   ↓
ADR-WSF-27  WSF Digital Twin & Simulation Architecture (Realization Design)
```

---

## Themes

| Theme | ADRs |
|---|---|
| **Position & Layering** | ADR-WSF-01, ADR-WSF-02 |
| **Authority & Inheritance** | ADR-WSF-03, ADR-WSF-04 |
| **Assertion & Evidence** | ADR-WSF-05, ADR-WSF-06 |
| **Capability & Capacity** | ADR-WSF-07 |
| **Relationships & Taxonomy** | ADR-WSF-08, ADR-WSF-09 |
| **Identity & Specification** | ADR-WSF-10, ADR-WSF-11 |
| **Assertion Model & Validation** | ADR-WSF-12, ADR-WSF-13 |
| **Context & Governance** | ADR-WSF-14, ADR-WSF-15 |
| **Evolution & Architecture** | ADR-WSF-16, ADR-WSF-17 |
| **Identity Foundation** | ADR-WSF-18 |
| **Relationship Model** | ADR-WSF-19 |
| **Concept Definition** | ADR-WSF-20 |
| **Namespace & Reference** | ADR-WSF-21 |
| **Assertion & Provenance** | ADR-WSF-22 |

---

## Authoring New ADRs

1. Use the [ADR Template](../templates/ADR-TEMPLATE.md).
2. Place in `wsf-governance/ADR/` with a sequential number.
3. Update this index.
4. Status begins as **Baseline**.
5. Transitions through the [Semantic Status Model](../GOVERNANCE/SEMANTIC-STATUS-MODEL.md).
6. Once **Final**, ADRs are immutable.

---

## Conflict Resolution

When ADRs appear to conflict:

1. **Later ADRs supersede earlier** (if explicitly stated)
2. **Domain-specific ADRs** take precedence within their domain
3. **Foundational ADRs** (WSF-01..07) take precedence over specialized ADRs
4. **Unresolved conflicts** are resolved by a new ADR

---

## Related Documents

- [GOVERNANCE/CHANGE-CONTROL-LIFECYCLE.md](../GOVERNANCE/CHANGE-CONTROL-LIFECYCLE.md) : The 8-stage lifecycle
- [GOVERNANCE/SEMANTIC-STATUS-MODEL.md](../GOVERNANCE/SEMANTIC-STATUS-MODEL.md) : The 6-stage status model
- [RESEARCH/INVESTIGATION-RECORD.md](../RESEARCH/INVESTIGATION-RECORD.md) : The 10 investigations behind these ADRs
- [templates/ADR-TEMPLATE.md](../templates/ADR-TEMPLATE.md) : Template for new ADRs

---

*ADRs are the authoritative architectural record of WSF. They are immutable once Final.*
