Yes. We should now move from synthesis into the formal WSF implementation decision layer.

The first ADR should establish the architecture itself—not individual concepts. Individual semantic decisions can then build underneath it.

ADR-WSF-17 — Foundational Semantic Architecture

Status: Proposed
Decision Type: Foundational Architecture
Scope: World Semantic Foundation (WSF)
Supersedes: None
Depends On: Completed WSF foundational investigations and synthesis

Context

The WSF program has investigated the semantic foundations required to support authoritative, reusable semantics across specialized semantic systems.

The investigation established that a world semantic foundation cannot adequately be represented as a flat vocabulary or an undifferentiated class hierarchy. It must distinguish several fundamentally different semantic concerns, including:

* what exists;
* what happens;
* what condition something is in;
* what things are related;
* what something is capable of doing;
* what is intended;
* what is asserted;
* how assertions are identified and referenced;
* under what context, time, and space an assertion applies;
* how provenance, evidence, authority, and validity are established.

The investigation also established that downstream systems require specialized semantic views of universal constructs.

For example:

WSF Capability
       │
       ▼
OpenDEA Business Capability

The downstream concept is therefore a specialization of foundational semantics rather than an independent redefinition.

This distinction is essential to the role of WSF.

Decision

WSF shall be established as a foundational semantic architecture consisting of a deliberately constrained set of semantic primitives, supporting constructs, and formally governed relationships.

WSF shall not attempt to represent the entire world through a single inheritance hierarchy.

Instead, WSF shall organize semantics through complementary dimensions:

Existence
Occurrence
Condition
Disposition
Relation
Identity
Semantics
Proposition
Assertion
Qualification
Temporality
Spatiality
Epistemics

The initial foundational semantic candidates are:

Entity
Concept
Relationship
Event
State
Disposition
Proposition
Assertion
Identity
Context
Time
Space

Supporting semantic constructs include:

Identifier
Reference
Namespace
Term
Definition
Validity
Evidence
Provenance
Authority

Derived and specialized concepts shall be introduced through explicit semantic specialization rather than promoted to foundational status merely because they are important in a particular domain.

Foundational Relationship Model

WSF shall support first-class relationships:

Subject
   │
   └── Relationship ──► Object

Relationships may subsequently be specialized into semantic relationship types, including:

classifies
specializes
enables
depends-on
located-in
precedes
causes

The existence of a relationship shall remain distinct from an assertion that such a relationship exists.

Disposition Model

The Capability investigation is incorporated into the foundational architecture through Disposition.

The semantic pattern is:

Disposition
    ├── Capacity
    ├── Ability
    └── Capability

Capability may subsequently be specialized according to domain purpose:

Capability
    ├── Business Capability
    ├── Operational Capability
    └── Technical Capability

This does not establish these as universal WSF classes automatically; their formal status is subject to subsequent ADRs.

Occurrence Model

WSF shall distinguish potential activity from actual occurrence:

Activity
    │
    └── realized as → Event

Likewise:

Event
   └── may produce/constitute → Change
                                │
                                ▼
                              State

Process and Workflow are therefore treated as higher-level structural constructs rather than automatically foundational primitives.

Proposition And Assertion

WSF shall distinguish:

Proposition
    │
    └── expressed through → Assertion

An Assertion may carry:

Provenance
Evidence
Authority
Validity
Context
Time
Space

This allows WSF to distinguish semantic content from claims about that content.

Identity And Reference

WSF shall preserve the distinction:

Identity
Identifier
Name
Reference
Representation

A Reference shall not automatically be treated as the identity of its referent.

Reference resolution may depend upon:

Namespace
Context
Identity

Temporal And Spatial Semantics

Time and Space shall be first-class semantic dimensions.

The foundation shall accommodate concepts such as:

Instant
Interval
Duration
Location
Position
Spatial Region

without requiring every downstream model to use every construct.

Temporal precedence shall remain distinct from causality:

A precedes B

does not imply:

A causes B

Context

Context shall be treated as a semantic qualification mechanism.

It may qualify:

Meaning
Interpretation
Assertion
Validity
Relationship
Evaluation

