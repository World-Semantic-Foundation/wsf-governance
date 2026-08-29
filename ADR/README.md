# Architectural Decision Records (ADRs)

> **The 18 ADRs that constitute WSF's architectural foundation.**

All ADRs are immutable historical records once Accepted. Changes occur through subsequent ADRs, not by modifying existing ones. Each ADR implements the [8-stage change control lifecycle](../GOVERNANCE/CHANGE-CONTROL-LIFECYCLE.md).

---

## ADR Index

| ADR | Decision | Status | Status Date |
|---|---|---|---|
| [ADR-WSF-01](./ADR-WSF-01-WSF-Foundational-Position.md) | WSF Foundational Position | Proposed | 2026-08-29 |
| [ADR-WSF-02](./ADR-WSF-02-Semantic-Layering.md) | Semantic Layering | Proposed | 2026-08-29 |
| [ADR-WSF-03](./ADR-WSF-03-Semantic-Authority.md) | Semantic Authority | Proposed | 2026-08-29 |
| [ADR-WSF-04](./ADR-WSF-04-Semantic-Inheritance.md) | Semantic Inheritance | Proposed | 2026-08-29 |
| [ADR-WSF-05](./ADR-WSF-05-Semantic-Assertion.md) | Semantic Assertion | Proposed | 2026-08-29 |
| [ADR-WSF-06](./ADR-WSF-06-Evidence-Provenance.md) | Evidence & Provenance | Proposed | 2026-08-29 |
| [ADR-WSF-07](./ADR-WSF-07-Capacity-Ability-Capability.md) | Capacity–Ability–Capability | Proposed | 2026-08-29 |
| [ADR-WSF-08](./ADR-WSF-08-Foundational-Concept-Relationships.md) | Foundational Concept Relationships | Proposed | 2026-08-29 |
| [ADR-WSF-09](./ADR-WSF-09-Foundational-Concept-Taxonomy.md) | Foundational Concept Taxonomy | Proposed | 2026-08-29 |
| [ADR-WSF-10](./ADR-WSF-10-Semantic-Identity-Naming.md) | Semantic Identity & Naming | Proposed | 2026-08-29 |
| [ADR-WSF-11](./ADR-WSF-11-Semantic-Concept-Specification.md) | Semantic Concept Specification | Proposed | 2026-08-29 |
| [ADR-WSF-12](./ADR-WSF-12-Semantic-Assertion-Model.md) | Semantic Assertion Model | Proposed | 2026-08-29 |
| [ADR-WSF-13](./ADR-WSF-13-Semantic-Constraints-Validation.md) | Semantic Constraints & Validation | Proposed | 2026-08-29 |
| [ADR-WSF-14](./ADR-WSF-14-Semantic-Context-Boundary.md) | Semantic Context & Boundary | Proposed | 2026-08-29 |
| [ADR-WSF-15](./ADR-WSF-15-Semantic-Authority-Governance.md) | Semantic Authority & Governance | Proposed | 2026-08-29 |
| [ADR-WSF-16](./ADR-WSF-16-Semantic-Evolution-Versioning.md) | Semantic Evolution & Versioning | Proposed | 2026-08-29 |
| [ADR-WSF-17](./ADR-WSF-17-Foundational-Semantic-Architecture.md) | Foundational Semantic Architecture | **Accepted** | 2026-08-29 |
| [ADR-WSF-18](./ADR-WSF-18-Concept-Identity.md) | Concept Identity | **Proposed** | 2026-08-29 |

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
ADR-WSF-10  Semantic Identity & Naming        (Identity)
   ↓
ADR-WSF-11  Semantic Concept Specification    (Specification)
   ↓
ADR-WSF-12  Semantic Assertion Model          (Full Assertion)
   ↓
ADR-WSF-13  Semantic Constraints & Validation (Validity)
   ↓
ADR-WSF-14  Semantic Context & Boundary       (Context)
   ↓
ADR-WSF-15  Semantic Authority & Governance   (Governance)
   ↓
ADR-WSF-16  Semantic Evolution & Versioning   (Evolution)
   ↓
ADR-WSF-17  Foundational Semantic Architecture (Implementation Gate) ★ ACCEPTED
   ↓
ADR-WSF-18  Concept Identity                   (Identity Foundation) ★ NEW
   ↓
ADR-WSF-19  Semantic Relationship Model        (Relationship Grammar)
   ↓
ADR-WSF-20  Concept Definition Model           (Formal Specification)
   ↓
ADR-WSF-21  Namespace & Reference Model        (Identifier Scheme)
   ↓
ADR-WSF-22  Assertion & Provenance Model       (Assertion Support)
   ↓
ADR-WSF-23  Semantic Representation Architecture (Format Strategy)
   ↓
ADR-WSF-24  WSF Software Architecture          (Engine Design)
   ↓
ADR-WSF-25  WSF Integration Architecture       (Connector Design)
   ↓
ADR-WSF-26  WSF Visualization Architecture     (Visual Asset Design)
   ↓
ADR-WSF-27  WSF Digital Twin & Simulation Architecture (Realization Design)
```

---

## Themes (per Investigation)

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
| **Identity Foundation** | ADR-WSF-18 (NEW) |

---

## How to Add a New ADR

1. Use the [ADR Template](../templates/ADR-TEMPLATE.md)
2. Place in `wsf-governance/ADR/` with sequential number
3. Update this index
4. Status begins as `Proposed`
5. Transition through `Candidate → Investigating → Proposed → Normative` per the [Semantic Status Model](../GOVERNANCE/SEMANTIC-STATUS-MODEL.md)
6. Once Accepted, ADRs are immutable

---

## Conflict Resolution

When ADRs appear to conflict:
1. **Later ADRs supersede earlier** (if explicitly stated)
2. **Domain-specific ADRs** take precedence within their domain
3. **Foundational ADRs** (WSF-01..07) take precedence over specialized ADRs
4. **Unresolved conflicts** require a new ADR to reconcile

---

## Related Documents

- [GOVERNANCE/CHANGE-CONTROL-LIFECYCLE.md](../GOVERNANCE/CHANGE-CONTROL-LIFECYCLE.md) — The 8-stage lifecycle
- [GOVERNANCE/SEMANTIC-STATUS-MODEL.md](../GOVERNANCE/SEMANTIC-STATUS-MODEL.md) — The 6-stage status model
- [RESEARCH/INVESTIGATION-RECORD.md](../RESEARCH/INVESTIGATION-RECORD.md) — The 10 investigations behind these ADRs
- [templates/ADR-TEMPLATE.md](../templates/ADR-TEMPLATE.md) — Template for new ADRs

---

*ADRs are the authoritative architectural decisions of WSF. They are immutable once Accepted.*
