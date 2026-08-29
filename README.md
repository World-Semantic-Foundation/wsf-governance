# World Semantic Foundation (WSF)

> **An authoritative, understandable, referenceable, machine-readable, executable, and integrable semantic foundation** — bridging meaning, representation, execution, and application.

[![Status: FROZEN](https://img.shields.io/badge/Status-FROZEN-blueviolet.svg)](./07_implementation/wsf-governance/GOVERNANCE/)
[![ADR-WSF-17 Accepted](https://img.shields.io/badge/ADR--WSF--17-Accepted-success.svg)](./07_implementation/wsf-governance/ADR/)
[![CR-WSF-17 Rev.1 Implementation](https://img.shields.io/badge/CR--WSF--17%20Rev.1-Implementation-orange.svg)](./07_implementation/wsf-governance/CR/)

---

## 1. WSF Purpose

The **World Semantic Foundation (WSF)** is the authoritative semantic foundation for universally reusable concepts and relationships. It exists because:

- Enterprise architectures and other specialized semantic systems require a foundation **broader than any individual domain**
- Without authoritative foundational semantics, downstream systems independently redefine the same concepts, creating **semantic divergence**
- A semantic foundation that exists only as documentation is difficult to operationalize
- A software platform without authoritative semantics risks encoding arbitrary or inconsistent meanings

WSF bridges four normally separated concerns:

```
Meaning → Representation → Execution → Application
```

## 2. WSF Mission

Establish WSF as a governed, versioned, authoritative, and usable semantic foundation from which downstream semantic systems (e.g., OpenDEA, Assessment-Models) may specialize and inherit foundational semantics.

## 3. WSF Scope

WSF provides **six mutually reinforcing capabilities** + Governance:

1. **Semantic Foundation** — authoritative foundational concepts, definitions, relationships, constraints
2. **Knowledge Assets** — human-readable documentation, ADRs, design rationale
3. **Semantic Engine** — deployable software implementation (Store + Services + API)
4. **Integration** — interfaces with OpenDEA, knowledge graphs, digital twins, AI platforms
5. **Visualization** — visual semantic assets for understanding and communication
6. **Realization** — reference applications including Entity modeling, Digital Twin, Simulation
7. **Governance** — ADR lifecycle, CR lifecycle, semantic status, versioning

## 4. WSF Non-Scope

WSF is **NOT**:

- An enterprise architecture model
- A business architecture model
- An assessment/maturity model
- A single-industry ontology
- A terminology catalogue
- A replacement for specialized domain semantic systems
- A complete universal ontology

WSF **provides the foundation** upon which these specialized systems can be built.

## 5. Foundational Semantic Architecture

WSF organizes semantics around **14 Foundational Domains**:

| Domain | Principal Concepts |
|---|---|
| **Existence** | Entity |
| **Occurrence** | Event |
| **Condition** | State |
| **Disposition** | Capacity, Ability, Capability |
| **Relation** | Relationship |
| **Identity** | Identity, Identifier, Name |
| **Semantics** | Concept, Term, Definition |
| **Proposition** | Proposition |
| **Assertion** | Assertion |
| **Qualification** | Context |
| **Temporality** | Time, Instant, Interval, Duration |
| **Spatiality** | Space, Location, Position |
| **Epistemics** | Evidence, Provenance, Authority, Trust |
| **Intentionality** | Goal, Purpose, Intention |

## 6. Design Principles

WSF is built on **12 Foundational Principles** (see [FOUNDATIONAL-PRINCIPLES.md](./07_implementation/wsf-docs/conceptual/FOUNDATIONAL-PRINCIPLES.md)):

1. Semantic Primacy
2. Minimal Foundation
3. Explicit Specialization
4. Identity Separation
5. Contextual Semantics
6. Assertion Separation
7. Provenance
8. Temporal Integrity
9. Relationship First-Classness
10. Lifecycle Independence
11. Evidence-Based Evolution
12. Open Specialization

## 7. Investigation History

WSF was established through **10 deep investigations** (see [INVESTIGATION-RECORD.md](./07_implementation/wsf-governance/RESEARCH/INVESTIGATION-RECORD.md)):

1. Capability–Ability–Capacity
2. Semantic Representation
3. Intent–Constraint–Commitment
4. Ontological Classification
5. Proposition–Assertion
6. Identity–Reference
7. Existence–Occurrence
8. Time–Space–Causality–Validity
9. Foundational Semantic Synthesis
10. WSF Product Architecture

The investigation lineage is preserved as a first-class program asset.

## 8. Architectural Decisions

WSF has **17 PROPOSED Architectural Decision Records (ADRs)** (see [ADR/](./07_implementation/wsf-governance/ADR/)):

| ADR | Decision |
|---|---|
| ADR-WSF-01 | WSF Foundational Position |
| ADR-WSF-02 | Semantic Layering |
| ADR-WSF-03 | Semantic Authority |
| ADR-WSF-04 | Semantic Inheritance |
| ADR-WSF-05 | Semantic Assertion |
| ADR-WSF-06 | Evidence & Provenance |
| ADR-WSF-07 | Capacity–Ability–Capability |
| ADR-WSF-08 | Foundational Concept Relationships |
| ADR-WSF-09 | Foundational Concept Taxonomy |
| ADR-WSF-10 | Semantic Identity & Naming |
| ADR-WSF-11 | Semantic Concept Specification |
| ADR-WSF-12 | Semantic Assertion Model |
| ADR-WSF-13 | Semantic Constraints & Validation |
| ADR-WSF-14 | Semantic Context & Boundary |
| ADR-WSF-15 | Semantic Authority & Governance |
| ADR-WSF-16 | Semantic Evolution & Versioning |
| ADR-WSF-17 | Foundational Semantic Architecture |

## 9. Repository Architecture

WSF is implemented across **8 repositories** under `World-Semantic-Foundation`:

```
World-Semantic-Foundation/
├── wsf             ← Canonical semantic assets
├── wsf-spec        ← Normative specifications
├── wsf-governance  ← ADRs, CRs, governance
├── wsf-examples    ← Reference applications
├── wsf-software    ← Deployable Semantic Engine
├── wsf-connectors  ← Integration adapters
├── wsf-visuals     ← Visual semantic assets
└── wsf-docs        ← Conceptual documentation
```

## 10. Semantic Assets

WSF provides foundational semantic assets for:

- **Concepts** — Entity, Concept, Relationship, Event, State, Disposition, Proposition, Assertion, Identity, Context, Time, Space
- **Supporting Constructs** — Identifier, Reference, Namespace, Term, Definition, Validity, Evidence, Provenance, Authority
- **Disposition Realization Chain** — `Disposition → Capacity/Ability/Capability → Activity → Event → Change → State`
- **4 Forms of Relation** — Structural / Temporal / Causal / Dispositional
- **Identity/Reference/Representation** distinctions
- **12 Epistemic Distinctions** — Term/Concept/Ontology/Assertion/Evidence/Provenance/Authority/Trust/Validation/Truth

## 11. Software Platform

The WSF Semantic Engine architecture:

```
WSF Semantic Engine
   ├── Semantic Store: Concepts/Entities/Relations/Assertions/Context/Provenance
   ├── Semantic Services: Validation/Resolution/Query/Reasoning/Mapping
   └── API Layer: REST/Graph/Events/SDK
```

**11 Engine Capabilities**: Create / Identify / Reference / Describe / Relate / Contextualize / Validate / Query / Reason / Transform / Import / Export / Observe

**Platform neutrality**: Technology choices (RDF/OWL/JSON-LD/Graph/Relational/REST/Events) implement the semantic architecture; they do NOT define it.

## 12. Integration

WSF integrates via governed semantic interfaces with:

- **OpenDEA** — Enterprise Architecture specialization
- **Assessment-Models** — Maturity model ecosystem (separate lifecycle)
- Enterprise Architecture Platforms
- Knowledge Graph Platforms
- Data Platforms
- Modeling Tools
- Digital Twin Platforms
- Simulation Systems
- AI/Agent Platforms
- Mainstream Enterprise Platforms

## 13. Visualization

WSF provides visual semantic assets in 7 categories:

- Conceptual Diagrams
- Semantic Maps
- Architecture Diagrams
- Lifecycle Diagrams
- Causal Diagrams
- Comparative Diagrams
- Application Diagrams

Diagrams should have **machine-readable or reproducible source representations** rather than only exported images.

## 14. Digital Twin Application

```
Entity Type (Data Center)
   ↓
Entity Instance (OTCHERE DC-01)
   ├── Identity
   ├── State
   ├── Events
   ├── Relationships
   ├── Capabilities
   ├── Context
   ├── Time
   └── Space
```

## 15. Simulation

```
Initial State
   ↓
Event / Action
   ↓
Transition
   ↓
Resulting State
   ↓
Next Event
```

**Capability vs Actual Event distinction is fundamental:**
- "What can this entity do?" (Capability)
- "What did this entity actually do?" (Event)

## 16. OpenDEA Relationship

```
WSF (foundational semantics)
   ↓
OpenDEA (enterprise architecture specialization)
   ↓
Architecture Models
```

OpenDEA inherits WSF Capability → specializes as Business Capability. **OpenDEA remains an independently governed Enterprise Architecture system. WSF does NOT absorb OpenDEA.**

## 17. Assessment-Models Boundary

```
Assessment-Models (maturity-model governance)
   ↓
Maturity Models
   ↓
OpenDEA Maturity Assessment (OpenDEA-specific instance)
```

**Assessment-Models remains independently governed. WSF does NOT become the assessment governance authority.**

## 18. Governance

The 8-stage change control lifecycle:

```
Investigation → Finding → Synthesis → ADR → CR → Implementation → Validation → Release
```

The 6-stage semantic status model:

```
Candidate → Investigating → Proposed → Normative → Deprecated → Retired
```

> **No implementation is interpreted as automatically creating a normative semantic decision.**

## 19. Contribution

WSF welcomes contribution through the ADR/CR framework. Each contribution must:

- Reference prior research (investigation record)
- Follow the 12 Foundational Principles
- Distinguish Finding / Decision / Implementation
- Use canonical OTCHERE Inc / Kwesi examples
- Avoid redefining WSF concepts downstream

## 20. Versioning

WSF distinguishes:

- **Semantic Identity** — stable identifier independent of name/location
- **Version** — state of a semantic definition
- **Validity** — temporal applicability
- **Lifecycle Status** — Candidate → Normative → Deprecated → Retired

A version change does NOT automatically imply a new semantic identity. A fundamental semantic change may require a new identity.

## 21. Conformance

A WSF implementation may be assessed against:

- Semantic Conformance
- Identity Conformance
- Reference Conformance
- Relationship Conformance
- Assertion Conformance
- Provenance Conformance
- Specialization Conformance
- API Conformance
- Serialization Conformance

Detailed conformance requirements are established through subsequent ADRs.

## 22. Roadmap

```
Phase 1 — WSF Inception           ← CR-WSF-17 Rev.1 implements this
Phase 2 — Foundational Model     (Tier 1: 12 primitives)
Phase 3 — Supporting Semantics   (Tier 2: 9 constructs)
Phase 4 — Semantic Specialization
Phase 5 — Reference Implementations
Phase 6 — Downstream Integration
```

**Next Implementation ADRs** (18-27):
- ADR-WSF-18: Concept Identity
- ADR-WSF-19: Semantic Relationship Model
- ADR-WSF-20: Concept Definition Model
- ADR-WSF-21: Namespace And Reference Model
- ADR-WSF-22: Assertion And Provenance Model
- ADR-WSF-23: Semantic Representation Architecture
- ADR-WSF-24: WSF Software Architecture
- ADR-WSF-25: WSF Integration Architecture
- ADR-WSF-26: WSF Visualization Architecture
- ADR-WSF-27: WSF Digital Twin and Simulation Architecture

---

## Quick Navigation

| Want to understand... | Read |
|---|---|
| **Why WSF exists** | [Investigation Record](./07_implementation/wsf-governance/RESEARCH/INVESTIGATION-RECORD.md) |
| **What WSF defines** | [12 Foundational Principles](./07_implementation/wsf-docs/conceptual/FOUNDATIONAL-PRINCIPLES.md) |
| **How decisions are made** | [ADRs](./07_implementation/wsf-governance/ADR/) + [Governance](./07_implementation/wsf-governance/GOVERNANCE/) |
| **What canonical examples exist** | [OTCHERE/Kwesi examples](./07_implementation/wsf-examples/) |
| **How to integrate** | [Integration Architecture](./07_implementation/wsf-connectors/) |
| **What visuals are available** | [Visual Assets](./07_implementation/wsf-visuals/) |

---

## Canonical Example Convention

All WSF examples use:

- **Enterprise**: OTCHERE Inc (or OTCHERE)
- **Individual**: Kwesi
- **ACME**: SHALL NOT BE USED

This applies to: documentation, specifications, diagrams, source code, test data, tutorials, simulations, digital twin examples, and all future WSF-derived work.

---

## Success Condition

> WSF exists as an authoritative, understandable, referenceable, machine-readable, executable, and integrable semantic foundation that can be applied to real-world modeling and demonstrated through practical applications.

**User Journey**: UNDERSTAND → REFERENCE → MODEL → VALIDATE → EXECUTE → INTEGRATE → VISUALIZE → SIMULATE → REALIZE

> **Without leaving the semantic foundation behind.**

---

## License

See [LICENSE](./LICENSE) (TBD — to be established by governance ADR)

## Contact

WSF Program — `World-Semantic-Foundation` GitHub Organization

---

*This README documents the WSF semantic foundation as established by CR-WSF-17 Rev.1 (per ADR-WSF-17) and 17 prior Architectural Decision Records. See `/07_implementation/wsf-governance/` for full governance documentation.*
