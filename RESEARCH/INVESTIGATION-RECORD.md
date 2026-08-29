# WSF Investigation Record

> **The research lineage leading to WSF's architectural foundation.**

This document preserves the 10 investigations that produced WSF. Per CR-WSF-17 Rev.1 §6, the investigation record is a **first-class program asset** — it is preserved distinctly from normative decisions.

---

## Why This Record Exists

WSF's architectural decisions are not arbitrary. They are grounded in 10 specific investigations that progressively explored:

- What kinds of things exist, occur, persist, change, relate
- How meaning is represented, asserted, validated
- How semantic systems integrate without absorbing each other

> **The record explains not just WHAT WSF defines but WHY it defines it this way.**

---

## The 10 Investigations

### Investigation 1 — Capability–Ability–Capacity

**Question**: Is Capability a foundational concept, or derived?

**Key findings**:
- Capability = attributable, contextualized potential of an Entity, grounded in Capacity + Ability
- Capacity ≠ Ability: Capacity = potential/extent, Ability = competence to perform
- Capability is a **middle-layer concept** in the semantic spine, not a primitive

**Consequence**: WSF Capability = grounded via `Disposition → Capacity/Ability/Capability`, with semantic home in Disposition category.

---

### Investigation 2 — Semantic Representation

**Question**: How does WSF distinguish reality, meaning, representation, encoding, and claim?

**Key findings**:
- 5 critical distinctions: Entity ≠ Concept, Concept ≠ Information ≠ Data, Assertion ≠ Truth
- WSF = 3 foundations (Ontological + Semantic Modeling + Governance), NOT one ontology
- Reality → Meaning → Representation → Encoding is a layered chain

**Consequence**: WSF kernel is 8 primitives (Entity/Identity/Type/Relationship/Context/Assertion/Provenance/Evidence) — not just concepts.

---

### Investigation 3 — Intent–Constraint–Commitment

**Question**: How do Goal/Requirement/Rule/Policy/Agreement/Contract relate to the WSF foundation?

**Key findings**:
- Goal ≠ Outcome (Goal = desired, Outcome = achieved)
- Rule ≠ Policy (Rule = constraint, Policy = governance intent)
- Agreement ≠ Contract (Contract = formalized Agreement)
- **Obligation** and **Right** are NEW concepts not in original list
- Relationship is foundational (not just an implementation detail)

**Consequence**: WSF should be relationship-centric, not inheritance-centric.

---

### Investigation 4 — Ontological Classification

**Question**: Which candidates are foundational, derived, relational, contextual?

**Key findings**:
- 7-question classification test (Existence/Independence/Identity/Relationality/Contextuality/Representation/Derivability)
- 8 ontological categories (Foundational/Derived/Relational/Dispositional/Activity/Contextual/Representational/Qualifying)
- Resource = Role pattern (not Entity subtype)
- Service = Relational construct (not Thing)
- Value = Contextual evaluation (not Primitive)

**Consequence**: WSF should define **semantic patterns, not just classes**.

---

### Investigation 5 — Proposition–Assertion

**Question**: What does it mean to make a semantically valid assertion about something?

**Key findings**:
- 12 epistemic distinctions (Term ≠ Concept, Concept ≠ Ontology, Ontology ≠ Assertion, Assertion ≠ Evidence, Evidence ≠ Provenance, Provenance ≠ Authority, Authority ≠ Trust, Validation ≠ Truth)
- Assertion is more than Subject-Predicate-Object triple (needs Context, Time, Source, Provenance, Evidence, Authority, Confidence/Trust)
- 7 validation types (Syntactic/Semantic/Ontological/Constraint/Evidence/Provenance/Conformance)
- **Semantic Contract** — new concept for governing specialization preservation

**Consequence**: WSF Semantic Assertion Model includes 10+ qualifiers, not just triple structure.

---

### Investigation 6 — Identity–Reference

**Question**: What is Identity, and how does it differ from Identifier/Name/Reference/Representation?

**Key findings**:
- Identity ≠ Identifier ≠ Name ≠ Reference ≠ Representation
- URI = ONE type of Identifier, not Identity itself
- A Reference shall NOT automatically be treated as the identity of its referent
- Reference resolution may depend on Namespace + Context + Identity

**Consequence**: WSF preserves 5 distinct identity-related constructs.

---

### Investigation 7 — Existence–Occurrence

**Question**: What kinds of things can WSF say exist, occur, persist, change?

**Key findings**:
- 3 modes of existence: Entity (what exists), Event (what happens), State (what condition)
- Activity ≠ Event (Activity = type/pattern, Event = occurrence)
- State ≠ State Machine (model vs thing modeled)
- **Disposition** is a NEW foundational category
- Process is LIKELY DERIVED (not primitive)
- Workflow likely NOT foundational

**Consequence**: Capability is grounded in Disposition, not a standalone primitive. 9 ontological families emerge.

---

### Investigation 8 — Time–Space–Causality–Validity

**Question**: What dimensions are required for an assertion to be sufficiently qualified?