Context shall not simply be treated as a generic container for arbitrary metadata.

⸻

Architectural Boundary

The decision establishes the following direction:

                         WSF
                          │
                Foundational Semantics
                          │
              ┌───────────┴───────────┐
              ▼                       ▼
             ESS                      EO
              │                       │
              └───────────┬───────────┘
                          ▼
                       OpenDEA

The downstream systems may specialize, constrain, compose, and reuse WSF semantics.

They shall not redefine WSF foundational concepts within their own semantic namespace without an explicit governance decision.

⸻

OpenDEA Boundary

This ADR explicitly preserves the previously established organizational boundary.

OpenDEA remains:

an Enterprise Architecture system serving the enterprise.

Its concepts are therefore enterprise-architecture specializations of broader semantics where appropriate.

For example:

WSF
 └── Capability
      └── OpenDEA Business Capability

OpenDEA does not become the authoritative home of the universal concept Capability.

⸻

Assessment Boundary

The Assessment-Models organization remains independently governed.

Its relationship to OpenDEA is:

Assessment-Models
       │
       │ governs maturity-model ecosystem
       ▼
Maturity Model
       │
       │ instantiated/specialized by
       ▼
OpenDEA
       │
       ▼
OpenDEA Maturity Assessment

The OpenDEA maturity assessment therefore remains an OpenDEA-managed architecture adoption/usage assessment instance, while its foundational maturity-model constructs and inter-model relationships remain governed by Assessment-Models.

WSF does not collapse these organizational lifecycles.

⸻

Consequences

Positive

This decision gives WSF:

* a small semantic foundation rather than an uncontrolled ontology;
* explicit separation of universal and domain-specific semantics;
* reusable identity and reference semantics;
* first-class relationship semantics;
* explicit epistemic semantics;
* temporal and spatial qualification;
* a principled basis for specialization;
* a clear semantic inheritance path into ESS, EO, and OpenDEA;
* room for future domain ontologies without destabilizing the foundation.

Cost

The approach requires:

* stronger semantic governance;
* explicit distinction between foundational and derived concepts;
* versioned definitions;
* formal change control;
* provenance;
* conformance mechanisms;
* greater discipline when introducing new concepts.

That complexity is intentional. WSF is being established as authoritative infrastructure, not merely as documentation.

⸻

Alternatives Rejected

A. Flat Vocabulary

Rejected because terminology without formal semantic relationships cannot reliably support semantic interoperability.

B. Universal Class Hierarchy

Rejected because it forces fundamentally different semantic categories—entities, events, states, relationships, propositions, and dispositions—into an inappropriate single taxonomy.

C. Domain-First Ontology

Rejected because it would make WSF dependent upon a particular domain such as enterprise architecture.

D. OpenDEA-As-Foundation

Rejected because OpenDEA is explicitly an Enterprise Architecture system and therefore represents a specialization of the world rather than the semantic foundation of the world.

E. Assessment-As-Foundation

Rejected because Assessment-Models represents a separate semantic and governance concern with its own lifecycle.

⸻

Implementation Implications

This ADR authorizes the implementation program to establish the WSF foundational semantic architecture, but it does not yet authorize arbitrary implementation choices.

The next implementation decisions should address:

ADR-WSF-18
WSF Concept Identity
ADR-WSF-19
WSF Semantic Relationship Model
ADR-WSF-20
WSF Concept Definition Model
ADR-WSF-21
WSF Namespace And Reference Model
ADR-WSF-22
WSF Assertion And Provenance Model

The precise numbering can be reconciled against the existing ADR sequence before committing the files, so that we do not accidentally create a numbering collision.

⸻

Implementation Gate

With this ADR, the program moves from:

INVESTIGATE
     ↓
SYNTHESIZE
     ↓
DECIDE

and is ready for:

IMPLEMENT
     ↓
VALIDATE
     ↓
GOVERN
     ↓
EVOLVE

The next practical artifact should therefore be the CR implementing ADR-WSF-17, including creation of the initial WSF repository structure under the existing World-Semantic-Foundation GitHub organization, the authoritative README, governance scaffolding, investigation record, and initial semantic architecture specification.
