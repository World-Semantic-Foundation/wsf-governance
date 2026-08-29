# WSF Investigation Record

> **The research lineage that produced the WSF architectural foundation.**

This document preserves the 10 investigations that constitute the research foundation of WSF. The investigations are historical records of how the foundational semantic architecture was developed.

---

## The 10 Investigations

The foundational semantic architecture derives from 10 coordinated investigations:

| # | Investigation | Focus |
|---|---|---|
| 1 | WSF Foundational Semantic Architecture | Position, layers, scope, boundaries |
| 2 | WSF Semantic Authority | Authority boundaries, governance hierarchy |
| 3 | WSF Semantic Inheritance | Specialization, conformance, derived concepts |
| 4 | WSF Semantic Assertion | Claim structure, evidence, provenance |
| 5 | WSF Semantic Mechanism Boundary | Mechanism vs concept distinction |
| 6 | WSF Semantic Ontology Boundary | Foundation vs formal ontology distinction |
| 7 | WSF Semantic Governance & Authority | Cross-repository governance, lifecycle |
| 8 | WSF Foundational Spine | Entity → Role → Capability → Value chain |
| 9 | WSF Structure-Means | System, Resource, Service, Process, Workflow |
| 10 | WSF Representation-Knowledge | Entity, Concept, Information, Data distinction |

Each investigation produced findings that fed into the architectural decision records.

---

## Investigation 1 : WSF Foundational Semantic Architecture

**Question:** What is the appropriate scope and structure of a world semantic foundation?

**Findings:**

- WSF is a semantic foundation, not an enterprise architecture, ontology, or domain repository.
- The foundation distinguishes Existence, Occurrence, Condition, Relation, Identity, Semantics, Proposition, Assertion, Qualification, Temporality, Spatiality, Epistemics as foundational domains.
- The foundation is layered: Kernel (minimal machinery) + Foundational Concepts (reusable building blocks) + Semantic Mechanisms (how things happen) + Domain Concepts (specialized compositions).
- The foundation is minimal : it provides the smallest sufficiently expressive base from which all domain semantics derive.

**Architectural Outcome:** Established the 4-layer foundation model (L0:L8).

## Investigation 2 : WSF Semantic Authority

**Question:** Who is authoritative for which kind of semantic asset?

**Findings:**

- WSF is authoritative for world-level semantic definitions.
- Semantic Architecture is authoritative for semantic organization and composition.
- Ontology Architecture is authoritative for formal representations.
- ESS/EO are authoritative for enterprise semantic specialization.
- OpenDEA is authoritative for enterprise architecture specialization.
- Assessment-Models is authoritative for maturity-model governance.
- Authority follows semantic responsibility, not repository location.

**Architectural Outcome:** Established the 7-authority model.

## Investigation 3 : WSF Semantic Inheritance

**Question:** How do semantic concepts specialize while preserving meaning?

**Findings:**

- Specialization is the mechanism for moving from universal to specific.
- Reuse, Specialization, Extension, and Composition are the four forms of semantic derivation.
- Specialization preserves parent meaning; extensions add semantics; compositions combine.
- Meaning preservation requires: identity inheritance, semantic preservation, constraint compatibility, conformance validation.

**Architectural Outcome:** Established the inheritance contract and conformance framework.

## Investigation 4 : WSF Semantic Assertion

**Question:** How are claims about the world represented in the semantic foundation?

**Findings:**

- An assertion has the pattern: Subject : Relationship → Object.
- An assertion is not a fact; truth is a property of the asserted proposition.
- Assertions require provenance: source, asserted-by, asserted-at, authority.
- Assertions may have evidence: observations, measurements, documents, records.
- Assertions have lifecycle states: Proposed → Active → Confirmed | Disputed | Rejected | Expired | Superseded | Withdrawn.

**Architectural Outcome:** Established the Semantic Assertion Model.

## Investigation 5 : WSF Semantic Mechanism Boundary

**Question:** What is the distinction between concepts and mechanisms?

**Findings:**