**Key findings**:
- Time is a semantic dimension, not merely an attribute
- Instant ≠ Interval
- Duration ≠ Interval
- Precedence ≠ Causality (CRITICAL distinction)
- Validity ≠ Truth
- Position ≠ Location
- 4 Forms of Relation: Structural / Temporal / Causal / Dispositional
- Potentiality → Actuality axis: Disposition → Activity → Event → Change → State

**Consequence**: WSF preserves all 4 relation forms as specializations of foundational Relationship.

---

### Investigation 9 — Foundational Semantic Synthesis

**Question**: After 8 deep investigations, what is the consolidated WSF foundation?

**Key findings**:
- 3-Tier Implementation Plan:
  - Tier 1: 12 foundational (Entity, Concept, Relationship, Event, State, Disposition, Proposition, Assertion, Identity, Context, Time, Space)
  - Tier 2: 9 supporting (Identifier, Reference, Namespace, Term, Definition, Validity, Evidence, Provenance, Authority)
  - Tier 3: 16+ derived (Capacity, Ability, Capability, Activity, Process, Workflow, etc.)
- 14 Foundational Semantic Domains (Existence / Occurrence / Condition / Disposition / Relation / Identity / Semantics / Proposition / Assertion / Qualification / Temporality / Spatiality / Epistemics / Intentionality)
- **WSF is broader than an ontology** — 3 foundations + 14 domains + semantic patterns

**Consequence**: ADR-WSF-17 (Foundational Semantic Architecture) was created to formally adopt this synthesis.

---

### Investigation 10 — WSF Product Architecture

**Question**: How should WSF be implemented as a usable product?

**Key findings**:
- WSF = 7 capabilities: Semantic Foundation / Knowledge Assets / Semantic Engine / Integration / Visualization / Realization / Governance
- 8-repository structure (wsf / wsf-spec / wsf-governance / wsf-examples / wsf-software / wsf-connectors / wsf-visuals / wsf-docs)
- Semantic Engine architecture: Store + Services + API
- 11 engine capabilities (Create/Identify/Reference/Describe/Relate/Contextualize/Validate/Query/Reason/Transform/Import/Export/Observe)
- Digital Twin pattern + Simulation pattern are foundational applications
- Platform neutrality: technology implements architecture, not defines it

**Consequence**: CR-WSF-17 Rev.1 (Establish WSF Product Foundation) was created to anchor implementation.

---

## The Synthesis Chain

```
Investigation 1 (Capability–Ability–Capacity)
   ↓ grounded Capability in Disposition
Investigation 7 (Existence–Occurrence)
   ↓ introduced Disposition as foundational category
Investigation 4 (Ontological Classification)
   ↓ classified 25 candidates across 8 categories
Investigation 2 (Semantic Representation)
   ↓ established 5 distinctions + 3 foundations
Investigation 3 (Intent–Constraint–Commitment)
   ↓ surfaced new concepts (Obligation, Right)
Investigation 5 (Proposition–Assertion)
   ↓ formalized 12 epistemic distinctions
Investigation 6 (Identity–Reference)
   ↓ preserved identity vs reference distinction
Investigation 8 (Time–Space–Causality–Validity)
   ↓ established 4 relation forms + temporal validity
Investigation 9 (Synthesis)
   ↓ consolidated to 3-tier foundation + 14 domains
Investigation 10 (Product Architecture)
   ↓ anchored implementation with 7 capabilities + 8 repos
```

---

## Architectural Decisions That Emerged

Each investigation led to specific ADRs:

| Investigation | ADRs |
|---|---|
| 1 | ADR-WSF-07 Capacity–Ability–Capability |
| 2 | ADR-WSF-02 Semantic Layering, ADR-WSF-12 Semantic Assertion Model |
| 3 | ADR-WSF-08 Foundational Concept Relationships, ADR-WSF-09 Foundational Concept Taxonomy |
| 4 | ADR-WSF-09 (refined) |
| 5 | ADR-WSF-12 (refined) |
| 6 | ADR-WSF-10 Semantic Identity & Naming, ADR-WSF-11 Semantic Concept Specification |
| 7 | ADR-WSF-17 (Disposition grounding) |
| 8 | ADR-WSF-13 Semantic Constraints & Validation, ADR-WSF-16 Semantic Evolution & Versioning |
| 9 | ADR-WSF-17 Foundational Semantic Architecture |
| 10 | CR-WSF-17 Rev.1 |

---

## Distinction: Finding vs Decision vs Implementation

Per CR-WSF-17 Rev.1 §13 and §26, this investigation record explicitly distinguishes:

- **Investigation Finding** — A research observation, not yet architectural
- **Architectural Decision** — A formal ADR establishing a position
- **Implementation** — The execution of a CR based on an ADR

**These shall NOT be conflated.** The investigation record preserves Findings, even when they are superseded by Decisions or replaced by Implementation.

---

## How to Use This Record

If you want to understand:
- **WHY** WSF is structured this way → read the Investigation Findings
- **WHAT** WSF decides → read the ADRs
- **HOW** WSF is implemented → read the CRs and the 8 repositories

---

*This investigation record is preserved per CR-WSF-17 Rev.1 §6 as a first-class program asset. It shall remain distinguishable from normative decisions.*