- Concepts describe what exists (Entity, Capability, Role).
- Mechanisms describe what happens (Commitment, Authorization, Decision, Action, Observation).
- Mechanisms are not concepts; they describe dynamic semantic structure.
- Time, Event, State, Validity are semantic dimensions, not concepts proper.

**Architectural Outcome:** Established the 4-dimensional semantic model (Things, Dynamics, Normativity, Measurement).

## Investigation 6 : WSF Semantic Ontology Boundary

**Question:** What is the boundary between WSF and formal ontology?

**Findings:**

- Semantic Meaning is the authoritative layer; Ontology is its formal representation.
- The architecture distinguishes: WSF (meaning authority) → Semantic Architecture (semantic organization) → Ontology Architecture (formal representation) → Ontology (machine-processable).
- An ontology artifact does not become authoritative merely by being represented.
- WSF, Semantic Architecture, and Ontology Architecture are three distinct foundations with separate concerns.

**Architectural Outcome:** Established the 3-foundation architecture (Ontological + Semantic Modeling + Semantic Governance).

## Investigation 7 : WSF Semantic Governance & Authority

**Question:** How does authority, inheritance, specialization, validation, and lifecycle operate across the foundation?

**Findings:**

- Authority is scoped : no single authority exists.
- The semantic dependency graph is distinct from organizational hierarchy.
- Lifecycle, versioning, deprecation, conformance, and cross-repository governance are required.
- The 10-layer semantic stack and 4 distinct graphs (Semantic, Specialization, Authority, Assertion) emerge from governance analysis.

**Architectural Outcome:** Established the comprehensive governance model.

## Investigation 8 : WSF Foundational Spine

**Question:** What is the core entity → capability → value chain?

**Findings:**

- Entity is a participant in semantic assertions (not "a thing").
- Role is relational, not a subtype of Entity.
- Capacity ≠ Ability ≠ Capability : the distinction is foundational.
- Capability is a middle-layer concept, not a primitive.
- The 9 ontological families (Participation, Potential, Purpose, Structure, Result, Representation, Intent, Commitment, Measurement) emerge from this analysis.

**Architectural Outcome:** Established the Entity → Role → Capacity → Ability → Capability → Function → Outcome → Value spine.

## Investigation 9 : WSF Structure-Means

**Question:** How do System, Resource, Service, Process, and Workflow relate semantically?

**Findings:**

- The 5 structure-means families are identified.
- Function ≠ Capability (Function is a subtype).
- Process ≠ Workflow (Workflow is a representation).
- System/Resource/Service may be relational, not "things".
- Workflow is not foundational : it belongs in Semantic Architecture.

**Architectural Outcome:** Established the structure-means semantic model.

## Investigation 10 : WSF Representation-Knowledge

**Question:** What is the distinction between Entity, Concept, Information, and Data?

**Findings:**

- Entity ≠ Concept : the distinction is foundational.
- Concept ≠ Information ≠ Data : three distinct levels.
- Assertion ≠ Truth : the distinction is preserved.
- The foundation requires 5 validation operations.

**Architectural Outcome:** Established the 7-distinction semantic model.

---

## Architectural Outcomes Summary

The 10 investigations collectively produced:

- The 14 (later refined to 13) foundational semantic domains
- The 12 Tier 1 foundational concepts
- The 9 supporting constructs
- The 6-stage semantic status model
- The 8-stage change control lifecycle
- The inheritance, assertion, evidence, and provenance models
- The 3-foundation architecture
- The graph-native representation model

These outcomes are formalized in the 22 ADRs in the [ADR/](../ADR/) directory.

---

## Related Documents

- [../ADR/](../ADR/) : Architectural Decision Records
- [../CR/](../CR/) : Change Requests
- [../GOVERNANCE/CHANGE-CONTROL-LIFECYCLE.md](../GOVERNANCE/CHANGE-CONTROL-LIFECYCLE.md) : Lifecycle model
- [../GOVERNANCE/SEMANTIC-STATUS-MODEL.md](../GOVERNANCE/SEMANTIC-STATUS-MODEL.md) : Status model

---

*The investigation record preserves the research lineage of the WSF architectural foundation.*
